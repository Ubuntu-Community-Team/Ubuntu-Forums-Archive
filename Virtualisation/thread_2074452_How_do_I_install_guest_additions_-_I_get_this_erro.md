---
title: "How do I install guest additions - I get this error"
date: 2012-10-21
forum: Virtualisation
---

### Post by Codeless on 2012-10-21
I recently created an ubuntu natty distro unfortunately the sound was out of synch and no matter what I did I couldn't fix it. I made another thread regarding that.

Anyway I decided to build a new vm using ubuntu 12.10 which I could from the ubuntu website

if I go to devices and install guest additions I get this

Verifying archive integrity... All good.
Uncompressing VirtualBox 4.2.0 Guest Additions for Linux..........
VirtualBox Guest Additions installer
Removing existing VirtualBox DKMS kernel modules ...done.
Removing existing VirtualBox non-DKMS kernel modules ...done.
Building the VirtualBox Guest Additions kernel modules
The headers for the current running kernel were not found. If the following
module compilation fails then this could be the reason.

Building the main Guest Additions module ...done.
Building the shared folder support module ...done.
Building the OpenGL support module ...done.
Doing non-kernel setup of the Guest Additions ...done.
Starting the VirtualBox Guest Additions ...done.
Installing the Window System drivers
Warning: unknown version of the X Window System installed.  Not installing
X Window System drivers.
Installing modules ...done.
Installing graphics libraries and desktop services components ...done.
Press Return to close this window...

now after this the mouse is still laggy and widescreen is not enabled, theres no noticible difference. Is this because of the unknown version of the x window system above?

how do I fix this

---

### Post by cepal on 2012-10-31
So far I've only found the answer here: [http://ubuntuforums.org/showthread.php?t=2057146](http://ubuntuforums.org/showthread.php?t=2057146)
 
The answer is:
Code:
sudo apt-get install virtualbox-guest-additions
It will only find 4.1.18 additions but it should be fine for the time being until Vbox provides updated additions package.
 
**EDIT #1**: There is new VirtualBox package, 4.2.4, that one has Guest Additions aware of Xorg 1.13 and installs well on Ubuntu 12.10. Don't know why VBox update checker doesn't detect this so you have to manually browse their web, download it and install manually.
 
One quick advice: use google before you start askinig question which have already been asked, or even answered elsewhere!

---

### Post by ThiagoK on 2013-05-02
Folks -

I've just upgraded to Ubuntu 13.04 (64 bit) and then installed the accurate version of VirtualBox (4.2.12). It all went just as perfect as I wished except for the fact that, when I tried the "Install the Guest Additions" option at "Devices", it didn't work at all. I tried the sudo apt-get install virtualbox-guest-additions, but it didn't worked either. The Terminal suggested the following command instead: virtualbox-guest-additions-iso and that worked for installation at least, but not for running the other OS in widescreen mode through Virtualbox. Why so?

---

### Post by Lamukra on 2013-05-04
[COLOR=#333333][FONT=Ubuntu Beta]Hey guys!

In order to install Oracle Guest Additions on Ubuntu Guest OS (tested on 12.04.2) you have to make sure that there is nothing from ubuntu specific virtualbox packages, do this

```
sudo apt-get remove --purge virtualbox*
```

After it is done, you have to install some essential tools for building and for guest additions as well, so do this

```
sudo apt-get install build-essential dkms
```

now check that headers are installed

```
sudo apt-get install linux-headers-$(uname -r)
```

after this, jsut in case reboot, dunno why but sometime i got wrong result if not rebooted

```
sudo reboot
```

after you are done, just pres HOST+D
this will mount guest additions iso
after you should be presented with autorun dialog and you should be able to push RUN and it will automatically install GA
or you ca
do this

```
cd /media/V {hit TAB and it will autocomplete name of the mounted drive}
```

then do the installation

```
sudo ./VBoxL {hit TAB here as well and it will autocomplete}
```

should work

[/FONT][/COLOR][COLOR=#ff0000][FONT=Ubuntu Beta]BUT BE AWARE!!!!!

Installing Guest Additions (does not matter from whom Oracle or Ubuntu specific) will be a cause of not bootable system with enabled 3D acceleration, disable it and you are good
I am still trying to get 3d working with 12.04.2, no luck for now[/FONT][/COLOR]

---

### Post by ThiagoK on 2013-05-05
Thanks a lot, Lamukra, but it didn't work for the ubuntu 13.04 - it's still stuck at the same point.

---

### Post by Lamukra on 2013-05-05
> **ThiagoK said:**
> Thanks a lot, Lamukra, but it didn't work for the ubuntu 13.04 - it's still stuck at the same point.

Dunno if that solution helped to Codeless , but **ThiagoK**, tell what is version of your Virtualbox and what is a problem - is it the same?

What guest you are trying to install 64 or 32 bit

---

### Post by Lamukra on 2013-05-05
Hey, ThiagoK

I just tried installing Ubuntu 13.04 x64 guest on My Virtualbox 4.2.12 and it installs Guest Additions 4.2.12 sucessfully with no errors.
I made all neccessary steps as mentioned before in one of my posts in this thread. 

I can confirm that on Windows 8 Pro x64 with VirtualBox 4.2.12 corresponding Guest Additions install succesfully with no errors.
3D experience in 13.04 is very slow now in VirtualBox, but it is another story.

---

