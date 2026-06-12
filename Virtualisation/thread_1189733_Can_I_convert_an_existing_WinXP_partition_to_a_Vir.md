---
title: "Can I convert an existing WinXP partition to a VirtualBox HD image?"
date: 2009-06-17
forum: Virtualisation
---

### Post by Zeikcied on 2009-06-17
I thought I would reword my post and try again (with a subject line that indicates a question as opposed to a tutorial).

I have VirtualBox currently set to run my Windows XP partition as a virtual machine.  For obvious reasons I'm no longer able to boot it as a normal OS.  I would like to know if it is possible to convert it to a hard drive image that can be used by VirtualBox?

I tried booting my VM and using VMWare Converter.  However, when I tried adding an ext4 partition as a Shared Folder to put the converted drive image, Windows apparently thinks that it has the same 2 Gig limitation as FAT32, and the program insists that the drive be split into 2 Gig chunks.  If this is indeed the only way I can make this work, then is there a way to combine the file chunks after the conversion?

---

### Post by Zeikcied on 2009-06-24
I found some methods on the VirtualBox forums, unfortunately I'm not having a whole lot of luck.  All methods I tried involved creating a .vdi file and making it the slave for the VM.

One method involved a program called HDClone.  Its free version only lets you a Drive-to-Drive clone.  But I can't seem to get the .vmdk file I use to boot my physical WinXP partition to use only that partition.  Instead it reads the whole drive (including two Linux partitions that WinXP sees as "Unknown"), so the HDClone method won't work.

Another method involved SelfImage, another program for cloning a drive.  My problem with that is the program didn't work right for some reason.  I would select Drive, and the drop-down menu would be completely blank and displaying improperly.

I also tried booting the Kubuntu Jaunty disc within the VM and using Gparted to copy the WinXP partition over to the .vdi slave.  That worked, and WinXP booted from the .vdi file afterward.  But once it scanned the disc and rebooted, it would only get so far and stop booting.  It gets to what is usually the Welcome screen right before the Explorer shell starts, and it just shows the "Windows XP" logo.  It never changes to "Welcome" and doesn't give a login screen.  It just stops there.

I don't have a Windows XP disc, and buying one is much too expensive.  Other methods I've seen require an existing WinXP VM, separate from the physical partition, which seems odd to me (if you have a working WinXP VM, why would you need to boot a physical partition in the first place?).

I've been stressing over this all day and I'm about at my wits end.  I don't know what to do.

---

### Post by {CGL}ToWeR on 2009-07-14
Im sure its possible.

Im working on that too.  For a start though, can you boot the winXP vm into safe mode? IE keep pressing f8 at the beginning of boot and choose safe mode.

If it gets in ok then its just a matter of drivers and vm settings... Also post your virtualbox version.

---

### Post by wcasper4 on 2009-07-14
I believe I have done what you are trying to do, however, I am having issues with having to reactivate windows everytime I boot from vbox or natively.. but I believe this is what you want to do, but I need help getting around the reactivation issue if you know how

follow this if you want but you may have the activation issue unless you can figure that out [http://ubuntuforums.org/showthread.php?t=1212702]("http://ubuntuforums.org/showthread.php?t=1212702")

---

### Post by RealG187 on 2009-07-14
I think you can, but am not sure as to how...

I know when I ran VMWare workstation I had the option to use a real partition, although it was advanced

---

### Post by Zeikcied on 2009-07-15
I found my solution via the VirtualBox forums.

Basically, I took an empty .vdi file and attached it as the Slave drive to my WinXP VM, which had the .vmdk file (which uses the physical WinXP partition) as the Master.

I then booted the Kubuntu Jaunty disc image and used Gparted to copy the WinXP partition from the physical drive to the .vdi drive.  My first attempt apparently didn't work properly, but the second attempt was fine.

---

### Post by RealG187 on 2009-07-15
VMDK file? That's what VM Ware uses I thought you were using Virtual Box? Same for VMWare Converter.

---

### Post by Zeikcied on 2009-07-15
> **RealG187 said:**
> VMDK file? That's what VM Ware uses I thought you were using Virtual Box? Same for VMWare Converter.

VirtualBox can apparently use VMDK files.  At least for reading physical partitions.

---

### Post by RealG187 on 2009-07-16
> **Zeikcied said:**
> VirtualBox can apparently use VMDK files.  At least for reading physical partitions.But a VMDK file is not a physical partition, what do you mean?

---

### Post by Zeikcied on 2009-07-23
> **RealG187 said:**
> But a VMDK file is not a physical partition, what do you mean?

There's a program that comes with VirtualBox (maybe the closed source version only) that lets you create a VMDK file that's configured to read a physical partition.

There's a tutorial on these forums, but I think it's been changed since I used it.  The version I used more resembles this: [http://mesbalivernes.blogspot.com/2008/01/virtual-box-booting-from-existing.html](http://mesbalivernes.blogspot.com/2008/01/virtual-box-booting-from-existing.html)

I used that to create a .mbr file, then a VMDK file that uses the .mbr file as the MBR for that VM.  Then it points toward a physical partition.

---

