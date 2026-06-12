---
title: "Does *buntu support the LSI 1068E SAS RAID controller?"
date: 2009-07-12
forum: Server Platforms
---

### Post by jazzop on 2009-07-12
I have the following hardware, and it has been impossible to get a working install of Ubuntu 9.04 with SAS RAID set up in the BIOS.

ASUS Z8PE-D12X motherboard
ASUS PIKE 1068E SAS Adapter (LSI 1868E chipset/firmware)
2x Fujitsu MBA3147RC hard drives in RAID 1

There are several other threads suggesting that this SAS adapter is not supported under *buntu, but I wish I could get a definitive answer.  ASUS only provides RHEL and SuSE drivers.  I tried OpenSuSE 11.1, but it also fails at partition time.

Can someone PLEASE let me know if I need to stop messing with this and go to a different OS?

---

### Post by rdave on 2009-11-12
Hi,

"LSI does not release any Ubuntu Linux drivers
  This means Ubuntu OS is not supported at all for onboard SAS (LSI 2008)
   
  You can check with the Ubuntu OS community if any users managed to get it working 
  But according to our data this is not available
   
  Only onboard SATA is compatible in AHCI mode"


I have a SAS2 (LSI 2008) adapter, can you please someone help me to find a way to use it with ubuntu 9.10 Server? It's really strange beacuse it's works perfectly with the Ubuntu 9.10 Desktop.


Thanks in advance

---

