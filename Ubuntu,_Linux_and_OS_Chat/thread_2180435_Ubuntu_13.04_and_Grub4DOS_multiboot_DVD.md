---
title: "Ubuntu 13.04 and Grub4DOS multiboot DVD"
date: 2013-10-13
forum: Ubuntu, Linux and OS Chat
---

### Post by zanoni2 on 2013-10-13
This has been tested and it is working with Grub4DOS multiboot cd/dvd.  I'm posting it here because I couldn't find it anywhere else, and I think is the right place.  I like having different versions of Ubuntu Live in one DVD.  Why carry 2 or more CD/DVDs when you can carry one?

Keep in mind that the ISO files were kept on the root of the folder making the ISO (in other words, the ISOs would be found in the root of the DVD once made).  Also, I renamed the ISO files to keep it compatible with some older OSs when reading the DVD (I have other OSs booting in the same DVD, not just Linux Mint).

Here is the "menu.lst" settings:


title Ubuntu 13.04 X64 Desktop
find --set-root /U1304X64.ISO
map --heads=0 --sectors-per-track=0 /U1304X64.ISO (0xff) || map --mem /U1304X64.ISO (0xff)
map --hook
root (0xff)
kernel /casper/vmlinuz.efi file=/cdrom/preseed/ubuntu.seed noprompt boot=casper iso-scan/filename=/U1304X64.ISO quiet splash locale=de_DE.UTF-8 --
initrd /casper/initrd.lz


PLEASE:  If anyone finds a better Grub4DOS menu settings, do let me know.  These settings have been working flawlessly so far...

---

