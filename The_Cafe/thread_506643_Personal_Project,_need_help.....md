---
title: "Personal Project, need help...."
date: 2007-07-21
forum: The Cafe
---

### Post by Turboaaa2001 on 2007-07-21
Ok, heres the thing. I have a lot of computers laying around that, at the moment, are used for parts and what-not. I will be moving in the near future hopefully to a house instead of an apartment. There I plan on using the higher power output to run all my machines. (Right now I keep tripping the breaker.)

I participate in distributed computing projects via BOINC software and have done so for years. However, now I would like to make my own project so I can use all this power laying around. I would prefer to create a cluster that would run a single virtual machine that could take advantage of these machines as 1 "super computer".


Here is what I want:

Scalable cluster that uses ANY mixture of processors, can re-work itself if a machine dies, and can be managed from a single interface once setup.

I need to know what would be the best way of going about this with the hardware and software. I also need some ideas of projects that would be practical or just neat. i.e. Creating an AI program that will play any computer game starting with basic Super Mario Bros then going up to Doom and beyond. Sadly I don't know how to program so I would need others to help with that.

Can you help me?

EDIT:

Here is the URL to my BOINC stats page: [http://boincstats.com/stats/boinc_user_graph.php?pr=bo&id=1144891](http://boincstats.com/stats/boinc_user_graph.php?pr=bo&id=1144891)

---

### Post by aktiwers on 2007-07-21
This reminds me of an old post I made here a year or 1½ ago.
Funny thing is, I just found it!
[http://ubuntuforums.org/showthread.php?t=157676](http://ubuntuforums.org/showthread.php?t=157676)

Maybe you will find some useful links there.

Good luck with the project, sounds awesome! :)

---

### Post by Turboaaa2001 on 2007-07-22
Hey thanks. One of those links also gave me some ideas for uses for the cluster.

I still like the idea of developing a AI that will play video games as the user. The idea of eventually getting the AI to the point of recognizing the limitations (i.e. gravity, walls, ammo, etc) would be awesome. When you play a game like F.E.A.R. the enemy AI only uses 1 or 2 weapons, never run out of ammo and does not realize that they are in need of health/help.

Anyway, I appreciate the links. When I move I'm going to put the stuff together, then I'll setup several VLANs and let people use it over the net until I can get something better into the mix.

Does anyone else have any ideas?

---

### Post by bread eyes on 2007-07-22
[http://en.wikipedia.org/wiki/Linux_Virtual_Server](http://en.wikipedia.org/wiki/Linux_Virtual_Server)
[http://en.wikipedia.org/wiki/OpenMosix](http://en.wikipedia.org/wiki/OpenMosix) (...)
[http://en.wikipedia.org/wiki/Rocks_Cluster_Distribution](http://en.wikipedia.org/wiki/Rocks_Cluster_Distribution)

---

### Post by tutomlin on 2007-08-10
Other links to check out:

for a HPC cluster build:
[https://wiki.ubuntu.com/MpichCluster](https://wiki.ubuntu.com/MpichCluster)
but you'll need to write all your own parallel code to use it (it's pretty hard to do correctly)

an alternative to OpenMosix:
[http://www.kerrighed.org/wiki/index.php/Main_Page](http://www.kerrighed.org/wiki/index.php/Main_Page)
I'd probably try to use this instead of OpenMosix, since kerighed is good on 2.6 kernels, and 64 bit kernels, while OpenMosix is not.  In theory Kerrighed should also be good on SMP systems any day now.(that's what I'm waitin on)

As for ideas:  I've been pondering setting up a HPC cluster to run large FEA(Finite Element Analysis) simulations on data pulled from 3D medical image scans.  At the moment I'm still working on getting the data from the medical imaging into the right format for FEA processing.  After that I'll need to write(or find) a parallelized FEA solver (will test on my SMP desktop first probably).  At that point I'll  look to get a cluster running.

Cheers

Tucker

---

