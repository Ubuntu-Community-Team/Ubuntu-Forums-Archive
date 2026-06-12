---
title: "Installation of Ubuntu renders Windows 7 unbootable with GRUB error message"
date: 2015-01-21
forum: Windows
---

### Post by ben134 on 2015-01-21
I recently installed Ubuntu 14.10 over an old linux installation, which is on a separate partition of my HDD with Windows 7 on the other partition. Unfortunately, the replacement of GRUB with a newer version has made my Windows 7 installation unbootable.
When I boot the computer, the GRUB menu comes up, and I am able to select between my current Ubuntu install, an old Win 7 install that is on a separate hard drive, and my desired Win 7 install. Both the Ubuntu and old Win 7 options work fine, however the desired Win 7 install results in a "grub_term_highlight_color" not found error message. (This is after I select the option in the GRUB menu) After extensive research online and in the forums, I know that this error message is due to a bad installation of GRUB, and so I followed directions to fix the GRUB install, however the problem was not solved. My current suspicion is that the current Win 7 loader has an old version of GRUB that refuses to be updated, however I cannot seem to find it.

Here is the log from boot-repair:[ http://paste.ubuntu.com/9812275/]("http://paste.ubuntu.com/9812275/")

Additional information that may be useful:
- Ubuntu 14.10 was installed over Linux Mint (unknown version but a couple years old at this point) using the "Something Else" option; the linux partition (/dev/sdb5) was reformatted and resized.
- Windows partition was left untouched
- Windows partitions on /dev/sda1 2 and 3 are the old Win 7 install on an HDD that actually belonged to another computer. They can be successfully booted from.
- According to log linked above, the desired Win 7 partition is /dev/sdb2, however this partition is not listed in the GRUB menu (sda1,sda2,sdb1 are listed, along with Ubuntu)
- Tried repairing GRUB using dpkg-reconfigure grub-pc, boot-repair
- BIOS boots to /dev/sdb, however updated GRUB is installed on /dev/sda as well and produces exact same results

Hopefully I can be enlightened as to where the problem is. If there is any other information needed, just ask
Thanks!

---

