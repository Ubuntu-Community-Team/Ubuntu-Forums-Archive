---
title: "Encrypting My Server"
date: 2010-10-29
forum: Security
---

### Post by thegodfaza on 2010-10-29
I have an Ubuntu 10.04.1 LTS server that I set up a while back and I am considering encrypting the whole box. I store everything on the server and if it were stolen from a home robbery it could be quite devastating. The server is using two 750 GB SATA hard drives formatted with LVM. Inside the LVM I have a small partition on the first drive for the OS, SWAP, and everything else on the first and second drive is /var/media which is where I store all the data. I have set up an encrypted LVM on my laptop but that was during the install using the automatic method.

I read through [this]("https://help.ubuntu.com/community/EncryptedFilesystemHowto") but I can't figure out how to do what I want to do and I don't want to risk destroying the data on the server. What I would like is to non-destructively encrypt the server (System, SWAP, and DATA partitions) similar to how TrueCrypt works on Windows and I'd like the encryption key to be stored on a USB thumb drive so when the server boots it requires a hardware key. (And have the encryption key backed up online in case the flash drive dies.) And I'd like to use AES 256.

```

justin@singularity:~$ sudo vgdisplay
  --- Volume group ---
  VG Name               Primary
  System ID
  Format                lvm2
  Metadata Areas        2
  Metadata Sequence No  22
  VG Access             read/write
  VG Status             resizable
  MAX LV                0
  Cur LV                3
  Open LV               3
  Max PV                0
  Cur PV                2
  Act PV                2
  VG Size               1.36 TiB
  PE Size               4.00 MiB
  Total PE              357700
  Alloc PE / Size       357700 / 1.36 TiB
  Free  PE / Size       0 / 0
  VG UUID               WCuXZo-3Rvz-wj3I-Pe8k-y2p1-1Hu0-mry5cf
justin@singularity:~$ sudo pvs
  PV         VG      Fmt  Attr PSize   PFree
  /dev/sda1  Primary lvm2 a-   698.63g    0
  /dev/sdb1  Primary lvm2 a-   698.63g    0
justin@singularity:~$ sudo lvdisplay /dev/Primary
  --- Logical volume ---
  LV Name                /dev/Primary/System
  VG Name                Primary
  LV UUID                cF7HQx-MYb3-xRtO-xsJC-UHIc-QBCr-y36MZd
  LV Write Access        read/write
  LV Status              available
  # open                 1
  LV Size                92.13 GiB
  Current LE             23586
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:0

  --- Logical volume ---
  LV Name                /dev/Primary/SWAP
  VG Name                Primary
  LV UUID                DXqhTo-hCEz-OArf-UsEz-FnNy-KsyL-IN1IQ3
  LV Write Access        read/write
  LV Status              available
  # open                 1
  LV Size                4.66 GiB
  Current LE             1192
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:1

  --- Logical volume ---
  LV Name                /dev/Primary/Data
  VG Name                Primary
  LV UUID                u0DDpn-Z5bD-0UC0-RKYn-Je0p-iOUh-IcuyNO
  LV Write Access        read/write
  LV Status              available
  # open                 1
  LV Size                1.27 TiB
  Current LE             332922
  Segments               3
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:2

```

---

### Post by HermanAB on 2010-10-30
Howdy,

I prefer LUKS:
[http://www.aeronetworks.ca/howtos/luks-usb-howto.html](http://www.aeronetworks.ca/howtos/luks-usb-howto.html)

but encfs is secure too.

---

