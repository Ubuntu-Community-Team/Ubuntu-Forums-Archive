---
title: "New sysadmin - I don't know where to start"
date: 2007-11-20
forum: Server Platforms
---

### Post by leeping on 2007-11-20
Dear community,

I'm starting some sysadmin responsibilities for my group, and I've decided to use Ubuntu 7.10 Server Edition to manage our computing cluster.

I'm figuring out how to configure the head node right now - and I need to configure it as a DHCP server for the compute nodes.  I would also like to learn how to install Ubuntu from the head node via LAN (The hope is to standardize the OS for the compute nodes, and install the OS image with a single command.)

If my questions are overly basic, then please point me to the correct tutorial section, and I would appreciate that very much as well.

Thanks everyone,

- Lee-Ping

---

### Post by rmemm on 2007-11-22
I'm personally not certain that Ubuntu is really setup for this.  Sounds like you want to build a beowulf cluster?

There are some distros specifically for this I think.  Also there are venders that sell pre build cluster systems with the software pre configured.

From memory there is one called ClusterKnoppix for example.  There is a beowulf system called Scyld Beowulf (commercial).  I'm sure there are others.  Not used any of them myself -- except at work we are buying something pre-setup from SGI.

You should probably search the web for "beowulf cluster" to find some of the how toos.

Rob

---

### Post by sciurus on 2007-11-22
Take a look at [http://oscar.openclustergroup.org/](http://oscar.openclustergroup.org/) and [http://www.rocksclusters.org/](http://www.rocksclusters.org/) for specialized cluster distros.

Buy the book "High Performance Linux Clusters with OSCAR, Rocks, OpenMosix, and MPI" from O'Reilly.
[http://www.oreilly.com/catalog/highperlinuxc/index.html](http://www.oreilly.com/catalog/highperlinuxc/index.html)

Also, buy the book "LPI Linux Certification in a Nutshell, Second Edition  " from O'Reilly as a general, task-oriented reference.
[http://www.oreilly.com/catalog/lpicertnut2/index.html](http://www.oreilly.com/catalog/lpicertnut2/index.html)

---

### Post by leeping on 2007-11-25
Hey there,

Thanks for the replies.  Indeed, I'm trying to make a Beowulf cluster. :)

I've looked at Rocks, and I've actually tried quite hard to install it on one of the new nodes.  I'm running into some serious hardware compatibility issues, which is discouraging especially when Ubuntu installs on the nodes flawlessly.

Rocks is feature-packed, but for a relatively small operation such as ours, we only need a queueing system and a node management system.  I think it should be doable with just Ubuntu .. maybe simplicity is the best thing.

Let me know what you think.  I should look at OpenMosix and buy those books.

Thanks,

- Lee-Ping

---

### Post by rmemm on 2007-11-28
Ubuntu -- yes you could use ubuntu -- the biggest issue I have is that you'll have to build and install a lot of your own stuff.  Specifically I don't think Ubuntu has a queuing system, I also don't think it supports automatic node provisioning, boot, etc.  So yes of couse you could do it -- but it will take some effort.

You might want to look at the Quantian Live CD.  Just stick in the live CD in each computer, reboot and your mostly setup.  I've used Quantian as a utility CD -- but not as a cluster -- but it looks interesting.

[http://dirk.eddelbuettel.com/quantian.html](http://dirk.eddelbuettel.com/quantian.html)

It has clusterknoppix built in and it has openmosix built in -- to pretty good things.

The other thing I would consider -- look at some of the cluster distribution -- just to see what tools they use -- then install a minimal subset of these on ubuntu if you want.

One thing that is true -- Ubuntu does have MPI plus some of the common numerical computing libraries -- so should be able to manually configure the cluster -- just boot everything manually and use it like a set of normal workstations, then just run MPI on the nodes.

That would be easy to setup.  What would be a pain would be things like automatic provisioning and cluster reboots, etc.  A lot of the management would be difficult -- no easy way to monitor and kill jobs cluster wide, etc.  When managing a large cluster especially you want uniformity and simplicity -- if your talking about 2-4 workstations than totally manual might be OK.

Rob

---

### Post by rmemm on 2007-11-28
Another thought.  A way you could play with this if you wanted would be with VMWare.  You could setup VMWare to simulate the cluster environment without actually having install things on actual hardware.  You'd need one pretty big machine to do this -- i.e. so you could test multiple machines running on a single piece of hardware.

Just a thought.

Rob

---

### Post by SpacePilot on 2007-12-03
Hello

I don't know if you already have figured out what you are going to use. If you have not, you can try to run Ubuntu with condor clustering software. I administer a condor cluster running on Ubuntu Linux here at a research facility and it is working quite well. You will have to read up a bit, but it is not a big deal.

Good luck

---

