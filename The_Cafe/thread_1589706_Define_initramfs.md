---
title: "Define initramfs"
date: 2010-10-06
forum: The Cafe
---

### Post by A_Nonny_Moose on 2010-10-06
I've been running tests on 10.10 and receiving the updates via the normal channels.  They always seem to update initramfs, which I assume is key to boot loading the system.

My old computer smarts say it means "initialization Random Access Memory File System", but what is it?  Why is it? and what does it do?  The various man pages indicate that it is both a script and a table in memory, but there doesn't seem to be a cohesive definition.  Oh, and one thing more, when is it?

---

### Post by Windows Nerd on 2010-10-06
Wikipedia says: "An initial ramdisk is a temporary file system used in the boot process of the Linux kernel. initrd and initramfs refer to slightly different schemes for loading this file system into memory. Both are commonly used to make preparations before the real root file system can be mounted."

See more by Googling initramfs.

---

### Post by NightwishFan on 2010-10-06
I think for example it can enable modesetting or the framebuffer to print plymouth, or in my recent case enable compcache for compressed ram swap. Things along that line that need to be done first.

---

### Post by nerdopolis on 2010-10-06
AFIK I think a file system image file. (sort of like a virtual disk file for a virtual machine). Its a ram disk, so its a file system that exits in RAM.

I think linux mounts it on the root folder ( / ), and it has scripts and stuff to allow it to prepare filesystem. I think it can have storage drivers for a RAID, or filesystems. Once it loads all the stuff it needs from it, it switches / to be your normal fs, and unmounts the intramfs.

---

### Post by psusi on 2010-10-06
Essentially it is a .tar.gz ( actually cpio instead of tar and lzma instead of gzip ) of a minimal set of files to make up a bare bones system that is passed to the kernel by the boot loader, unpacked in ram, and is then responsible for detecting hardware, locating the root fs, mounting it, and passing control to it.

---

### Post by del_diablo on 2010-10-06
Does not being a ramdisk just mean that its 1 large archive file, and that its suppose to be read and used in 1 go?

---

### Post by psusi on 2010-10-07
What?

---

### Post by del_diablo on 2010-10-07
A zip archive contains compressed files.
A ramdisk contains the files in the order they are read, so the reading goes faster.

---

### Post by Lucradia on 2010-10-07
init = initial or initialize

ram = random access memory

fs = filesystem

You're thinking too hard.

/thread

---

### Post by Ctrl-Alt-F1 on 2010-10-07
> **Lucradia said:**
> init = initial or initialize

ram = random access memory

fs = filesystem

You're thinking too hard.

/thread
What an entirely unhelpful post.  The OP stated that much in his own post.


The posts of Nightwish through psusi pretty much contain my understanding of the matter (which coincidentally I was reading about today in a RedHat/SuSe manual).

---

### Post by psusi on 2010-10-07
> **del_diablo said:**
> A zip archive contains compressed files.
A ramdisk contains the files in the order they are read, so the reading goes faster.

No, a ramdisk is just a disk in ram.  There is no order about it.  initrd stands for initial ram disk, which was a ram disk that was populated from a disk image read by the boot loader, and used as the root fs.  Then they did away with the disk and made the tmpfs filesystem to hold files in ram, rather than use a conventional filesystem on top of a block of ram emulating a disk.  The initramfs is an lzma compressed cpio archive of files that the kernel unpacks into the tmpfs it mounts as the root.

---

### Post by Lucradia on 2010-10-07
> **Ctrl-Alt-F1 said:**
> What an entirely unhelpful post.  The OP stated that much in his own post.


The posts of Nightwish through psusi pretty much contain my understanding of the matter (which coincidentally I was reading about today in a RedHat/SuSe manual).

> **Ctrl-Alt-F1 said:**
> What an entirely unhelpful post.

:)

---

### Post by A_Nonny_Moose on 2010-10-10
Thanks to all.  I am of the opinion that it is a typical programmer portmanteau symbol.  I was as guilty as the next guy when I was coding.  Frankly, too much of this stuff leaks over into the public domain.

---

