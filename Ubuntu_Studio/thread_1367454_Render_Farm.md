---
title: "Render Farm"
date: 2009-12-29
forum: Ubuntu Studio
---

### Post by dougHines on 2009-12-29
First off, I'm not entirely sure this is the right board for this, but here's my situation and question anyways:

I am brand new to the world of Ubuntu.  I am attempting to create a cluster in which I can do distributed rendering of CGI movies.  My ideal setup is this:

1 controller
X number of diskless render nodes (mobu, ram, power supply, NIC)
1 NAS
 
I have already Ubuntu installed on a machine I am planning to use as a controller.  I also have a node ready to be interfaced with.  Unfortunately that is about all I know how to do.  I believe I am at the point where I need to setup the controller to wake/boot the node(s) over the network and distribute frames for rendering; though I may be wrong.

I have searched the forums but have either a) not come across a post that closely fits my situation, or b) the posts became far too technical and were already closed, preventing me from asking further questions in a post that already exists

On a semi-related note, what kind of cluster am I attempting to create?  I've heard several names thrown around Beowulf, HPC, balanced, etc... but am not entirely sure what this beast's name is.

Thanks in advance,
Doug

PS. I will also be making a image based tutorial on my process (though I'm sure it's similar to most other processes)

---

### Post by bandgeek on 2009-12-29
Most likely you want a render farm

Here's what the terminology means:
HPC- General term for cluster and super computing
Balanced- For ftp or website hosting
Beowulf- Basically you have single really powerful computer 
Render farm- Splits job up and gives each node a part to do.

Here are two websites on render farms they're pretty much the same thing:
[http://helmer.sfe.se/]("http://helmer.sfe.se/")
[http://obscuredclarity.blogspot.com/2008/09/24-core-linux-cluster-in-2999-case-from.html]("http://obscuredclarity.blogspot.com/2008/09/24-core-linux-cluster-in-2999-case-from.html") _Read the comments lots of good stuff in them._

Beowulf:[http://www.beowulf.org/index.html]("http://www.beowulf.org/index.html")

---

### Post by bandgeek on 2009-12-31
You could also use GPU's.
[http://fastra.ua.ac.be/en/index.html]("http://fastra.ua.ac.be/en/index.html")

---

### Post by dougHines on 2010-01-01
I've got the hardware side set.  I'm getting stuck on the OS side.  I am unable to find specific files or I'm configuring files incorrectly.  Again, I'm brand spanking new to Ubuntu and I haven't used Unix in over 4 years.

---

### Post by dougHines on 2010-01-01
I'm using this HOWTO to convert to a diskless system:

[http://developer.novell.com/wiki/index.php/HOWTO:_Convert_Ubuntu_to_Diskless](http://developer.novell.com/wiki/index.php/HOWTO:_Convert_Ubuntu_to_Diskless)

I'm getting stuck at this command
 sudo cp -Rp /etc/mkinitramfs /etc/mkinitramfs-pxe

It seems I don't have mkinitramfs installed at that location and I can't seem to find it anywhere else

---

### Post by bandgeek on 2010-01-04
Just ask your computer
```
whereis mkinitramfs
```

---

### Post by dougHines on 2010-01-05
> **bandgeek said:**
> Just ask your computer
```
whereis mkinitramfs
```


But is there a reason it's not in the /etc/ directory?

---

### Post by dougHines on 2010-01-06
I just found a post on Kerrighed.  Anyone know if this is a viable solution for a render farm setup: where 1 host distributes many frames across many processors?

[https://wiki.ubuntu.com/EasyUbuntuClustering/UbuntuKerrighedClusterGuide](https://wiki.ubuntu.com/EasyUbuntuClustering/UbuntuKerrighedClusterGuide)

---

### Post by alphacrucis2 on 2010-01-07
> **dougHines said:**
> But is there a reason it's not in the /etc/ directory?

Should be under /usr/sbin

/etc is normally for config files rather than binaries.


Edit: I see that mkinitramfs is actually a script rather than a binary but same same.

---

### Post by edwardtuner12 on 2010-08-20
A render farm is a computer cluster built to render computer-generated imagery (CGI),   typically for film and television visual   effects, using off-line batch processing.Visual   effects in movies and television are specifically created by it.for more info google out renderrocket.

---

### Post by jvin248 on 2010-08-30
A couple of options:

A slightly aging distro, but it has some cluster features built in:
[http://dynebolic.org/](http://dynebolic.org/)
[http://dynebolic.org/manual-in-development/dynebolic-x171.en.html](http://dynebolic.org/manual-in-development/dynebolic-x171.en.html)

A parallel cluster
[http://idea.uab.es/mcreel/ParallelKnoppix/](http://idea.uab.es/mcreel/ParallelKnoppix/)
This is really easy to set up and run, boot the LiveCD on the head node and then (mostly) start booting up the cluster machines. I try this out periodically, although their recent move to 64-bit is a struggle as I only have one 64-bit pc and a garage full of 32-bit pcs... Then all you need to do is install Blender/etc on the head node to do the rendering.

A single massive computer
[http://www.kerrighed.org/wiki/index.php/Main_Page](http://www.kerrighed.org/wiki/index.php/Main_Page)
this is what I'd like to build next, but don't have a specific project need.

This may help build a system
[https://wiki.edubuntu.org/EasyUbuntuClustering/UbuntuKerrighedClusterGuide](https://wiki.edubuntu.org/EasyUbuntuClustering/UbuntuKerrighedClusterGuide)
(Edubuntu has always had LTSP, a client-side cluster that allows using a single server to host the OS on and dumb-terminals for all the clients to log in .. this recipe seems to add Kerrighed into the server side, so there is a dynamic cluster on both aspects)

You can subscribe to this thread:
[http://ubuntuforums.org/showthread.php?t=1030849](http://ubuntuforums.org/showthread.php?t=1030849)



I love the Helmer build (listed near the top of the thread, it's easy to find and it's actively being used).  There was also a great little 10 node Beowulf put in a regular plastic tool-box somewhere on the web.

---

