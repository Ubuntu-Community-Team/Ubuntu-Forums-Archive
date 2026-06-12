---
title: "Problem with compiling kernal for VirtualBox..."
date: 2009-03-06
forum: Virtualisation
---

### Post by Chaosleet on 2009-03-06
I tried to install VirtualBox today using the Synaptic Package Manager and the repo from their download page, and it installed fine but when it tried to compile the kernal I got this error:

```
VirtualBox will not start until this problem is fixed. Please consult /var/log/vbox-install.log to find out why the kernel module does not compile. Most probably the kernel sources were not found. Install them (the package name is probably linux-headers-<version> whereby <version> can be determined by 'uname -r') and execute

  /etc/init.d/vboxdrv setup

as root.
```

After checking what kernal I have, I got this:
```
2.6.28.1-xxxx-std-ipv4-32
```

And after doing some Google'ing it seems not many people have this kernal?

Anyway, I really need to get VirtualBox up and running ASAP, so any help would be appreciated :)

I am running Ubuntu 0.04 (Hardy) by the way. :D

---

### Post by Shazaam on 2009-03-06
In terminal...
```
sudo apt-get install linux-headers-$(uname -r)
```
Then do the recommended command...
```
sudo /etc/init.d/vboxdrv setup
```

---

### Post by Chaosleet on 2009-03-07
Hi, when I enter that command I get this:

```
admin@ks359837:~$ sudo apt-get install linux-headers-$(uname -r)
[sudo] password for admin: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-headers-2.6.28.1-xxxx-std-ipv4-32

```

---

### Post by Chaosleet on 2009-03-07
Alright, I think I know what's happening.

The place I bought my dedicated server from (ovh.co.uk) use their own version of the kernel: **2.6.27.10-grs (OVH)** and seen as it's a custom kernel I can't run the commands you gave me. I have looked over their site and I can't seem to find a download for their kernel (I think that's what I'm looking for) so I'm well and truly stuck now.

---

