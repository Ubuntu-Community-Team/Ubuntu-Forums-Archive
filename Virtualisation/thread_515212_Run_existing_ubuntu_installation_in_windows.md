---
title: "Run existing ubuntu installation in windows"
date: 2007-08-01
forum: Virtualisation
---

### Post by Kent84 on 2007-08-01
There have been lots of tutorials about running an existing windows installation in ubuntu with vmplayer/vmserver, is it possible to go the other way around? 

I have to boot into windows for games. Wine, although good, doesn't work for everything, especially when an ATI card is involved. When I am in windows, sometimes I want to open something in my current ubuntu installation without having to reboot (i.e. I might want bittorrent to be downloading while I play games). So it would be nice if I am able to run my existing ubuntu installation from within windows.

---

### Post by Rocket2DMn on 2007-08-01
Only one operating system can ever run at any given time on a computer.  The OS controls the hardware and running processes, and controls access to the disk and RAM, so having more than one OS would cause a conflict.
You can, of course, share files.  ntfs-3g allows linux to read ntfs file systems and the driver from [http://www.fs-driver.org](http://www.fs-driver.org) allows windows to read ext2/3 file systems, though it is imperfect since it mounts them as ext2.  ext3 can be read and written, but I understand you should be weary.
VMs simulate an operating system under the control of the OS that is actually controlling everything, but there is a loss of efficiency and you cannot simulate a real partition - you have to grant the VM its own resources which the native OS allows it to (and sometimes not to) manipulate.

---

### Post by Kent84 on 2007-08-01
So you are saying that [this link]("http://www.thinkdigit.com/forum/showthread.php?p=558695"). And about a dozen different posts on running an existing windows installation in ubuntu with vmplayer don't work and are complete rubbish?

---

### Post by Rocket2DMn on 2007-08-01
I did not know you could virtually simulate an existing partition, I thought you had to grant the VM it's own drive space.  I guess it makes sense that you can, but I wouldn't be too terribly trusting with windows running your Ubuntu partition.  If you figure it out, do post.  Good luck.

---

### Post by bodhi.zazen on 2007-08-01
Booting an existing partition is IMO in Alpha development, meaning breakage can occur ...

You can run VMWare, Virtualbox, or qemu in Windows and run Linux within windows.

You can consider running a light weight Linux distro like DSL or Puppy or live CD's like Wolvix and ZelLive as an alternate to Ubuntu (might be faster ...)

I would advise making a virtual hard drive ...

You can try it, boot windows, launch VMWorkstation,

Menu -> New -> Virtual Machine

Virtual Machine Configuration -> Custom

Guest Operating System -> Linux, Version : Use Other Linux 2.6.x kernel

Name : & Location -> Your choice

Disk -> Use a physical disk

Device -> select your partition to boot and Use entire disk

Once you boot the hard drive, you should see GRUB ... SELECT UBUNTU 

You will likely need to re-configure X

Good luck ...

---

### Post by Kenai on 2008-02-23
> **bodhi.zazen said:**
> 
You can run VMWare, Virtualbox, or qemu in Windows and run Linux within windows.

 ...

You can try it, boot windows, launch VMWorkstation,


Question here- would VMware Server also suffice? I do not have the ~200 dollars needed to buy the workstation edition, though VMware seems to be the best option thus far.

Also, would Microsoft's own Virtual PC 2007 be able to launch an existing Ubuntu install? This system seems to have some mouse problems when Ubuntu is installed from inside the VM, would this have an effect?

-Kenai

Edit- Virtual PC 07 doesn't work for a physical drive as far as I can tell...

And, I have my Ubuntu installed on my USB hard drive... VMWare Server doesn't have it among it's list of partitions. :( Is there any way to work around this?

---

### Post by bodhi.zazen on 2008-02-23
VMWare server should work just fine, I bet that is what most around here run ;)

That is what I run when I VMWare :twisted:

---

### Post by bitterbug on 2008-02-24
I'm really looking forward to hardware hypervisors that will let us divide the cores/hardware among the OSes of our choice. 90% of the time my dual core 2.6 would be plenty of horsepower to be running both ubuntu and xp with full hardware access.

:drool:

---

### Post by raditzman on 2009-07-16
Has anyone here successfully ran an existing linux partition (or instalation) in windows? Because I want to be able to keep downloading my stuff in linux while I play games in windows (Vista). Thanx for any reply.

---

### Post by bodhi.zazen on 2009-07-16
> **raditzman said:**
> Has anyone here successfully ran an existing linux partition (or instalation) in windows? Because I want to be able to keep downloading my stuff in linux while I play games in windows (Vista). Thanx for any reply.

I have not personally done it, but it should be easy with either VMWare or VirtualBox. 

Running Linux, as a guest, on windows is probably easier then running windows as a guest on Linux.

Unless you have good reason though I suggest you simply create a virtual HD , it is sasier and booting a physical partition is a long run for a short slide.

Another great option is Portable Ubuntu.

[http://portableubuntu.demonccc.cloudius.com.ar/](http://portableubuntu.demonccc.cloudius.com.ar/)

Portable Ubuntu is fast, light weight, and you have full access to your C:\ drive from the Ubuntu guest.

---

