---
title: "Getting higher screen resolutions for Ibex in Virtualbox"
date: 2008-10-31
forum: Virtualisation
---

### Post by SunnyRabbiera on 2008-10-31
Alright before I even commit to a full install I still like to install my distros in Virtualbox.
However I am stuck at low resolution thanks to the issue with Virtual box screen resolution that never got resolved and wont get resolved till jaunty.
But is there at least some way to make my screen resolution higher?
I know how to edit xorg but I have no idea what I should put in to get this issue fixed.
I looked at a solution on launchpad, but it didnt seem to work

---

### Post by SunnyRabbiera on 2008-10-31
Hello?

---

### Post by FrostyFlames on 2008-10-31
Have you installed the Guest Additions?

---

### Post by SunnyRabbiera on 2008-10-31
> **FrostyFlames said:**
> Have you installed the Guest Additions?

No I have not, and so far none of the guides I have found on doing it are kind of useless.
They dont explain the process that well

---

### Post by laurielegit on 2008-11-01
I'll second that. After using virtualbox for quite a while I still can not install guest additions. I know it's the answer to getting a higher screen resolution but when I downloaded the .iso and put it into my virtual machine I failed to see how to install it. If anyone knows a guide on how to install guest additions on a Linux guest then I would be most grateful if they posted it here

---

### Post by FrostyFlames on 2008-11-01
Assuming you have the guest additions loaded in the VirtualBox settings and the disk shows up on your Ubuntu Desktop... 

First you need to know what version of Ubuntu you installed (x86 or 64-bit). You can figure that out buy running

```
uname -m
```

This will probably spit out i386, i486, i586, i686, or x86_64.
If you get "iXXX" you're running x86.
If you get "x86_64" you're running 64-bit (also sometimes called amd64).

```

cd /media/cdrom
ls
```

When you run "ls" it should spit out the contents of the CD. My contents looked like this:

```
32Bit        VBoxLinuxAdditions-amd64.run  VBoxWindowsAdditions-amd64.exe
64Bit        VBoxLinuxAdditions-x86.run    VBoxWindowsAdditions.exe
AUTORUN.INF  VBoxSolarisAdditions.pkg      VBoxWindowsAdditions-x86.exe
```

Based on when we did the uname command, you will run 1 of the Linux versions of the additions. For sake of example I'll demonstrate both installs.

```
sudo ./VBoxLinuxAdditions-x86.run
``` - x86 Install

```
sudo ./VBoxLinuxAdditions-amd64.run
``` - 64-bit Install. Note: It doesn't matter if you're running an Intel CPU and you install this, it should work anyhow.

Both of these will auto run and do their thing. Once they are done they will ask if you want to reboot. Reboot.

---

### Post by laurielegit on 2008-11-01
Thanks, thats perfect

---

