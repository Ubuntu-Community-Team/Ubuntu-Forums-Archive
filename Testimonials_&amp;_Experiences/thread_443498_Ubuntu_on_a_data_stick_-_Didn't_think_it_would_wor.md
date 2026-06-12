---
title: "Ubuntu on a data stick - Didn't think it would work"
date: 2007-05-14
forum: Testimonials &amp; Experiences
---

### Post by ironfistchamp on 2007-05-14
Hey all

Today I hijacked my mates Lappie and data stick (4GB). I backed up his work and proceeded to install Feisty onto the data stick from my new CD's. Damn I love shipit. Anyway I always have trouble with installing an OS but for once this one went perfectly. No problems at all. All the hardware was recognised and it worked first time.

I am so impressed with Feisty.

Anyway has anyone else managed to install Ubuntu on removable media? What has been your experience with this type of thing?

Oh yeah there was one problem. GRUB installed to the stick aswell it seems. Windows will now not boot if the stick is not in the machine. Hmm will need to sort that one later.

Ironfistchamp

---

### Post by MontanaMax on 2007-05-14
I was shopping for a 4 gig thumb drive and ran across ones at MadTux.com that come pre-installed with bootable Feisty. I figured as long as I'm going to buy a thumb drive, I might as well support a vendor who is commercially offering Linux. I'm hoping it will be delivered this week and will let you know if I spot anything unusual about the setup that they might have done to make it work.

---

### Post by BigSilly on 2007-05-15
Is there a guide anywhere about how to do this? It's not for me, but I have a friend who is an Ubuntu user and wants to try this for himself. If you can help, please let me know. Thanks.

---

### Post by ironfistchamp on 2007-05-15
I didn't use a guide it was pretty much like a normal install. All I did was plug the stick in, boot from a Feisty CD and when it came to the partitioning I selected to use the entire disk. It mounted it as sdb but it could be anything on yours. I knew it was that one as it put the name of the disk next to it.

After that just install as you normally would.

HTH

Ironfistchamp

---

### Post by PointSource on 2007-05-15
Me, personally, I did it a different way.

From numerous howtos and guides (I have no idea where they all are so don't ask), I found you can make a USB stick bootable by:
1. Copy contents of live ubuntu CD onto stick (fat16/fat32 primary partition)
2. Move contents of isolinux directory into root directory
3. Move vmlinuz and initrd.gz from casper directory into root directory
4. Get packages mbr and syslinux
5. Rename isolinux.cfg to syslinux.cfg
6. Edit syslinux.cfg so:
   - all instances of "/casper/vmlinuz" are changed to "vmlinuz"
   - all instances of "initrd=/casper/initrd.gz" are changed to "initrd=initrd.gz"
7. Run command "install-mbr /dev/sdX" POTENTIALLY DANGEROUS make sure the "/dev/sdX" is your USB stick
8. Run command "syslinux /dev/sdX#" make sure the "/dev/sdX#" is the partition on your USB stick that has the cd image

If all has gone well then you should have a bootable ubuntu liveUSB. If not, then I'm afraid I can't help you.
I hope I got the instructions right!

---

### Post by BigSilly on 2007-05-15
Many thanks people. I'll forward a link to this page to my mate. That's pretty cool actually, sticking Ubuntu on a USB drive. Who woulda thunk of it?

Cheers again. :)

---

### Post by ironfistchamp on 2007-05-15
@ PointSource:  Wow I had never thought of making a liveUSB. Ours was just a regular install of Ubuntu. quite good as Ubuntu always seems to work out what hardware we are using. I managed to get it to work on my computer straight off. Just plugged it in and off I went.

---

### Post by happybrick on 2007-05-15
A guide to running various distros from flash drives can be found here:
[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

I got Edgy working on a 4GB flash drive though haven't done much with it since. I also had it running with QEMU emulator so I could run both XP and Edgy at the same time on the one machine. Useful when you're learning and you haven't quite got wireless working in Ubuntu.

---

### Post by Tux.Ice on 2007-11-11
i cannot get it to work installing gutsy on my 4gb adata drive

oh well

trial and error

---

### Post by aselya1 on 2008-01-16
Tux.Ice: What problems did you have? Were you trying to do a LiveUSB or an actual install? I personally love my LiveUSB, but I used GRUB, not Syslinux to bootload. You can also leave a partition for Windows to recognize and use for 'normal' USB drive shuttling of files, etc.

---

### Post by wolfen69 on 2008-01-16
> **Tux.Ice said:**
> i cannot get it to work installing gutsy on my 4gb adata drive

oh well

trial and error

it took me 3 or 4 tries to get gutsy to work on my 4gb drive. but, it is really cool. you can bring your computer in your pocket. [http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/](http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/)

---

