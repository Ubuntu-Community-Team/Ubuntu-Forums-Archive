---
title: "Virtual Floppy Drive"
date: 2010-07-25
forum: Virtualisation
---

### Post by jmpeer on 2010-07-25
What is the quickest way to format a bootable .bin file to an .img file and mount it in a virtual floppy drive in terminal? Since I don't have a floppy drive, I need a virtual floppy to test something in virtual box. 

I tried using dd, mkfs, and mount, but I kept having a problem with the .img filesystem I think.

Answers are much appreciated.
I'm not completely Linux retarded.
But I'm retarded enough to overlook obvious mistakes. 

^_^

---

### Post by vinnie1 on 2010-07-26
Hi

 I have just done this today with Virtualbox. Here's the steps

 sudo mkfs.msdos -C /home/vincent/floppy.img 1440
 
 sudo chown user.user ./floppy.img   (change user.user to your name)

 Thats it, start Virtualbox use the media manager and select it as a floppy device. In windows(within Virtualbox) it appears as a floppy disk which I can read / write to and even reformat it.
 
 If you want to mount it in Linux try

 sudo mount -o loop /home/vincent/floppy.img /media/floppy/  (this assumes you have a /media/floppy folder, if not make one or use another folder)


I used this to practice automated XP installs in Virtualbox, and of course like you I don't have a floppy drive.

---

### Post by SpawnHappyJake on 2012-05-20
I know this is a little anal-retentive/OCD, and that this thread is a little old, but I feel the need to do some Internet clean-up here for the sake of future knowledge seekers:

It's important to realise that a plain vanilla Linux kernel does _not_ have the ability to emulate hardware. A plain vanilla Linux kernel _does_ have the ability to take an image of a filesystem and mount it.

You can image any filesystem with dd and mount it in Linux. All this is doing is having the files in that filesystem image displayed in the directory where you mount the image to. It does not emulate hardware.

Pull up terminal and do the following: "sudo lshw | more". Or even better, "sudo lshw > $HOME/Documents/my_hardware.txt", then view my_hardware.txt.

Run lshw before and after mounting a floppy image with the mount command. It will have absolutely no effect on the hardware list. You are not emulating a  floppy drive, or else it would show up in the hardware list.

Now get an iso image of a CD or DVD. Check lshw before and after mounting it with the mount command. Again, no emulation of hardware.

Now install CDEmu and mount the iso with CDEmu. Now check lshw. Ah. Now it's in the hardware list. Now you're emulating hardware.

Only the kernel has the privileges necessary to see hardware, so all non-kernel programs only know anything about hardware from the information the kernel feeds them. Thus hardware can be emulated simply by the kernel lying and saying there is this (non-existent) hardware. That is what CDEmu does via a kernel module.

Of course there is more to emulating hardware than just showing up in the hardware list, and CDEmu does quite a few things, such as responding to certain protocols, such as the SCSI command set and whatever the Raw DAO 96 protocol is.

I have searched and not found a single floppy drive emulator for Linux. However, mounting a floppy image with the mount command is often sufficient for what people are trying to do.

Cheers,
Jake

---

