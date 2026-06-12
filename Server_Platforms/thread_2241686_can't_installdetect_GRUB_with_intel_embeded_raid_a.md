---
title: "can't install/detect GRUB with intel embeded raid array"
date: 2014-08-27
forum: Server Platforms
---

### Post by wild_dog on 2014-08-27
I have been struggling with this for weeks, trying every bit of help online that I could find, but one half is out of date (for Ubuntu versions 9.xx or lower) and the other half simply didn't work.
So I have come here in the hope I could get some help that applies directly to the trouble I am having.

Here is the background:

I recently bought a server from around 2006, with an Intel s5000pal motherboard which has "Intel® Embedded Server RAID Technology II" in order to create RAID arrays (after some reading up, it seems this is a form of Fake RAID).
I have used this technology to put 6 2TB hard disks in a RAID 5 configuration, giving me 10TB of space to install/store everything.
I want to use the RAID 5 array because this server is going to be used as a data backup/synchronization server using OwnCloud, so I really don't want to lose data if a drive fails for whatever reason.
And I also want to use the embedded RAID functionality because, well, having a server with embedded RAID capability (and buying an 80$ RAID key to enable RAID5) and then not using it seems just preposterous to me.
Installing the server version of the OS goes fine, the RAID array is properly recognized and partitioned, and all software seems to get installed properly, except the GRUB2 boot loader.

I have tried a lot of possible solutions, mounting the RAID array under different names and trying to install GRUB there during the initial installation, installing without GRUB and trying to install it later using a live DVD and even setting the /boot mount point to a USB flash drive and installing GRUB on there, but so far, none have worked.

In the first case (during initial installation), the installer would simply fail saying it couldn't execute grub-install on the specified location.
In the second case, it appears I managed to install GRUB in the RAID array with the other files/programs but the BIOS doesn't "see" the boot loader and skips to network booting.
in the third case, it appears it installed GRUB in the version meant for EFI secure boot, and trying to get it to install the normal version has so far failed. (Most of those failed attempts have to do with problems with the canonical path of /cow)


I am at a loss about what to do now, any help would be much appreciated

---

