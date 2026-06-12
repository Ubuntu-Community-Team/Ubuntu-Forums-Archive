---
title: "Virtualbox-error in suplibosinit"
date: 2010-06-24
forum: Virtualisation
---

### Post by pombe on 2010-06-24
Hi all, I'm having a small issue running a Windows XP guest in a Ubuntu 10.04 host OS.  Following a restart of the computer I always get this message when trying to start XP.

```
Virtualbox-error in suplibosinit

Kernel driver not installed (rc-=1980)

The VirtualBox Linux kernel driver (vboxdrv) is either not loaded or there is a permission problem with /dev/vboxdrv. Please reinstall the kernel module by executing

'/etc/init.d/vboxdrv setup'

as root. Users of Ubuntu, Fedora or Mandriva should install the DKMS package first. This package keeps track of Linux kernel changes and recompiles the vboxdrv kernel module if necessary.
```

Running the "/etc/init.d/vboxdrv setup" does fix the issue, but I have no idea why this module should need re-installing each time...

Any ideas?

Thanks

---

### Post by pombe on 2010-06-30
Bump.

Anyone?

---

### Post by 88300D on 2010-07-13
Hi i am a newb this is my first post. This wont help you but i have the exact same problem. This linux thing sucks me in every couple of years. after i get on top of this i will have samba to deal with and then i reckon i will have a usable item. messed around for ever last couple of days trying to load some windows media player codecs for a guy who liked a particular radio station. Im not quite sure what i did that worked but reckon i may be able to do it again LOL. when i learn something i will post agian. Peace and blessings Howie

---

### Post by 88300D on 2010-07-16
well best i can work out is, i blew my setup away and started from scratch, same issue. so its not my wrong doing. removed latest version and installed earlier one that came with the distro (ps i am also now running KDE, kubuntu) it works fine but of course i get no USB.

They have a closed version but i cant work out how to buy it, i have even rang and been shuffled through many people to finally get a message machine.

Next solution for me will have to be give money to a different VM software distributer, I used to use VM ware and liked it very much and have been recommended parallels dont see any other option Vitual box does not work (why donate) and they dont want to sell so throw the doe at some one who cares.

I did like their product but oh well.

Peace and blessings Howie,

PS what are you using for disk imaging? we use acronis for our windows pcs but it wants to write linux partitions sector by sector and takes way too long. i even shrunk the partition to <5gig and next morning it said it had 2 days to go.

---

### Post by siabost on 2010-07-16
pombe,

I had the exact same problem in Fedora 13.

I removed the package I had installed via Synaptic and installed the relevant package direct from the Virtualbox website, and all was fine.

[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

Or you could add the relevant repository & key which might be better (on same page).

Good luck :D

---

