---
title: "How do I mount an entire hard drive image?"
date: 2013-12-17
forum: Virtualisation
---

### Post by davethewave83 on 2013-12-17
I have a drive image that I need to mount, boot sector and all. 
The common method of _mount -o loop, -t ntfs offset=number image.img /mnt/drive_ doesn't apply to me, 
I need to do what it tells me I'm trying to do when I try _mount -o loop, image.img /mnt/drive_

"Maybe the wrong device is used? **Or the whole disk instead of a partition**" 

exactly this though, whole disk. I don't want to mount a partition, I need to be able to access the whole drive including boot sector. 

any ideas? 

I know this is possible in Windows, so I assume it must be in Linux

---

### Post by electrohandyman501 on 2013-12-17
What type of file is the image you are trying to mount. Is it a VMWare or Vbox image? or something else.
Do you have the individual partition information?

It may be a little more involved, but what about just mounting all the individual partitions.
You will still end up with access.

Just brainstorming here.

---

### Post by tgalati4 on 2013-12-17
There is a good reason for not being able to mount an entire device--like destroying all of the data contained on it.  The kernel expects a partition with a specific, supported, file system on it to create a mount point.  If you need to operate on the entire physical disk, then there are forensic tools that can read/copy the disk (like *dd*) and then you can operate on the output of that--an ISO file, or a partition table, or a directory tree, etc.  

I won't post the commands, but you can *cp* an entire device to a file.  You just need a really big disk and a lot of time.  Then you need some tools to read the file.  You can also *cp* one device to another--small drive to a bigger drive for instance.

What is it that you are trying to do?  My guess is that it will be different than what you are used to in Windows.

---

### Post by davethewave83 on 2013-12-18
My laptop has no boot capability, the dvd drive is shot, the USB doesn't support booting, the hard drive contains Windows but I'd like to switch it over to Linux, so I used a hex editor HXD to copy all of the sectors of the hard drive to a file HardDrive1.bin in raw output. My plan was to transfer this hard drive image to this machine I'm on now which is running linux, then to mount the image, install linux and re-write all the sectors straight to the Windows drive so that it contains the grub boot loader and loads linux. 

The problem is, If I only mount each partition, this won't give me access to sector 0, which means grub won't be on the drive, so it will fail to boot and I'll end up with a dead laptop and no OS. 

alternatively I can disassemble the laptop, pull the hard drive out, connect it to the PC with a hard drive (laptop/standard IDE) converter and install that way, but I wanted to first try it the image way since I don't like to disassemble laptops.

---

### Post by tgalati4 on 2013-12-18
I had an old HP Omnibook with a similar dilemma.  I just took the hard drive out, used a 3.5" IDE ribbon adapter and plugged it into a spare desktop computer.  Then I did a normal install.  After testing, I took out the drive and put it in the laptop and it worked fine.

You can use *dd* to copy the *.bin file to a device.  You would need to specify the correct sector or block size.

I think it would be easier to take the drive out, use a USB enclosure and install from another computer then reinstall the drive.

I bet your laptop BIOS supports PXE boot.  You could activate PXE and hook the laptop to a wired network and then set up the appropriate PXE boot server.  Once booted to a command line, you now have some tools to perform a network installation.

---

### Post by TheFu on 2013-12-19
If you just need to copy an entire HDD, use **ddrescue** from any bootable Linux available.  You can mirror everything on the physical HDD to another HDD or to a file ... every bit, byte, everything.  Be very careful to check the command options - if you get them backwards, you will completely destroy all the data on the target HDD.  Please be very careful, please.

DO NOT MOUNT the partition or HDD to accomplish this.  **ddrescue** is a safer version of **dd**. It doesn't give up when a sector failure is discovered. It tries hard to get every bit copied possible.  If the physical HDDs do not have matching sector sizes (512b vs 4Kb), then it would be smarter to setup the partitions outside using any bit-for-bit mirror tool to avoid sector alignment performance issues (50% slower access if the alignment is off) .... take a look at ...
**fsarchive ** can be used to mirror many file systems.  It is smarter than dd/ddrescue, since it understands empty disk areas and uses compression.

The boot sector really isn't anything magical under Linux.  From any live-boot media (USB, CD, DVD) you can reinstall grub2 using grub-install.  Alas, we need to handle 1 question at a time here to limit confusion. There are lots of how-tos for grub, but for many people using **boot-repair** is the easiest. See my signature for links.

Of course, before starting anything at this level it is a good idea to have a 100% backup of any of the data involved.

---

