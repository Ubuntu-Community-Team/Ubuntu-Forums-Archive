---
title: "mksquashfs and luks = error?"
date: 2009-06-17
forum: Security
---

### Post by yogg on 2009-06-17
Hi

I try to format a luks encrypted file with squashfs. But this ends with a strange error

```

// create a 200MB file
dd if=/dev/urandom of=filesystem bs=2k count=102400

// setup the loop
losetup /dev/loop0 filesystem

// setup the luks encryption
cryptsetup luksFormat -c "aes-cbc-essiv:sha256" /dev/loop0

// open the luks encrypted device
cryptsetup luksOpen /dev/loop0 luksloop

// try to make the squashfs
mksquashfs /home/user/livecd/work/chroot /dev/mapper/luksloop -noappend -e /home/user/livecd/work/chroot/boot
->
Parallel mksquashfs: Using 2 processors
Creating little endian 3.1 filesystem on /dev/mapper/luksloop, block size 131072.
[=====                                                       ]  2440/27528   8%Lseek on destination failed: Invalid argument
[=====                                                       ]  2513/27528   9%Lseek on destination failed: Invalid argument

// make ext3, et4, ntfs, ... works without problems
mkfs.ext3 /dev/mapper/luksloop

```Has anyone an idea what I make wrong?

---

