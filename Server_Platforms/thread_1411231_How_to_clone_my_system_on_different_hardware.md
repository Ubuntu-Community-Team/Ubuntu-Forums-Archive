---
title: "How to clone my system on different hardware?"
date: 2010-02-19
forum: Server Platforms
---

### Post by jmz2 on 2010-02-19
Hello,

I am getting a new server and would like to avoid the typicall install process of OS and aplications.

How can I clone my actual server on a new one that has different hardwre?

Many thanks.

---

### Post by joberly on 2010-02-19
You can probably take the drive out and put it in the new system. Others have done it with no hassles, and it has caused hassles for others. Only one way to find out.

You can also disk image your current drive, and reimage the new one if you are changing drives as well.

---

### Post by The Real Dave on 2010-02-19
If your looking at cloning the harddrive on one system, onto a harddrive in a new system, try [Clonezilla]("http://clonezilla.org/"). It's my favourite imaging software. :)

---

### Post by lisati on 2010-02-19
Another option *might* be [remastersys]("http://www.geekconnection.org/remastersys/remastersystool.html")

---

### Post by windependence on 2010-02-19
The easiest way to remain portable IMHO is to virtualize the machine and then you can either run it virtual or convert it back to physical. ESXi works great for this with VMware converter. DO not use VMware server. You can install ESXi on a flash card or CF or SD card with a simple little $15 adapter and then you don't have to worry about the HD compatibility thing. 

We virtualize all our customers even with just one server because of flexibility. Most of the time they run better than on real hardware.

-Tim

---

### Post by koenn on 2010-02-20
the more orthodox way to do this would be
1- standardize and automate your OS install eg by using a preseed file
2- collect a list of installed software on one system, apply it to the other system (semi-automatically, eg with '--get-selections'' and '--set-selections''
3- reapply config for installed software by copying the relevant files 

here are some ideas:
[http://users.telenet.be/mydotcom/howto/linux/automatic.htm](http://users.telenet.be/mydotcom/howto/linux/automatic.htm)
[http://users.telenet.be/mydotcom/howto/linux/autoinventory.htm](http://users.telenet.be/mydotcom/howto/linux/autoinventory.htm)


I would advise against swapping disks or simply cloning (dd, clonezilla e.a.) because you'd depend entirely on hardware recognition in the new system. it's a "cross your fingers" approach I wouldn't recommend on anything but a hobby project or an experiment. 

Abstracting your hardware by using virtualisation, what windependence suggests,  sounds like a reasonable alternative, although, IIRC, you can't completely abstract the CPU so you might have issues with kernels that are optimized for certain CPU architectures, types, or extensions.

---

### Post by grndslm on 2010-02-23
Here's some hints on how to use Remastersys to customize your own distro, which is what the OP was asking for...

[http://ubuntuforums.org/showthread.php?t=1073838](http://ubuntuforums.org/showthread.php?t=1073838)
-OR-
[http://geekconnection.org/remastersys/forums/index.php?topic=406.0](http://geekconnection.org/remastersys/forums/index.php?topic=406.0)

But what the OP actually *needs* is probly virtualization.  As another poster stated... virtualized systems DO run better than on direct hardware for some reason!  If you've got the appropriate hardware, of course.  You setup everything ONE TIME and then make a copy of the virtual disk, so that you can go a thousand different ways with it and/or start back from that same point again.  Virtualization is really awesome.

---

### Post by tlsarles on 2010-02-23
Completely Agree with windependence.

VMWare ESXi. There is no reason not to, now that they offer it for free. Their VMWare converter application with dump your existing machine onto your new box quick and nearly effortlessly.

---

### Post by nanog on 2010-02-28
> I would advise against swapping disks or simply cloning (dd, clonezilla e.a.) because you'd depend entirely on hardware recognition in the new system.

disagree. if you have problems with hardware recognition after cloning you are also likely to have them on a managed install. in fact, by using dd you often avoid kernel bugs that hamper net/media installs.

---

### Post by koenn on 2010-03-01
> **nanog said:**
> disagree. if you have problems with hardware recognition after cloning you are also likely to have them on a managed install. in fact, by using dd you often avoid kernel bugs that hamper net/media installs.

So if I have, say, an old machine with a AMD K7 MB/CPU and the corresponding linux-image-k7 kernel installed,  with maybe an old 3COM NIC, and I dd the entire contents of the disks to a new system, maybe an all Intel MB/CPU/NIC/... thing, that's going to work ? Reliably ? 
I'd be surprised if it even boots. And if it does boot, I wonder how suddenly the old systems MBR, partition table, /etc/fstab ... is going to match the new system's disks ... 

Whereas, with a preseed, I can easily leave those hardware related issues up to the installer (granted that this will require some manual choices here and there) and have the preseed file provide all the known values such as network config, hostname, locales, keyboard map, time zone, ...

or you could copy/rsync those from an old system ... I see no problem with that. I'd just stay away from kernels, kernel modules, and other hardware-dependent stuff.

---

