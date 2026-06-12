---
title: "Successful migration to 14.04 ..."
date: 2014-04-24
forum: Ubuntu, Linux and OS Chat
---

### Post by cwmoser on 2014-04-24
After a little work I think I have successfully migrated Ubuntu AMD-64bit 12.04 to 14.04.

I note that 14.04's root foot print is much smaller:
12.04 used 13GB while my new 14.04 uses 6.1GB.

I have my boot hard drive setup with two root partitions - one for my daily use and the other
for the next distribution of Ubuntu, and my /home in a third partition.
I have:
/dev/sda1    15GB    /  for 14.04
/dev/sda2     8GB    Swap
/dev/sda3    80GB    /home
/dev/sda4    15GB    /  for 12.04

I have quite a number of applications loaded:  VirtualBox, Monodevelop, X10 controls,
Stellarium, Shutter, Samba, Compiz, Gnome desktop, Scummvm, DOSBOX, and on and on.
Took some time to install and configure the way I wanted along with some research on how
to do various configurations.


What I really like about Ubuntu 14.04 is the way Places -> Network works now - much better than 12.04

What I don't like is the way windows maximize automatically when you move them to the top - got to
find out how to disable that.

I do think that 14.04 was the easiest to migrate of all the prior Ubuntu distributions I have done.

I know over the next few weeks more tweaks and updates will be sent out.
So far looks like a winner distro.

Carl

---

### Post by Frogs Hair on 2014-04-24
***Moved to Ubuntu Linux and OS Chat***

---

### Post by 3rdalbum on 2014-04-25
> **cwmoser said:**
> 
What I don't like is the way windows maximize automatically when you move them to the top - got to
find out how to disable that.

Ubuntu 12.04 definitely did that too. You must have disabled it some time in the last two years.

You can disable it again in Compizconfig-settings-manager.

But yes, 14.04 is excellent. Been running it on my netbook for a month or so, just upgraded my desktop. Apart from nouveau drivers crashing (which, unfortunately, is nothing new) and forcing me to install the Nvidia proprietary driver, I'm absolutely at home with 14.04. Love it.

---

### Post by cwmoser on 2014-04-25
I looked all through CCSM and can't find how to disable that automatically maximizing window feature.

Re Nvidia, I am running with nvidia-current drivers.  On initial install my desktop would freeze - had to go through
Recovery and **sudo apt-get remove nvidia*** and then **sudo apt-get install nvidia-current**

Somehow I sense some minor delays in responsiveness with some Compiz actions - setting in CCSM or Nvidia driver I'm using?

---

### Post by coffeecat on 2014-04-25
> **cwmoser said:**
> I looked all through CCSM and can't find how to disable that automatically maximizing window feature.

Although this isn't a support thread, I'll tell you that one for free. If only because it ticks me off as well. :) I like to decide when I want a window maximised.

CCSM -> Windows Management -> Grid ->  Corners/Edges tab -> Top Edge -> Change dropdown to None.

---

### Post by cwmoser on 2014-04-25
CoffeeCat, thanks for the freebie.
It was an irritating feature.

---

