# All-in-One Server
Recourses and notes of building All-in-One Server

## Hardwares
- CPU & Motherboard: [CWWK N100/I3-N305 SIX-BAY NAS MONSTER BOARD/4X 2.5G/6X SATA3.0/2X M.2 NVME/115X RADIATOR ITX BOARD TYPE MOTHERBOARD
](https://cwwk.net/products/cwwk-n100-i3-n305-six-bay-nas-monster-board-4x-2-5g-6x-sata3-0-2x-m-2-nvme-115x-radiator-itx-board-type-motherboard?variant=45197980238056)
- Memory: [TEAMGROUP Elite SODIMM DDR5 32GB 5600Mhz (PC5-44800) CL46 Non-ECC Unbuffered 1.1V 262 Pin Laptop Memory Module Ram - TED532G5600C46A-S01](https://www.amazon.com/dp/B0CRB5MPL4?ref=ppx_yo2ov_dt_b_product_details&th=1)


## TrueNAS Core
### Installation
### Fresh Setup
#### Test Disk Speed
- Create a dataset in the pool with SMB and no compression
- `cd` into the dataset and use the following command to do speed tests:
```
# Sequential write
fio --direct=1 --iodepth=16 --thread --rw=write --ioengine=psync --bs=128k --size=2G --numjobs=30 --group_reporting --name=seqwrite

# Sequential read
fio --direct=1 --iodepth=16 --thread --rw=read --ioengine=psync --bs=128k --size=2G --numjobs=30 --group_reporting --name=seqread

# Random write
fio --direct=1 --iodepth=16 --thread --rw=randwrite --ioengine=psync --bs=128k --size=2G --numjobs=30 --group_reporting --name=randwrite

# Random read
fio --direct=1 --iodepth=16 --thread --rw=randread --ioengine=psync --bs=128k --size=2G --numjobs=30 --group_reporting --name=randread
```

#### Test Tasks
- **Scrub:** Every 1st and 15th of the month at 4 am. The threshold on 10 days.
- **Short S.M.A.R.T:** Every 5th, 12th, 19th and 26th of the month at 3 am.
- **Long S.M.A.R.T:** Every 8th and 22nd at 4 am.


## OpenVPN Client


## References
- https://vicfree.com/2023/01/truenas-setup-guide/
- https://www.reddit.com/r/openwrt/comments/199b2qh/openwrt_over_proxmox_in_a_mini_pc_ryzen_5/
- https://theramblingtech.com/setup-proxmox8/
- https://foxi.buduanwang.vip/virtualization/1754.html/
- https://halysl.github.io/2020/05/12/fio%E6%B5%8B%E8%AF%95%E7%A3%81%E7%9B%98%E6%80%A7%E8%83%BD/
- https://blog.konpat.me/dev/2019/03/11/setting-up-lxc-for-intel-gpu-proxmox.html
- https://pve.proxmox.com/wiki/OpenVPN_in_LXC
