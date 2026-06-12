---
title: "Ubuntu 20 on old Dell Desktop not booting without manual intervention"
date: 2024-01-26
forum: Ubuntu, Linux and OS Chat
---

### Post by gutter007 on 2024-01-26
I'm trying to repurpose on old Desktop and install ubuntu server on it.

Dell Optiplex 755
BIOS Rev A22 (latest)
BIOS non UEFI
ubuntu 20.04 - legacy server

I have looked into the BIOS and there are no UEFI/Legacy Mode options available.  From the research I have done it is not UEFI.

I can boot into the live USB of ubuntu 20 legacy server, and it installs ubunbtu 20.04 on it.

However,  when it boots back up, it beeps twice then "No boot device available"

I checked the bios, and the boot order is set correctly.  The first option is the SATA HD.

However, if I boot and choose "Boot Menu", and then select the SATA HD, it will show grub, then boot into ubuntu.

Although it is functioning, I'd like it to be able to reboot without having to step in with manual intervention.

I feel like it's a combination of partitioning, grub, and MBR configuration, but I could be way off.

Please let me know if there are any questions, or if I can try anything else to get this working.

thanks!

---

### Post by gutter007 on 2024-01-27
OK ... it turns out it has nothing to do with Ubuntu.  I tried installing debian (similar) and Fedora (less so).  Both installed, but couldn't boot, so the same problem as Ubuntu.

I did a factory reset of my BIOS (Basically set all configuration back to factory setting)  I then had to disable the hardware I did not have, diskette drive, second HD.  Then it worked!

So again, stupid BIOS.

---

