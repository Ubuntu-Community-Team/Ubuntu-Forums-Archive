---
title: "Problem setting up VirtualBox"
date: 2007-12-07
forum: Virtualisation
---

### Post by oneadvent on 2007-12-07
I get this when I try and set up VirtualBox. I am not sure what I did wrong. I have 7.10 with all upgrades. I should have the right kernel then right?


```

VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Please install the virtualbox-ose-modules package for your kernel and execute '/etc/init.d/vboxdrv start' as root.
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}


```

confused, thanks for any help.

Josh

---

### Post by oneadvent on 2007-12-08
Ok, I got it.

First I had to start the Virtual drivers by 
```

sudo /etc/init.d/vboxdrv start

```

Then I added myself to the group vboxdrv

That worked like a charm.

I hope this helps someone else.

---

### Post by zeller on 2007-12-09
> **oneadvent said:**
> Ok, I got it.

First I had to start the Virtual drivers by 
```

sudo /etc/init.d/vboxdrv start

```

Then I added myself to the group vboxdrv <-----

That worked like a charm.

I hope this helps someone else.

How do you do that?

---

### Post by oneadvent on 2007-12-09
Went to system-->administration-->users and groups

I then went to the manage groups for my user, and scrolled down to vboxusers.

All you have to do is check mark your user id, and then I believe you have to restart gnome.

Let me know if you have any problems.

---

### Post by phonicboom on 2008-04-08
**virtualbox 1980 error linux mint FIX :D**


_____

[I]VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Please install the virtualbox-ose-modules package for your kernel and execute '/etc/init.d/vboxdrv start' as root.
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).

or similar error....[/I]
_____
[B]
I did not find an answer specific to Mint so here it is.....[/B]

System menu (daryna in my case) > Administration > Users and groups (enter root password) > select your name > Properties > advanced > change 'main group' to vboxusers

restart your system

bingo :D

---

### Post by marli2 on 2008-11-02
I still have this problem, ive done what you suggested also i get " No suitable module for running kernel found" when i try the Terminal commands

---

### Post by oneadvent on 2008-11-02
have you installed virtualbox-ose-modules?

If so can you post the command that you are using and the exact error that pops out?

thanks!

---

### Post by cabletie on 2009-08-26
Installed VirtualBox from the Ubuntu repository.

Got the "no suitable module for running kernel found" and "VirtualBox kernel driver not installed." errors.

Followed instructions to run "sudo /etc/init.d/vboxdrv setup" and the machine's response is that 'setup' isn't one of the commands that can be used with vboxdrv. Tried reinstalling, and a number of other cryptic commands that people have offered to try and fix it.

I finally uninstalled it and downloaded a .deb from the official Sun VirtualBox site:


[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

I grabbed the Ubuntu-appropriate one for my machine, and it installed cleanly.

Tried to start my VM, and lo and behold, it worked!
Thanks to all who have offered solutions, but I recommend downloading from the Sun site.

---

### Post by tenghoward on 2009-08-26
Try to install dkms from Ubuntu repos. Next time when you install/upgrade virtualbox or linux kernel it should automatically compile and install virtualbox kernel.

I highly recommend you install VirtualBox using Sun's release, not Ubuntu repos. OSE edition comes with limited function (USB is a major one).

Make sure you put your name in vboxuser from User & Group.

---

### Post by pornee on 2009-08-28
when i try to log in it gives me an error
Connecting to 'localhost:20012'...
vbox: can't connect to 'localhost:20012'.

---

### Post by seuzo on 2009-08-28
i install dkms. virtualbox not working. And all add user name in vboxuser.

after that
I uninstall virtualbox and install again
And it works! hehe thank guys

---

