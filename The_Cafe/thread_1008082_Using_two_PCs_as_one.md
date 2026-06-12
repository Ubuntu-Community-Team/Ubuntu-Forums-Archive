---
title: "Using two PCs as one?"
date: 2008-12-11
forum: The Cafe
---

### Post by MadeR on 2008-12-11
Does anybody know if there is a programme that, using an ethernet connection, lets me connect two pc (well I am thinking to my two laptops) to share the screens and computing power?

With "share the screens" I mean like both monitors are connected to the same graphic card.

thnak you

---

### Post by windhair on 2008-12-11
I would say, it is not tht easy, since there are not screen plugout for a laptop, what I suggest is using [VNC]("http://www.realvnc.com/"), with which you can access the other desktop easily. 
About the power, there is no way to share.

---

### Post by renzokuken on 2008-12-11
you mean a **cluster**?

[http://en.wikipedia.org/wiki/Cluster_(computing](http://en.wikipedia.org/wiki/Cluster_(computing))

very possible using linux, there are even distros designed specifically for this.

---

### Post by Chris_B on 2008-12-11
You could run them both individually using a KVM switch also?

---

### Post by MadeR on 2008-12-11
> **renzokuken said:**
> you mean a **cluster**?

[http://en.wikipedia.org/wiki/Cluster_(computing](http://en.wikipedia.org/wiki/Cluster_(computing))

very possible using linux, there are even distros designed specifically for this.

A cluster fits the descrition for sharing computing power, but not the screens.

Let's say a cluster, and one Xserver should be "linked" to both monitors.

---

### Post by wishyjr on 2008-12-11
this might not be what you're after but i think you'll find it interesting considering your original post:

[HTML]http://synergy2.sourceforge.net/[/HTML]

---

### Post by derekr44 on 2008-12-11
Oh I think I'm going to give Synergy a try :)

---

### Post by semitone36 on 2008-12-11
I heard about synergy on digg a few months ago.  Post back here if it works out for you.  I havent had the chance to test it yet

---

### Post by vrangforestillinger on 2008-12-11
For cluster computing, check out [open-mpi]("http://www.open-mpi.org/"). Its a framework that allows a program to run in parallel on many computers connected on a network. The bad news is that you need to rewrite any programs you want to run on this framework. This [Department of Mathematics]("http://wiki.math.ntnu.no/drift/stud/parallel_computing") use the MPI-framework on their student computer labs (running Ubuntu).

---

### Post by klange on 2008-12-11
(Sorry to the OP, as my post won't really help you directly...)

Two machines, one graphical output is entirely possible (ignoring clustering for a moment...). Remember that X is a server/client system. With the proper facilities in place, you can make your secondary system use your local system's X server (and force it as a default). It would probably be best not to run a DE on the second machine, and to make sure that all the required QoS provisions are in place to handle the massive network load you'll have. But, regardless, this would be horribly inefficient and pointless when we throw clustering into the mix. You need only run your X server on one machine (with all of its own screens) and let it leech significantly off of the clustered machine.

Now, completely ignoring almost everything the OP said: If you have two distinct machines that you want to "act as one", Synergy is your best bet for input handling, and you can use a system like xmove (with some extra scripting to handle physically dragging a window from one screen to the other) to give you more control of window management.

---

### Post by UbuWu on 2008-12-11
If you want to use synergy, install [Quicksynergy]("apt:quicksynergy"), it will make your life a whole lot easier.

---

