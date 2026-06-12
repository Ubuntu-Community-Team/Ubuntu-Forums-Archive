---
title: "How would this be for Virtualization?"
date: 2010-09-30
forum: Virtualisation
---

### Post by steev182 on 2010-09-30
I'm trying to price up a box for under £200 to run as a Linux PC which also has a couple of servers for me to please my inner geek. I have another computer running OSX (a hackintosh) which I want to keep that way (and virtualization runs dog slow on it...)

I noticed this bundle during the week:

AMD Athlon 2 x4 640
ASUS M4A78LT-MLE motherboard
2GB DDR3 RAM

For £150, this with the 1TB drive I have (which could be wiped and used for Ubuntu) and a £30 case, I could have something quite nice.

Does this sound ok for virtualizing a few servers though?

---

### Post by TJet1.8 on 2010-09-30
Sure...sounds good except that you may not be able to run too many servers with only 2GB of RAM in your host pc.

You need to figure that ubuntu requires about 400-500MB of RAM (depending what you install) which leaves you with 1.5GB of free RAM left to run your VM's.

If each of your VM Servers are assigned ~500MB of RAM....you can only run 3 VM Servers efficiently.

If you assign more RAM to them...your host will start swapping memory to disk which slows everything down.

My "smallest" host pc has 4GB of RAM.
The last PC host I built about a year ago has 8GB of RAM.
My new PC host will have at least 12-16GB of RAM.

The more RAM...the more VM's you can run efficiently.

It all depends on what you want to run in your VM's and how much memory the guest OS needs.

Hope this helps...good luck.

:popcorn:

---

### Post by steev182 on 2010-10-01
Yeah, I know that's going to be a sticking point. But I'll be able to get £100 worth of RAM next month. To have a host like that in my closet or under my bed (or even in the utility room) would be pretty awesome.

---

### Post by sikander3786 on 2010-10-01
> Sure...sounds good except that you may not be able to run too many servers with only 2GB of RAM in your host pc.

+1

My only worry is 2GB RAM. As you said you will get some RAM in coming days, all other hardware seems pretty nice.

---

### Post by dpj23 on 2010-10-01
I would recommend > 4GB of memory for virtualization projects.  You will be able to run virtual machines with 2GB of memory.... An example would be 1GB for the virtual machine and 1GB for the host machine...  When it comes to virtualization the more memory you have the better things will run...

---

### Post by ihatecomputers on 2010-10-04
It depends on what you are planning on doing.  With 2gb of RAM in the host you could probably get a couple of Ubuntu Servers or a couple of XP machines running with 512mb of RAM.  If you're only playing with one or two machines at a time, this would be fine.  I used to have a similar setup with a quad core machine with 2gb of RAM that ran a couple of XP VMs with 512mb of RAM and they worked fine for what they did.  I used them to virtualize the machines that are used for P2P networks.  As long as I only used them for their specific purpose, they were fine.

Anything after that you'll want more RAM.

---

