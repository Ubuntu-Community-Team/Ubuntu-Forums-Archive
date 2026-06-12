---
title: "UBUNTU server still NO BOOT after using recommended option of BOOT REPAIR DISK"
date: 2017-05-25
forum: Server Platforms
---

### Post by felicianodark on 2017-05-25
Hi,

I´ve tried to repair my Ubuntu Server 14.04 installation on a DELL Poweredge T110 II server with Boot Repair bootable disk using recommended action but still doesn't boot. Can you please help me?

This is the boot info [http://paste.ubuntu.com/24655708](http://paste.ubuntu.com/24655708)

Thanks!

---

### Post by slickymaster on 2017-05-25
*Thread moved to **Server Platforms**.*

---

### Post by Michael_McKenney on 2017-05-25
Did it ever work?   Do you have a backup?   Most Dell servers don't fully support Ubuntu.   Even my HP DL380 Gen8 only supported Ubuntu on the old SATA controller not the SAS controller.

---

### Post by TheFu on 2017-05-27
Welcome to the forums.

Looked at the output. Thanks. It isn't saying much that is obviously wrong.

Is the server UEFI?  The install didn't get that, if so.  Is secureboot enabled in the BIOS?  If you are trying to use non-UEFI (legacy boot), I don't see anything clearly wrong.  Just check that the BIOS is set to boot off sda.

[https://certification.ubuntu.com/hardware/201105-8031/](https://certification.ubuntu.com/hardware/201105-8031/) says there aren't any special notes for this server running the 3.13 kernel.

I'd unplug sdb , sdc, sdd, sde and all other disks except sda. Then do an install.  For some reason, grub was installed to all the physical disks, which doesn't make sense. Removing the others should limit any confusion.  After the install and 2 boots that work, reconnect the disks and mount each where you'd like.

Sorry there isn't a clear answer.

---

### Post by oldfred on 2017-05-27
Running Boot-Repair installs grub to every drive.
It is one of the auto-fixes it runs that I do not like. As in many cases users may want different boot loaders in each drive.
But I think it is done so it does not matter which drive is set as default boot, that then it should boot.

Better to use Boot-Repair's advanced mode and choose operating system and then drive to install boot loader.

Note 14.04 should still have the driver. But old video card/chip.
 The stock kernel of Ubuntu 17.04 is doing away with Direct Rendering Manager (DRM) support for a number of ancient graphics processors.
3Dfx Banshee/Voodoo3+, ATI Rage 128, [COLOR=#ff0000]Matrox G200[/COLOR]/G400, SIS, VIA, and Savage hardware
This was done because they expose insecure APIs to user-space. [URL="https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1680276"]https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1680276

[/URL]But your Perc RAID card may be an issue.
[https://serverfault.com/questions/341125/installing-linux-on-dell-poweredge-t-110-perc-s300](https://serverfault.com/questions/341125/installing-linux-on-dell-poweredge-t-110-perc-s300)
[https://ubuntuforums.org/archive/index.php/t-1918254.html](https://ubuntuforums.org/archive/index.php/t-1918254.html)

---

### Post by darkod on 2017-05-28
I also do not see anything very wrong in the boot-repair results. Can you please tell us more info, for example why did you need to repair your boot at all? Was this server working, or it is new install? What made it stop working?

According to boot-repair you have 2x 500GB disks and 2x 2TB. Are you running any raid on the Dell, how are the disks configured? Big problem with branded servers is that it usually does not allow you not using their HW raid card, you have to use one type of raid or another. So when people want to use the disks without raid they usually have no choice except configuring raid0 with single disk for each disk they want to be presented to the OS as a single disk. How do you have your raid?

PS. Another thing that is confusing me in your script results is the kernel 3.13.0-46 that you seem to be running. That is very old, even for 14.04. Aren't you applying updates to your server at all? Ubuntu 14.04 kernels moved from 3.13 to 3.16 and 3.19, and by adding LTS enablement stacks even 4.4 and 4.8 are available.

---

