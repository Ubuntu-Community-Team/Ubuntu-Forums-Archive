---
title: "dmraid initrd causing boot failure"
date: 2006-11-25
forum: Server Platforms
---

### Post by dantrevino on 2006-11-25
I installed dmraid and now my system wont boot properly.  It looks like during installation a new initrd was built that causes the errors.  I can boot fine with older installed kernels (this system was upgraded from dapper).  I tried booting into 2.6.15 then generating the initrd for 2.6.17 but thats not working.  I've also tried reinstalling linux-image-2.6.17 with --reinstall, but that doesnt work either.

How can I regenerate a clean 'original' initrd?

dan

---

### Post by hondoslack on 2006-11-29
Hi Dan,

the command to rebuild an initramfs is:
update-initramfs -k 2.6.17-xxx (your version here) -r

There is a fancier command that will rebuild the currently booted initramfs, but I like this way for control over which one I'm deleting/rebuilding.

---

