---
title: "jaunty server performance"
date: 2009-10-04
forum: Server Platforms
---

### Post by Lekar on 2009-10-04
I'm looking to pull some performance out of a 1.5-3GHz jaunty servers... The workload would be generating some memory/cpu intense hashes. Can anyone recommend a good guide to sever performance?

---

### Post by Lars Noodén on 2009-10-04
What services are you running on the 'server' ?
Which ones are most important?

---

### Post by Lekar on 2009-10-04
its going to be an mpi program, and that is what is most important.. I don't really care about any other services.. i'm going to be researching putting ubuntu all into memory at some point.

---

### Post by Lars Noodén on 2009-10-04
Well, general tips are to install only the bare minimum.  
That includes looking in /etc/init.d/ for services you do not use and turn them off.  If you really end up not needing them, they can be uninstalled.

I'm not sure of the context of 'mpi' but find out what it needs to run and take out everything else.  Give more specific information about your task and more specific suggestions can be provided. 

Here's one long document on the topic:
[http://www.redbooks.ibm.com/redpapers/pdfs/redp4285.pdf](http://www.redbooks.ibm.com/redpapers/pdfs/redp4285.pdf)

If you want the whole system in RAM then you probably don't want Ubuntu but want BusyBox instead. 

 [http://packages.ubuntu.com/jaunty/busybox](http://packages.ubuntu.com/jaunty/busybox)
 [http://www.busybox.net/](http://www.busybox.net/)

---

### Post by Lars Noodén on 2009-10-04
If you don't use busybox, you can experiment with removing as many modules as possible from the kernel.  It will be messy.

---

### Post by Lekar on 2009-10-04
ok, i'll look into this. Thank you for the info.

---

### Post by Lars Noodén on 2009-10-04
1) I've had time to remember a few items that might help.  One are old notes on building kernel packages with custom kernels:
 [http://www-personal.umich.edu/~lars/kernel_patching.html](http://www-personal.umich.edu/~lars/kernel_patching.html)

If you do tune the kernel, it is best to work using the package manager so that changes can be undone.  

2) With RAM, my thoughts jumped to busybox but maybe you meant tmpfs.  
 [http://www.thegeekstuff.com/2008/11/overview-of-ramfs-and-tmpfs-on-linux/](http://www.thegeekstuff.com/2008/11/overview-of-ramfs-and-tmpfs-on-linux/)

/dev, /proc, /var, /tmp and /home need to be rw, some or all *could* be mounted in ramfs, if you have the space.  
See also [hier(7)](http://linux.die.net/man/7/hier)

Maybe with swap, if you have two drives, you could mount swap in a RAID0 array.  Or if you have lots of RAM and are willing to go without a helmet and seatbelt, turn off swap...

There is other filesystem tuning that can be done, but if your activity is CPU intensive, then that may not matter as much.

---

### Post by Lekar on 2009-10-04
The tmpfs and ramfs seems like a good choice. I have a gig or more in each  of the systems.. I'm thinking about disabling swap, but I will have to see what i can do with the remainder of ram if i load some parts into a tmpfs or ramfs .. I just might not have enough ram to do what i want. I will have to experiment further. 

I'm going to first start playing with it in a vm.. so I'm not to worried about undoing changes, but thanks for the heads up. This might be a route i end up taking. 

Thank you for you input.

---

### Post by cholericfun on 2009-10-07
as an alternative to messing around with kernels and such
heres a prebuild one that does what you want (i think)

[http://idea.uab.es/mcreel/ParallelKnoppix/](http://idea.uab.es/mcreel/ParallelKnoppix/)

---

