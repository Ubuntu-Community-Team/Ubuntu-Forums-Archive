---
title: "USB install fails...need help"
date: 2010-11-06
forum: Server Platforms
---

### Post by test006 on 2010-11-06
Hi,
I am trying to install ubuntu server 10.10 using a USB flash disk. My server is a supermicro server which does not have a cdrom drive. It supports booting off a USB drive.
I have tried two options for creating bootable USB disk drive:
1. using universal USB installer from pendrivelinux.com
2. using unetbootin-windows 
In both cases when i try in install the ubuntu server 10.10 i get message saying cannot mount cd-rom drive. Also tells me cannot load pre-configuration file.
Can someone please help me overcome this issue and proceed with installing ubuntu server using a usb flash disk...
Please help...Please note i am trying to install Ubuntu server and not desktop version.

Thanks

---

### Post by Fafler on 2010-11-06
Server vs. desktop shouldn't make much difference here. Have you tried using another flash drive?

---

### Post by dtfinch on 2010-11-06
For me, unetbootin (on Windows) has worked for the livecd, but never for the server or alternative cds due to long filename and symlink issues.

[https://bugs.launchpad.net/unetbootin/+bug/373089](https://bugs.launchpad.net/unetbootin/+bug/373089)

Linux-based usb installer creators don't seem to have the same problem, but I haven't used any myself.

---

### Post by dbo117 on 2010-11-06
I just had the same problem. I too tried Unetbootin (which I have had successfully install Desktop 10.04) as well as Universal. Right now I am going to just try installing Server 10.04. I'll keep ya posted.

---

### Post by dbo117 on 2010-11-07
Stepping back to 10.04 fixed that error. If the computer is older (single-core and under 2ghz) you may want to format it as FAT not FAT32 to avoid errors. Also you may need to modify the naming of your isolinux file, see: [http://ubuntuforums.org/showthread.php?t=1583344](http://ubuntuforums.org/showthread.php?t=1583344)

---

### Post by littlegreiger on 2010-11-07
I just ran into this same problem this week. I solved it by following a post I found on another forum: [http://www.revouser.com/forum/viewtopic.php?f=7&t=794](http://www.revouser.com/forum/viewtopic.php?f=7&t=794)

---

### Post by adrianecole on 2010-11-07
I could also not get 10.10 server to install on a machine from USB with no cd drive present. Adding the boot flag try-USB didn't work either. Will goto 10.04 then I guess.

---

### Post by adrianecole on 2010-11-07
My post crossed with the one above, that trick with re-mounting the ISO  as a CD image works great.

thanks for the link.

---

