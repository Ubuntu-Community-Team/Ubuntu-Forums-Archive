---
title: "Quadrowulf: Finally Posted!"
date: 2008-08-29
forum: The Cafe
---

### Post by h0ax on 2008-08-29
I finished posting the instructions // pictures for a neat Quad-node, quad-core compact Beowulf cluster I created. [IMG]http://i.slickdeals.net/images/smilies/emot-bounce.gif[/IMG] 

[CENTER][IMG]http://lh4.ggpht.com/humanumbrella/SJiZHyoIRSI/AAAAAAAAAzQ/8fMz6QDO9Vc/s288/Quadrowulf%20183.jpg[/IMG]
[/CENTER]

Just thought you guys/gals might think it's interesting! [IMG]http://i.slickdeals.net/images/smilies/emot-eek.gif[/IMG] 

I had a blast doing it!  (::guitar:

[http://www.humanumbrella.com/quadrowulf/]("http://slickdeals.net/?sduid=122262&sdtid=909089&sdfid=7&u2=http://www.humanumbrella.com/quadrowulf/")

Let me know if you have any questions / comments !! (:

Cheers!
--Justin

---

### Post by ugm6hr on 2008-08-29
Moved to Cafe - not a support query or complete Tutorial.

---

### Post by Hire on 2008-08-29
Omfg

---

### Post by h0ax on 2008-08-29
Sorry about posting in the wrong place!  Let me know if anyone has any questions -- I will try to answer.

Look what you can do with Ubuntu!! (:

---

### Post by uid313 on 2008-08-29
Why 4 graphics cards and so many network cards?

---

### Post by kpkeerthi on 2008-08-29
OMG! Do you mind posting the output of **cat /proc/cpuinfo** ? LOL!

---

### Post by regomodo on 2008-08-29
#

---

### Post by h0ax on 2008-08-29
> **uid313 said:**
> Why 4 graphics cards and so many network cards?

The graphics cards were cheap (I think $15/ea) for debugging / setup purposes.  I didn't want to have to move the graphics card around while I was setting up the nodes.  Each node is set to 3.2GHz over-clocked from 2.4GHz, so I needed visual information on each node.

The network card is to minimize latency of communication between nodes.  We are assuming here that each core of the quad core is like it's own "machine".  Thereby, there will be contention for the networking traffic.  If we designate a network card for each processor, or if we channel bond all 4 so that it appears as one, we can create somewhat of a "load balance" for network traffic.

Hope that clears it up! (:

---

### Post by h0ax on 2008-08-29
> **regomodo said:**
> Creating a custom beowulf cluster is something i've always wanted to do.

So do it! (:

Sure, you don't have to use a quad core setup (even though this entire setup cost <$3,000) -- just get some old machines.  Like the ones that used to be used in businesses, go to garage sales.  It can be done if you want, and I highly recommend it !(:

---

