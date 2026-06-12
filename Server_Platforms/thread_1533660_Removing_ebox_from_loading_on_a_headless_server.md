---
title: "Removing ebox from loading on a headless server"
date: 2010-07-18
forum: Server Platforms
---

### Post by matthewboh on 2010-07-18
Okay - I've done something and I can't get it back.

I upgraded my Ubuntu 8.04 LTS server to 10.04 LTS - rebooted and things ran good.  I knew I had a few problems, but DHCP and DNS were booting up and working fine for me.

I went to take a look at Webmin, but apparently that's been removed from support for Ubuntu 10.04 - so I thought, I'll use eBox.  I realized that Ebox didn't have the network module turned on, so I tried to turn it on.  I found out the installation was missing scriptaculous, so I got that and installed that and then turned on the network module.

I then rebooted the machine - and now nothing.  It hangs when I get to the load for Apache.  

I would like to disable the network module for eBox, but can't find documentation for how to do that from the command line - which I have to use because the damn box won't boot and I'm running from a Live CD.

ARRRRRRRR!  Someone please help!

In the meantime, I'm going to try renaming the network module conf name in /etc/ebox and see if that does anything....

---

### Post by naelq on 2010-07-18
hi,
eBox for 10.04 is still beta, though for home/basic usage might be fine.
anyway, to disable an eBox module, issue:
```
#sudo /etc/init.d/ebox 'module_name' stop
```
which is in your case:
```
#sudo /etc/init.d/ebox network stop
```

maybe you should take a look @ the logs in */var/log/ebox..* & try to understand what's causing the problem



nael

---

### Post by matthewboh on 2010-07-18
Thanks - but my problem is that it won't even boot all the way.  Right now, I'm accessing the box with a Live CD, so I need to be able to prevent ebox from loading at all.

How would I do that?

---

### Post by naelq on 2010-07-18
ohh!!

option 1:
nuke it!
> chroot into system
> remove it from the system:
```
#sudo apt-get -V purge ebox
```

option 2:
> chroot into system
> use the following to prevent it from auto start:
```
#sudo update-rc.d -f ebox remove
```



nael

---

### Post by matthewboh on 2010-07-18
Did that!  Thanks - but I went one step too far.

apt-get was complaining that I had all these other programs, and I should run apt-get autoremove - well that removed WAAAY too much stuff.

I would like to slap the ebox people silly....

---

