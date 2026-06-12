---
title: "What to actually install for drivers? (GTX 970)"
date: 2016-05-19
forum: Ubuntu/Debian BASED
---

### Post by bennylava2 on 2016-05-19
Hi all, new here. I am very new to Linux and I recently installed Zorin OS9 core 64 bit.

So I tried to go ahead and use the Synaptic Package manager and download  and install the Nvidia drivers. Problem is, they don't really make it  very easy to understand what the different Nvidia drivers actually are. I  searched "nvidia" in the search bar of the Synaptic package manager, and a list of  (packages?) showed up. But none of them are very clear on if they are a  GTX 970 driver for Linux. It all reads more like is some kind of driver  editor, or weird Nvidia server setup. None of it simply says "Latest  Nvidia driver for Linux". Its very difficult for me to determine which  one to actually install.

Can anyone point out exactly what I need to look for, word for word, in  the synaptic package manager? When looking for the correct driver for my  GTX 970. Thanks!

---

### Post by bennylava2 on 2016-05-19
Learned that I shouldn't be using the synaptic package manager to get the Nvidia drivers. Should I be using the Zorin app center?

---

### Post by Rob Sayer on 2016-05-22
Since it's ubuntu based there should be something called additional drivers or driver manager or something similar.

---

### Post by Bucky Ball on 2016-05-22
Do an update, open Additional Drivers, use the 'Propietary, tested' driver there, 361.42.

I'm running an Nvidia GTX 970 on 16.04 LTS also. Works flawlessly. ;)

(Note: You probably need to enable the 'Canonical Partners' repo in Software and Updates> Other Software before doing any of this.)

PS: Just noticed you are on Zorin. On Ubuntu, no, Synaptic is not the way to go for this, and I doubt Zorin app centre is, either, if you have Additional Drivers. Good luck.)

---

### Post by Bashing-om on 2016-05-22
bennylava2; Hello;

A thought, as Zorin is based on ubuntu. I would expect to have access to the same resources.
Depending on the version of X that is present:
```

X -version

```
Maybe the driver you want is available in either our software repository, or perhaps you can obtain the required driver from our trusted PPA ?
What returns:
```

sudo ubuntu-drivers devices
sudo ubuntu-drivers list

```
To see what an option might be.


[INDENT][INDENT]together we can
[/INDENT][/INDENT]

---

