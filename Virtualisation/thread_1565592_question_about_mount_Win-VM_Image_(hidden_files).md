---
title: "question about mount Win-VM Image (hidden files?)"
date: 2010-09-01
forum: Virtualisation
---

### Post by pred2k on 2010-09-01
EDIT:
Sorry got the wrong image file.
----------------
Hi, i try to mount my Windows XP KVM qcow2 Image on my host-system.
First i did this:
```
sudo modprobe nbd max_part=8
sudo qemu-nbd --connect=/dev/nbd0 xpsp2.qcow2
sudo mount  /dev/nbd0p1 /mnt/hdd
```

ls -al /mnt/hdd shows this content:
```
-rwxrwxrwx  1 root root      234 2008-11-08 01:04 boot.ini
-rwxrwxrwx  1 root root    36352 2005-03-25 13:00 NTBOOTDD.SYS
-rwxrwxrwx  1 root root    47772 2005-03-25 13:00 NTDETECT.COM
-rwxrwxrwx  1 root root   295536 2005-03-25 13:00 ntldr
-rwxrwxrwx  1 root root 41943040 2008-11-08 01:00 PAGEFILE.SYS
drwxrwxrwx  1 root root     8192 2008-11-08 01:03 WINDOWS

```Nice to see its is working. 
**But where are The Folders Document and Settings, Program Files, etc?**
I try to convert it to raw and mount it again:
```
qemu-img convert -f qcow2 xpsp2.qcow2 -O raw xpsp2.raw
sudo mount -o loop,offset=32256 xpsp2.raw /mnt/hdd2/
```
Still the same content.

Is there a ntfs mounting Problem?
Or is the problem because it is qcow2?

---

