---
title: "Why can't I lvextend my logical volume - 12.04 LTS server"
date: 2016-10-10
forum: Ubuntu Cloud and Juju
---

### Post by curmudge1 on 2016-10-10
I get this error when I try to lvextend:  Insufficient suitable allocatable extents for logical volume

I have this configuration:

vgdisplay -v
    Finding all volume groups
    Finding volume group "FTPdata1VG"
  --- Volume group ---
  VG Name               FTPdata1VG
  System ID
  Format                lvm2
  Metadata Areas        4
  Metadata Sequence No  3
  VG Access             read/write
  VG Status             resizable
  MAX LV                0
  Cur LV                1
  Open LV               1
  Max PV                0
  Cur PV                4
  Act PV                4
  VG Size               1023.98 GiB
  PE Size               4.00 MiB
  Total PE              262140
  Alloc PE / Size       196584 / 767.91 GiB
  Free  PE / Size       65556 / 256.08 GiB
  VG UUID               HUmA9A-uezF-vUdZ-ZaOS-9lT4-La45-PHbdNi


  --- Logical volume ---
  LV Name                /dev/FTPdata1VG/lvol0
  VG Name                FTPdata1VG
  LV UUID                ezTdE9-JB4F-N890-Fzl4-Vf3l-8VFm-FBefnV
  LV Write Access        read/write
  LV Status              available
  # open                 1
  LV Size                767.91 GiB
  Current LE             196584
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     768
  Block device           252:0


  --- Physical volumes ---
  PV Name               /dev/sdb1
  PV UUID               eAwZs9-BIUS-BFWs-s444-O2YT-LtWC-PR8Qjt
  PV Status             allocatable
  Total PE / Free PE    65535 / 7


  PV Name               /dev/sdc1
  PV UUID               qZOmsk-WoDU-g3Rt-sYcZ-2S5X-BuqA-aEuZD2
  PV Status             allocatable
  Total PE / Free PE    65535 / 7


  PV Name               /dev/sdd1
  PV UUID               jgnypu-Myz7-e0vx-tauj-kS1d-bZqW-4iX8bo
  PV Status             allocatable
  Total PE / Free PE    65535 / 7


  PV Name               /dev/sde1
  PV UUID               sK725R-B3Eu-Mo7r-fyA4-U3wt-cKiw-A7GS7n
  PV Status             allocatable
  Total PE / Free PE    65535 / 65535

... so I had 3 disk created the Logical volume (this is a VM in vmware, if it matters) ... this is NOT lvm mirror, most of the google search results were dealing with mirrors. I need more space so I added another 256GB (virtual) disk.
Added to the volume group OK, but cannot extend the logical volume, any idea why?  

lvextend /dev/FTPdata1VG/lvol0 /dev/sde1
  Using stripesize of last segment 64.00 KiB
  Extending logical volume lvol0 to 1023.90 GiB
  Not enough PVs with free space available for parallel allocation.
  Consider --alloc anywhere if desperate.

Also, this:

 lvextend -L+100G /dev/FTPdata1VG/lvol0
  Using stripesize of last segment 64.00 KiB
  Rounding size (222184 extents) down to stripe boundary size for segment (222183 extents)
  Extending logical volume lvol0 to 867.90 GiB
  Insufficient suitable allocatable extents for logical volume lvol0: 25578 more required

Any help is appreciated.

---

### Post by curmudge1 on 2016-10-12
Ok found the answer on a Centos forum.

My original LV is striped, so I can't add just one disk, because the LV can't restripe 3 disks to 4. 

I can ignore the striping to add space, so I did:

lvextend -i 1 -L+256G /dev/FTPdata1VG/lvol0
  Extending logical volume lvol0 to 1023.91 GiB
  Logical volume lvol0 successfully resized

then resize2fs & it works.

---

