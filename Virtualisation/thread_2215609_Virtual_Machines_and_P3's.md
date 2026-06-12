---
title: "Virtual Machines and P3's"
date: 2014-04-07
forum: Virtualisation
---

### Post by ibjsb4 on 2014-04-07
I'm thinking about going totally retro and setting up a box with multiple PIII processors.  Such boxes were built with the Xeon processor.  I could get a two core @1.13Ghz per core or up, maybe a 4 core.  These machines had a 400hz front bus, but plenty of ram capability.


What I would like to know is if anyone has ever ran vBox or other on such a machine?  Not having a VM would be a deal breaker on this project as this machine would be my test box.

---

### Post by TheFu on 2014-04-07
Slow is slow. It will be painful.  Plus a PIII will not support VT-x, which means it CANNOT run other virtualization systems like KVM or Xen - when you graduate.

Heck - a $200 chromebook has VT-x and is faster than some Core i5s from a few yrs ago. The only issue is lack of RAM in my C720. It is soldered to the MB.

---

### Post by tgalati4 on 2014-04-07
I don't understand the question.  Were the Xeon processors removed and you want to replace them with PIII's?

Depending on your location, a craigslist search will turn up multiple, used server's.  As businesses consolidate their racks or move to the cloud, a lot of single-rack servers are freed up for new life.

There is quite a performance difference between a Xeon and a PIII.  For VM's I would only use Xeon's because of the larger cache, faster internal memory bus, and a host of other server-specific features.

I bought a couple of Dell PowerEdge 1750's ($300 each a few years ago).  They are dual Xeon 2-core (one was 2.4 GHz, the other 2.6 GHz).  That's 4 cores per machine.  Certainly shy by today's standards, but they run xen just fine and multiple vm's.  They are 32-bit, so that may be a limitation if you have very large datasets or if you need other 64-bit performance features.

I read a study by Dell that the 1750's can handle ~14 vm's and the newer 1950's can handle ~20 vm's.  The 1750's run 200 to 240 watts depending on load.  Dell claims the 1950's run 25% less power, but I don't have those units to compare.  

I think if you did a head-to-head comparison, the Xeon's will blow the doors of PIII's for server and vm workloads.  I have a couple of PIII desktops running older distos and they are pretty darn slow for anything other than file serving.  I would  not think of running any vm's on it.

A Los Angeles craigslist search: $300

Used DELL Poweredge 1950 1U server in excellent condition. I also have lots of used Cisco gear if you want to start a network or lab.

Server specs:
2x Dual Core 1.86GHz CPU
3x 36GB 2.5" SAS drives
2x Power Supply
4GB RAM
No OS installed

Comes with front bezel. Pulled from working environment. I would trade for a DELL Poweredge 2900 III server. No scams, no low ballers. Text or email me at 213-.

---

### Post by TheFu on 2014-04-07
In a home environment, "servers" are usually too noisy and make too much heat.  A $400 3rd-gen Core i5 system with 16-32G of RAM can to some unbelievable things.   I run 8 VMs on a Intel(R) Core(TM)2 CPU  X6800  @ 2.93GHz with 8G of RAM.  Just starting to add some load on a Core i7 - expect to get 16+ VMs on that since it is about 2x faster.  Together, these machines with spinning HDDs draw less than 200W total - and that includes the network equipment, KVM, power too.  Not the monitors. ;)

Any MB that supports a PIII probably only supports 4G of RAM - that will be an issue.

The Dell 2950s ARE great machines. Deployed a few for clients when they first came out - saved lots of power costs, but they are still noisy, IMHO.

---

### Post by ibjsb4 on 2014-04-07
> Slow is slow. It will be painful. Plus a PIII will not support VT-x, which means it CANNOT run other virtualization systems like KVM or Xen - when you graduate.

Yes this is what I fear, slow.  And this is not about being able to graduate to KVM or others, I'm perfectly happy with vBox.  My vBox (guest) are very bare systems and I usually just have one VM running.  I am wondering if anyone has or had a P3 multi processor box running virtual software.


Also found out I was mistaken about the bus speed, its only 100MHz.  L2 cache 1 or 2 meg per processor.  Up to 8 processors @900GHz clock. 


These are servers, you can dump as much gig's of ram into them as you wish.


And yes they are noisy, mine will end up in the closet.  This will not be my first server setup, last one was a IBM x235.  A dual processor box that ran vBox just fine.  Its just I want to try this with P3 technology, if its even possible.


@tgalati4 .. Hi
I hope the above better explaines what I want to do.  I think the 100MHz front side bus will be too weak  :(

---

### Post by kostkon on 2014-04-07
+1

It's going to be terribly slow.

---

### Post by TheFu on 2014-04-08
I tried to use vbox on Mom's old P4 - painful doesn't describe it.  It was slower than running a complex X/Windows application over a 9600 baud modem while being hacked from overseas.

---

### Post by ibjsb4 on 2014-04-08
The way I see it:


Up to 8 processors is good enough for vBox ( this could also be used as a winter room warmer :) )


1 or 2 meg of l2 is good enough


Ram is not a problem


FSB of 100MHz is too slow to share unless there is some sort of bus magic going on between the processors.  The weak link :(

---

