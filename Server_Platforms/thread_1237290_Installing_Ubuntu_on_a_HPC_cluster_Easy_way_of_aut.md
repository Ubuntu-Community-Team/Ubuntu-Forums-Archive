---
title: "Installing Ubuntu on a HPC cluster: Easy way of automating it? (preseeding help plz!)"
date: 2009-08-11
forum: Server Platforms
---

### Post by TehDooMCat on 2009-08-11
**Never mind, I figured out how to do it. Needed to add auto=true priority=critical interface=auto after the --.**

I've installed Ubuntu on one of the nodes of a 20-blade HP cluster. Since all the blades are running the same hardware, I was wondering whether there was an easy way to automate the install for all of them? As in, pop the CD in and have all the install questions answered for you...

So I looked at using [preseed files](https://help.ubuntu.com/9.04/installation-guide/i386/preseed-using.html), but it doesn't seem to be using them. On the Ubuntu boot selection screen, I've tried prefixing/appending/replacing 'file=.../ubuntu.seed' with ```
url=http://192.168.212.19/preseed.cfg
``` and ```
auto=http://192.168.212.19/preseed.cfg
```
to the kernel args, but it seems to completely ignore them.

Does preseeding from a file over HTTP only work on Netbooted installs? Because all the blades are connected to a DHCP server and they can see each other on the network. 192.168.212.19 is the server already up, running thttpd. I've checked I can see it on the network, and preseed.cfg is world-viewable, so I'm guessing it's a problem on the installer side.

How can I get the preseed file to work? I don't fancy going through the whole setup process with 20 more blades :P

Either that, or, is there another easy way to get it automated?

---

