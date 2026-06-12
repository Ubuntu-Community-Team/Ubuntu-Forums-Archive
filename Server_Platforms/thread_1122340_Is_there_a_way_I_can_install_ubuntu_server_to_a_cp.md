---
title: "Is there a way I can install ubuntu server to a cpu w/o cdrom, floppy and keyboard?"
date: 2009-04-10
forum: Server Platforms
---

### Post by jeffdp78 on 2009-04-10
Hi there!

I had an old cpu 500MHz-celeron, 128MB-mem, 10GB-hdd, 10/100 nic card pci, **...but no usb, no floppy, no cdrom and no keyboard!!!**

Is there a way I can install ubuntu server on it? I'm not sure if there's a way to install it via network because the bios and nic were too old. I mean, it can only boot from floppy/cdrom/hdd...

I have a working lan with 5 ubuntu pc using netgear wgt624v4 router...


***" Yes, I can buy cdrom and keyboard for it but I just wanted to know if there's a different way of installation using hdd and router only, since I'm tinkering linux for my learning. "***


Any thoughts/links? Thanks in advance! ;)

---

### Post by Ravernomina on 2009-04-10
good news to you their is :) you can upgrade the kernel to a server kernel :). It should be some ware in the system repositories. Im sorry i do not know the full name of the kernel or how to get them but u can install them keep this forum up and u will get em :)

---

### Post by jeffdp78 on 2009-04-11
you're giving me hope! :p

I hope someone can give me guides on how to clean install/format, so I can use it via my network.

---

### Post by jeffdp78 on 2009-04-11
Hi there!

I had an old cpu 500MHz-celeron, 128MB-mem, 10GB-hdd, 10/100 nic card pci, ...but no usb, no floppy, no cdrom and no keyboard!!!

Is there a way I can install **ubuntu server** on it? I'm not sure if there's a way to install it via network because the bios and nic were too old. I mean, it can only boot from floppy/cdrom/hdd...

I have a working lan with 5 ubuntu pc using netgear wgt624v4 router...


" Yes, I can buy cdrom and keyboard for it but I just wanted to know if there's a different way of installation using hdd and router only, since I'm tinkering linux for my learning. "


Any thoughts/links? Thanks in advance! ;)







*(This is a doubled post, I don't know how to transfer my old post with exact topic... :confused: from _Networking & Wireless_ sub-forum) ...please delete the old one.*

---

### Post by aurelieng on 2009-04-11
I see two solutions:

- You can buy a cheap external case for the disk or your server, and install a minimal ubuntu server on it using your regular workstation. Then plug it back, boot it, and install what's left :)

- Alternatively, you can set up a [PXE server]("http://en.wikipedia.org/wiki/Preboot_Execution_Environment") on your network and boot from it. Even old BIOS usually came with this feature.

A ["target mode"]("http://en.wikipedia.org/wiki/Target_Disk_Mode"), like macs, would be great on PC for this kind of situation.

Aurel.

---

### Post by BkkBonanza on 2009-04-11
The easy way would be to swap the drive into another machine, install and then put it back.

---

### Post by Elfy on 2009-04-11
> (This is a doubled post, I don't know how to transfer my old post with exact topic...  from Networking & Wireless sub-forum) ...please delete the old one.

I merged them for you - next time you can use the report button and ask for them to be dealt with.

---

### Post by koenn on 2009-04-11
> **BkkBonaza said:**
> The easy way would be to swap the drive into another machine, install and then put it back.
+1

other than that, if there's an operating system on the PC already, you might be able to use that as a starting point.
 
Your problem is always goig to be that you need to run an installer, and the most common way is to **boot** the installer. Without any removable media, that's close to impossible. If there is already a unix-like system on th hard disk, you can use that to run an installer, and by using mount points and/or chroot, you can actually replace the existing system. If it's Windows, maybe you can try to do something similar with wubi ?

PXE will only work if your network card supports it, and other netboot systems usually also require a bootable NIC. Their are workarounds with bootfloppies to trigger e netboot, but you'll need a floppy drive. 

You can even install over a serial or parallel cable, but again you'll need a way of booting an installer ...

And to do all of that keyboardless ? no way. Although the installation can be run quasi handsfree, anything other than a net boot requires you enter boot options. 

Here's some documentation on the debian installer; ubuntu uses the same thing:

[http://d-i.alioth.debian.org/manual/en.i386/apa.html](http://d-i.alioth.debian.org/manual/en.i386/apa.html)
[http://d-i.alioth.debian.org/manual/en.i386/apds04.html](http://d-i.alioth.debian.org/manual/en.i386/apds04.html)
[http://d-i.alioth.debian.org/manual/en.i386/apbs01.html](http://d-i.alioth.debian.org/manual/en.i386/apbs01.html)
[http://www.patoche.org/LTT/install/00000103.html](http://www.patoche.org/LTT/install/00000103.html)

---

### Post by jeffdp78 on 2009-04-14
**Many thanks to all!** I guess swapping drive is my only solution. I will try it, ...the idea is to use it remotely once linux was installed ;)

pxe boot interests me, but doubt for it to work.

@forestpixie//thanks for the merge! It is better this way :p


Thanks again! :KS

---

### Post by jms1989 on 2009-04-14
Don't forget to install a ssh-server in the disk before you put it back in the old computer. 

sudo apt-get install openssh-server

---

### Post by loudog23 on 2009-04-14
I made and USB Start-up disk, and installed my desktop version from there
Get an 1gb usb storage, set the ISO on it, an voila! 

Hope this works with Server version too. :o

---

### Post by koenn on 2009-04-14
I'd would be interesting if you could explain how to do that on a machine with no USB (see OP)

---

### Post by BDNiner on 2009-04-14
You can setup a PXE server but you will need a keyboard for that to work. You need to get into the bios of the machine and set it to network boot. And a lot of times with older computers you will have to hold down a key combination like ctrl+alt to force the network boot to start. That was from my days in Novell Netware environment.

---

### Post by cariboo on 2009-04-14
You can install without a cd-rom or usb, but you are going to need a keyboard as the installer is text based. It doesn't work with a mouse. As well if the motherboard doesn't have a built in nic, you are going to have to install a nic that is that is pxe capable.

Jim

---

### Post by snakdoc on 2009-04-15
still keyboard from one of the other pcs in house :P

---

