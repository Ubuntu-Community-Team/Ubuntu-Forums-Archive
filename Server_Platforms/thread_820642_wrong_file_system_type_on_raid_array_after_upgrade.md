---
title: "wrong file system type on raid array after upgrade to 8.04"
date: 2008-06-06
forum: Server Platforms
---

### Post by SpaceBas on 2008-06-06
hey folks
I've got a doosie ...
I recently upgraded my 7.10 server to 8.04 using do-distro-upgrade
For the most part everything worked, except for my software raid5 array (the most critical part of said server).

Whenever I tried to assemble the array, two of the 4 drives reported a bad superblock (did the upgrade try and write to them?)  after a lot of digging I found a thread here that suggested using mdadm --zero-superblock on each drive then recreating the array.

Since only two the the 4 reported bad superblocks, those where the only two I zeroed out ... when I went to re-create it, there were no errors and 3 hours later it appears to be active and running.

The problem comes when I try and mount it. The volume was (and always has been ext3) but I get this error
```
sudo mount /dev/md0 
mount: unknown filesystem type 'ext4'
```

if I try and specify the file system I get this:
```
sudo mount /dev/md0  /local/media/ -t ext3
mount: wrong fs type, bad option, bad superblock on /dev/md0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```
and dmesg shows
```
[19075.232551] EXT3-fs: md0: couldn't mount because of unsupported optional features (4000000).

```

So, is there a way to change the file system ID? Can I run fsck without fear of corrupting the data? Anyone have any thoughts?

---

### Post by quelx on 2008-06-06
**ext4dev**, the module that provides support for **ext4** file systems, is not included in Hardy.
```
grep EXT4 /usr/src/linux-headers-2.6.24-17-server/.config
# CONFIG_EXT4DEV_FS is not set
```

You will need to rebuild your kernel to include *ext4* support.

[https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)

You will just be adding **File systems** > **Ext4dev/ext4**... as a module (**m** not *****).

---

### Post by fjgaude on 2008-06-16
I'm sure your filesystem was likely ext3 and not ext4... how did you resolve this issue?

---

### Post by dlungs on 2008-11-30
I am having the same problem that was described below, but it occurred after upgrading versions of SUSE. My raid5 array is ext3, but when I attempt to mount it I get the "mount: unknown filesystem type 'ext4'" error, even after specifying -t ext3. Any thoughts? There was never a resolution posted here so I was hoping someone could.

My array still works fine if I go back to the older version of the OS so I know the filesystem is fine.

Thanks

---

### Post by fjgaude on 2008-11-30
Are you moving from one type of OS to another? Like Ubuntu to SUSE?

---

