---
title: "Nbie wondering if I have things set right due to slow reaction"
date: 2014-01-19
forum: Virtualisation
---

### Post by shearer4 on 2014-01-19
Hello:
I just installed several VM's with intances of Ubuntu 12.04, 13.10 and XBuntu. 

I have; A MacPro1.1. with 2 Xeon 2.66 cores, 16 gigs of Ram, and I am using VIrtualBox 4.3.6 lastest  build

I have assinged 3gigs of memory to Salamander and 128 MB of video memory.  Still, it seems much more sluggish than Ubuntu 12.04, and of course XBuntu is much snappier as I would expect. 

Any advice on how I have this set up and or how to speed up reaction time on Ubuntu in general and Salamander in particular. 

Please excuse any uncool terminlology, as I am just beginning to mess around with. 

Thanks AShearer

---

### Post by TheFu on 2014-01-19
Follow these instructions: [http://blog.jdpfu.com/2012/09/14/solution-for-slow-ubuntu-in-virtualbox](http://blog.jdpfu.com/2012/09/14/solution-for-slow-ubuntu-in-virtualbox)

---

### Post by shearer4 on 2014-01-19
Thanks;  I read through all your instructions. Believe it or not, as a newbie, I've already figured out some of this, looking to improve speed. I'm new to Linux, but not OS's or virtualization. I've run Windows on my Mac for several years now.  I need to go through and review. But; what I wonder is, now that I have installed is there a way to change the type of VDisk from dynamic to fixed?  I don't recall that option anywhere in VBox?   Very helpful link; thanks again.

---

### Post by TheFu on 2014-01-20
There is not an 'easy way' to convert from dynamic to fully-allocated storage, but there are steps to do it, just like you'd do for any other cloning process or backup software.  This is one of those things where typing the instructions is 1000x harder than doing it - mainly because there are unknowns.  An overview of the process is:
* create another vHDD inside the VM - fully-allocated and sized appropriately
* connect a liveCD ISO to the CDrom device and boot.
* Using any data cloning utility, mirror the entire HDD device from vda to vdb (I don't know the exact device names/numbers under virtualbox). Tools that do this include dd, ddrescue, gparted, partimg. We are looking for bit-for-bit copy tools, not something that works at the file system level.
* shutdown the LiveCD OS
* Inside the VM settings of VBox, remove the "original" vHDD - so only the new vHDD remains
* Boot the VM - it should come right up, with all the old files under the new fully-preallocated vHDD.

Simple.  

Thinking about it a little, there might be a way to have vboxmanage to clone the VDI file into a non-sparse allocation. RTFM for that. The virtualbox website has fairly detailed documentation for cloning a vHDD using **vboxmanage clone**. You can read up on it as well as I can. ;)

---

### Post by shearer4 on 2014-01-20
Thanks for the detailed explanation. I am saving this to go off and try it once I get back to my main system.  Wonderful help.  BTW: I did read the VBox manual. At least as far as I can tell it only describes cloning an already existing VM to another location/Volume/etc..  This would have the same settings. At least in 4.3.6 there is a Clone option on the GUI of Vbox.  Also;  I'm not sure how cloning within Ubuntu would actually work. Seems like I can't get access to the VDisk on the Host.  Maybe clone on the Host?  I have already successfully moved my VM's by cloning to another drive I had in the system and "adding" a new machine using Vbox, but all this does is pick up the original settings.  Running Mac, maybe I could use like CCC and clone the disk image to the other drive, then follow as you mention above.  

Once again, thank you.  Working on it.

---

### Post by oldos2er on 2014-01-21
Moved to Virtualisation.

---

