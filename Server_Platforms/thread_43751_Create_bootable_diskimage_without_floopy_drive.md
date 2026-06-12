---
title: "Create bootable diskimage without floopy drive"
date: 2005-06-23
forum: Server Platforms
---

### Post by banishedknight on 2005-06-23
Hi,

for a diskless client I want to create a boot cd.
I found tons of instructions to compile the kernel with nfs root fs and create a bootdisk. But my problem is, I do not have a floppy drive  :-| (neither a working disk)

My first idea was to mount a empty file(2.88MB created with dd) as fs (with losetup) and use this as 'virtual floppy'.
But when I try to install lilo on it, it says it can't operate on a 'logical device'. 
It seems like my 'virtual disk' does not have a boot sektor   :-? (or sektors)...

How can I create a working bootable disk image to burn it on cd later?

Thanks in advance,
Oliver

---

### Post by Lunde on 2005-06-23
[QUOTE=banishedknight]Hi,

for a diskless client I want to create a boot cd.
I found tons of instructions to compile the kernel with nfs root fs and create a bootdisk. But my problem is, I do not have a floppy drive  :-| (neither a working disk)

My first idea was to mount a empty file(2.88MB created with dd) as fs (with losetup) and use this as 'virtual floppy'.
But when I try to install lilo on it, it says it can't operate on a 'logical device'. 
It seems like my 'virtual disk' does not have a boot sektor   :-? (or sektors)...

How can I create a working bootable disk image to burn it on cd later?

Thanks in advance,
Oliver[/QUOTE]

What if you download a boot image from the net.. you can actually download an .exe bootdisk extractor and open it in Archive Manager and extract the disk.img

[www.bootdisk.com](www.bootdisk.com) has a lot of downloadable images

I've managed to create disk images before, but I can't remebmer how.. I think it has something to do with that it has to have the ending .img

What do you want to do with this boot cd?

---

### Post by banishedknight on 2005-06-23
[QUOTE=Lunde]What if you download a boot image from the net.. you can actually download an .exe bootdisk extractor and open it in Archive Manager and extract the disk.img

[www.bootdisk.com](www.bootdisk.com) has a lot of downloadable images

I've managed to create disk images before, but I can't remebmer how.. I think it has something to do with that it has to have the ending .img

What do you want to do with this boot cd?[/QUOTE]

I want to boot a diskless client with this CD (the board is too old to support booting from net and I do not have a boot rom for my lan card).

The kernel has a specific option to use a nfs mount for the root filesystem, this is very good documented. My problem is to create the diskette image for the CD. The tricky thing is to create a image, copy the kernel into it and install lilo on it without going over a floppy drive.... 
I've tried to mount a 2.88MB file with a loopback device, but lilo can't operate on it :(
 
Because I have to compile the kernel by myself for the NFS root filesystem, I can't use a image from the net...

---

### Post by Lunde on 2005-06-23
[QUOTE=banishedknight]I want to boot a diskless client with this CD (the board is too old to support booting from net and I do not have a boot rom for my lan card).

The kernel has a specific option to use a nfs mount for the root filesystem, this is very good documented. My problem is to create the diskette image for the CD. The tricky thing is to create a image, copy the kernel into it and install lilo on it without going over a floppy drive.... 
I've tried to mount a 2.88MB file with a loopback device, but lilo can't operate on it :(
 
Because I have to compile the kernel by myself for the NFS root filesystem, I can't use a image from the net...[/QUOTE]
 Maybe this helps:

[http://rescuecd.sourceforge.net/288.html](http://rescuecd.sourceforge.net/288.html)

---

### Post by banishedknight on 2005-06-24
[QUOTE=Lunde]Maybe this helps:

[http://rescuecd.sourceforge.net/288.html](http://rescuecd.sourceforge.net/288.html)[/QUOTE]

Woohoo, this looks good, thank you very much.

---

