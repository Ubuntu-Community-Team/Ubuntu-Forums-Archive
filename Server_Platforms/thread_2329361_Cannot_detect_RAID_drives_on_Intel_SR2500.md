---
title: "Cannot detect RAID drives on Intel SR2500"
date: 2016-06-30
forum: Server Platforms
---

### Post by homemadejam-1 on 2016-06-30
First time ever attepting to install Ubuntu on an actual server.

I'm using Ubuntu Server 16.04 LTS, and attepting to install on Intel Server Chassis SR2500.

I boot up from the CD, enter username and password on the installation, and then whilst detecting drives, it fails, and comes up with a list of drivers to chose from.

We have a 80Gb, and a 500Gb harddrive inserted into the front hot swap bays.

Any help would be greatly appreciated.

---

### Post by nerdtron on 2016-06-30
Have you configured the RAID controller to your desired RAID setup? On server scenarios with hardware RAID setups, the OS will not detect the hard drives directly. You'll need to configure the RAID on your BIOS or RAID setup menu during boot-up. In there, you'll define your storage drives and initialize them. After that, try to boot Ubuntu again and see if your drives are detected.

---

### Post by homemadejam-1 on 2016-07-01
> **nerdtron said:**
> Have you configured the RAID controller to your desired RAID setup? On server scenarios with hardware RAID setups, the OS will not detect the hard drives directly. You'll need to configure the RAID on your BIOS or RAID setup menu during boot-up. In there, you'll define your storage drives and initialize them. After that, try to boot Ubuntu again and see if your drives are detected.

Brilliant, thanks a lot!
I did just that, and worked perfectly. First time using hardware RAID things.

---

