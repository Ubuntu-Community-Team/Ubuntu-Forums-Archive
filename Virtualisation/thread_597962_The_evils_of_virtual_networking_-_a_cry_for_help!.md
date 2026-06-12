---
title: "The evils of virtual networking - a cry for help!"
date: 2007-10-30
forum: Virtualisation
---

### Post by Bobbu on 2007-10-30
Right, I installed VirtualBox on my Gutsy, and manually set up a virtual connection via the good old host interface networking option.  It all worked smoothly.  Until I restarted linux and discovered that my wireless connection had disappeared...

It seems that whenever I make an adjustment to /etc/network/interfaces to put in a bridge for the virtualbox to connect to it removes the wireless interface because it's not to be found in the interfaces file....  Anyone know how I can get my wireless back without reinstalling linux AGAIN, or how to sort out a network with the windows another way? The guest and host can't see each other on the NAT setting.

And now it seems that my virtualbox won't even start the machine because 'VERR_HOSTIF_INIT_FAILED'...  oh, the lament of the newbie linux user trying to set up annoyingly advanced things..


By the way, while I'm here, anyone know why VMware player won't install on i386 machines?  I'm told it's simpler to set up, but it is clearly evil too..

---

