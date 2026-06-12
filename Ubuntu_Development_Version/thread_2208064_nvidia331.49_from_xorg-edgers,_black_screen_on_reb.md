---
title: "nvidia331.49 from xorg-edgers, black screen on reboot."
date: 2014-02-26
forum: Ubuntu Development Version
---

### Post by sdowney717 on 2014-02-26
I am running ubuntu, not kubuntu or lubuntu or etc...
painful but recovery is simple.

unplug computer.
at boot menu go down one, enter
select recovery for latest kernel at boot menu

then select enable networking, takes a while

then select drop to root prompt

type in 

sudo apt-get remove nvidia331, (or is it nvidia-331)

then

sudo apt-get install nvidia-current

then sudo reboot

I am back up on ubuntu, now running 304.119

331.38 was working fine.
How to go back, can you run 
sudo apt-get install nvidia331.38 ??????

---

### Post by sgage on 2014-02-26
> **sdowney717 said:**
> painful but recovery is simple.

unplug computer.
at boot menu go down one, enter
select recovery for latest kernel at boot menu

then select enable networking, takes a while

then select drop to root prompt

type in 

sudo apt-get remove nvidia331, (or is it nvidia-331)

then

sudo apt-get install nvidia-current

then sudo reboot

I am back up on ubuntu, now running 304.119

331.38 was working fine.
How to go back, can you run 
sudo apt-get install nvidia331.38 ??????

Yes, 

```
sudo apt-get install nvidia-331
```

will install 331.38.

---

### Post by Cavsfan on 2014-02-26
Yep, 331.49 killed my system too. 

I just logged in normally and when it wouldn't go past the orange screen, I pressed CNTL+ALT+F1 to bring up a CLI screen to login to.

Then once logged in I entered

```
sudo ppa-purge ppa:xorg-edgers/ppa
```

That downgraded all the packages from that ppa and installed 331.38 and the DKMS modules into 3.13.0-12-generic kernel.

**sudo reboot** and I'm back in business.

```
cavsfan@cavsfan-MS-7529:~$ dpkg -l | grep nvidia
ii  nvidia-331                                                  331.38-0ubuntu3                                 amd64        NVIDIA binary driver - version 331.38
rc  nvidia-331-updates                                          331.20-0ubuntu9                                 amd64        NVIDIA binary Xorg driver, kernel module and VDPAU library
ii  nvidia-libopencl1-331                                       331.38-0ubuntu3                                 amd64        NVIDIA OpenCL Driver and ICD Loader library
rc  nvidia-libopencl1-331-updates                               331.20-0ubuntu9                                 amd64        NVIDIA OpenCL Driver and ICD Loader library
ii  nvidia-opencl-icd-331                                       331.38-0ubuntu3                                 amd64        NVIDIA OpenCL ICD
rc  nvidia-opencl-icd-331-updates                               331.20-0ubuntu9                                 amd64        NVIDIA OpenCL ICD
rc  nvidia-persistenced                                         331.20-0ubuntu1~xedgers~trusty1                 amd64        Load the NVIDIA kernel driver and create device files
ii  nvidia-prime                                                0.5.7                                           amd64        Tools to enable NVIDIA's Prime
ii  nvidia-settings                                             331.20-0ubuntu8                                 amd64        Tool for configuring the NVIDIA graphics driver

```

It looks like I have some redundancies but I'm not touching anything at this point.

---

### Post by xc3RnbFO8P on 2014-02-26
Im dead...

---

### Post by sdowney717 on 2014-02-26
your in good company, painful but fairly easy to make it work again.

---

### Post by Cavsfan on 2014-02-26
> **Ringi said:**
> Im dead...

Just purge the ppa and you should be good.

```
sudo ppa-purge ppa:xorg-edgers/ppa
``` 

See just above your post.

---

### Post by xc3RnbFO8P on 2014-02-26
I did that > sudo ppa-purge ppa:xorg-edgers/ppa  and did sudo apt-get install nvidia-331
and now I got 331.49 op and running, but there is a update waiting!

[[img]http://farm8.staticflickr.com/7439/12797850194_1326146ec1_c.jpg[/img]](http://www.flickr.com/photos/96052779@N07/12797850194/)
[Screenshot from 2014-02-26 19:08:43](http://www.flickr.com/photos/96052779@N07/12797850194/) by [ringi_is](http://www.flickr.com/people/96052779@N07/), on Flickr

---

### Post by xc3RnbFO8P on 2014-02-26
Now Im getting this:
> Current Date/Time: ons feb 26 18:55:23 UTC 2014
Distro Release: No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu Trusty Tahr (development branch)
Release:	14.04
Codename:	trusty
Kernel Release: Linux version 3.13.0-13-generic (buildd@allspice) (gcc version 4.8.2 (Ubuntu 4.8.2-16ubuntu3) ) #33-Ubuntu SMP Tue Feb 25 18:52:10 UTC 2014
Gnome Release: gnome-shell: error while loading shared libraries: libwayland-egl.so.1: cannot open shared object file: No such file or directory

Kubuntu isn't working properly

---

### Post by ventrical on 2014-02-26
Could the OP please  put in what flavour is being used that prefixs the topic header because it is sometimes confusing when others  jump in with different flavours and we don't know what flavour is being used.

Thanks..

---

### Post by Cavsfan on 2014-02-26
I'm on plain Ubuntu Gnome Flashback (with Compiz) and the only thing I did was purge the ppa:

```
sudo ppa-purge ppa:xorg-edgers/ppa
```

The affected packages downgraded and I did not install anything afterwards. I rebooted and my system was good to go.

---

### Post by Cavsfan on 2014-02-26
Ventrical, do you know what the "ii" and "rc" mean at the far left? I've wondered that a while now.

```
cavsfan@cavsfan-MS-7529:~$ dpkg -l | grep nvidia
ii  nvidia-331                                                  331.38-0ubuntu3                                 amd64        NVIDIA binary driver - version 331.38
rc  nvidia-331-updates                                          331.20-0ubuntu9                                 amd64        NVIDIA binary Xorg driver, kernel module and VDPAU library
ii  nvidia-libopencl1-331                                       331.38-0ubuntu3                                 amd64        NVIDIA OpenCL Driver and ICD Loader library
rc  nvidia-libopencl1-331-updates                               331.20-0ubuntu9                                 amd64        NVIDIA OpenCL Driver and ICD Loader library
ii  nvidia-opencl-icd-331                                       331.38-0ubuntu3                                 amd64        NVIDIA OpenCL ICD
rc  nvidia-opencl-icd-331-updates                               331.20-0ubuntu9                                 amd64        NVIDIA OpenCL ICD
rc  nvidia-persistenced                                         331.20-0ubuntu1~xedgers~trusty1                 amd64        Load the NVIDIA kernel driver and create device files
ii  nvidia-prime                                                0.5.7                                           amd64        Tools to enable NVIDIA's Prime
ii  nvidia-settings                                             331.20-0ubuntu8                                 amd64        Tool for configuring the NVIDIA graphics driver

```

---

### Post by ventrical on 2014-02-26
> **Cavsfan said:**
> Ventrical, do you know what the "ii" and "rc" mean at the far left? I've wondered that a while now.

```
cavsfan@cavsfan-MS-7529:~$ dpkg -l | grep nvidia
ii  nvidia-331                                                  331.38-0ubuntu3                                 amd64        NVIDIA binary driver - version 331.38
rc  nvidia-331-updates                                          331.20-0ubuntu9                                 amd64        NVIDIA binary Xorg driver, kernel module and VDPAU library
ii  nvidia-libopencl1-331                                       331.38-0ubuntu3                                 amd64        NVIDIA OpenCL Driver and ICD Loader library
rc  nvidia-libopencl1-331-updates                               331.20-0ubuntu9                                 amd64        NVIDIA OpenCL Driver and ICD Loader library
ii  nvidia-opencl-icd-331                                       331.38-0ubuntu3                                 amd64        NVIDIA OpenCL ICD
rc  nvidia-opencl-icd-331-updates                               331.20-0ubuntu9                                 amd64        NVIDIA OpenCL ICD
rc  nvidia-persistenced                                         331.20-0ubuntu1~xedgers~trusty1                 amd64        Load the NVIDIA kernel driver and create device files
ii  nvidia-prime                                                0.5.7                                           amd64        Tools to enable NVIDIA's Prime
ii  nvidia-settings                                             331.20-0ubuntu8                                 amd64        Tool for configuring the NVIDIA graphics driver

```

rc is short for runrickus and ii is short for invisible ibex?

hehehehe ahahaeaeh .. it's been a long winter.. :) lol

edit.. I think rc could stand for release candidate and the ii is probably an index header of some sort .. but I don't know off hand... lots to learn around here.

rc ... repository catalog ?

---

### Post by xc3RnbFO8P on 2014-02-26
331.49-0ubuntu1~xedgers14.04.2 
is running fin here

```
dpkg -l | grep nvidia
ii  libkwinactivenvidiahack4                                    4:4.10.97-0ubuntu2                              amd64        library used by nvidia cards for the KDE window manager
rc  libkwinnvidiahack4                                          4:4.10.3-0ubuntu3                               amd64        library used by nvidia cards for the KDE window manager
rc  nvidia-304                                                  304.88-0ubuntu2                                 amd64        NVIDIA binary Xorg driver, kernel module and VDPAU library
rc  nvidia-325                                                  325.15-0ubuntu1~xedgers~saucy3                  amd64        NVIDIA binary Xorg driver, kernel module and VDPAU library
ii  nvidia-331                                                  331.49-0ubuntu1~xedgers14.04.2                  amd64        NVIDIA binary driver - version 331.49
ii  nvidia-common                                               1:0.2.88                                        amd64        transitional package for ubuntu-drivers-common
rc  nvidia-experimental-310                                     310.14-0ubuntu1                                 amd64        Experimental NVIDIA binary Xorg driver, kernel module and VDPAU library
ii  nvidia-libopencl1-331                                       331.49-0ubuntu1~xedgers14.04.2                  amd64        NVIDIA OpenCL Driver and ICD Loader library
ii  nvidia-opencl-icd-331                                       331.49-0ubuntu1~xedgers14.04.2                  amd64        NVIDIA OpenCL ICD
rc  nvidia-persistenced                                         331.20-0ubuntu1~xedgers~trusty1                 amd64        Load the NVIDIA kernel driver and create device files
ii  nvidia-prime                                                0.5.7                                           amd64        Tools to enable NVIDIA's Prime
ii  nvidia-settings                                             331.38-0ubuntu1~xedgers~trusty1                 amd64        Tool for configuring the NVIDIA graphics driver
rc  nvidia-settings-304                                         304.88-0ubuntu1                                 amd64        Tool for configuring the NVIDIA graphics driver
ii  nvidia-settings-319                                         331.38-0ubuntu1~xedgers~trusty1                 amd64        Transitional package for nvidia-settings
rc  nvidia-settings-325                                         325.15-0ubuntu1~xedgers~saucy2                  amd64        Tool for configuring the NVIDIA graphics driver
rc  nvidia-settings-331                                         331.20-0ubuntu1~xedgers~trusty1                 amd64        Tool for configuring the NVIDIA graphics driver
rc  nvidia-settings-experimental-310                            310.14-0ubuntu1                                 amd64        Tool for configuring the NVIDIA graphics driver
rig@rig-Aspire-R3600:~$ 
```

---

### Post by ventrical on 2014-02-26
```


There are 3 fields.  The first one is the called Desired, the second Status and the last one is Error.

Your first letter is r, thus the package is Removed
Your second letter is c, thus your config files are still there.
You don't have a third letter, thus no error.

```

---

### Post by ventrical on 2014-02-26
ii   means

```


[LIST=1]
[*]i: the package was marked for installation
[*]i: thepackage is successfully installed in the system
[/LIST]

```

[http://linuxprograms.wordpress.com/2010/05/12/ii-dpkg-list/](http://linuxprograms.wordpress.com/2010/05/12/ii-dpkg-list/)

---

### Post by Cavsfan on 2014-02-26
> **ventrical said:**
> rc is short for runrickus and ii is short for invisible ibex?

hehehehe ahahaeaeh .. it's been a long winter.. :) lol

edit.. I think rc could stand for release candidate and the ii is probably an index header of some sort .. but I don't know off hand... lots to learn around here.

rc ... repository catalog ?

:lol: Hehehehehehehe :lol: It hasn't been much of a winter here currently 71 degrees. :P

I got this from man dpkg-query

```
 dpkg-query -l 'libc6*'

              The first three columns of the output show the desired action, the package status, and errors, in that order.

              Desired action:
                u = Unknown
                i = Install
                h = Hold
                r = Remove
                p = Purge

              Package status:
                n = Not-installed
                c = Config-files
                H = Half-installed
                U = Unpacked
                F = Half-configured
                W = Triggers-awaiting
                t = Triggers-pending
                i = Installed

              Error flags:
                <empty> = (none)
                R = Reinst-required


```

```
cavsfan@cavsfan-MS-7529:~$ dpkg-query -l | grep nvidia
ii   nvidia-331                                                   331.38-0ubuntu3                                 amd64        NVIDIA  binary driver - version 331.38
rc   nvidia-331-updates                                           331.20-0ubuntu9                                 amd64        NVIDIA  binary Xorg driver, kernel module and VDPAU library
ii   nvidia-libopencl1-331                                        331.38-0ubuntu3                                 amd64        NVIDIA  OpenCL Driver and ICD Loader library
rc   nvidia-libopencl1-331-updates                                331.20-0ubuntu9                                 amd64        NVIDIA  OpenCL Driver and ICD Loader library
ii   nvidia-opencl-icd-331                                        331.38-0ubuntu3                                 amd64        NVIDIA  OpenCL ICD
rc   nvidia-opencl-icd-331-updates                                331.20-0ubuntu9                                 amd64        NVIDIA  OpenCL ICD
rc   nvidia-persistenced                                          331.20-0ubuntu1~xedgers~trusty1                 amd64        Load the  NVIDIA kernel driver and create device files
ii   nvidia-prime                                                 0.5.7                                           amd64        Tools to  enable NVIDIA's Prime
ii   nvidia-settings                                              331.20-0ubuntu8                                 amd64        Tool for  configuring the NVIDIA graphics driver

```

It would appear that "ii" means "Install, Installed, no errors" and "rc" means "Remove, Config files, no errors". At least that's how I see it. 
Anyone know more?

---

### Post by ventrical on 2014-02-26
already adressed that above.

---

### Post by Cavsfan on 2014-02-26
I was correct above ^^.

rc means:

```

[LIST=1]
[*]r: the package was marked for removal 
[*]c: the configuration files are currently present in the system 
[/LIST]

```

[http://linuxprograms.wordpress.com/2010/05/12/rc-dpkg-list/?relatedposts_exclude=758](http://linuxprograms.wordpress.com/2010/05/12/rc-dpkg-list/?relatedposts_exclude=758)

---

### Post by ventrical on 2014-02-26
yes .. below now ... :) lol

---

### Post by Cavsfan on 2014-02-26
So, knowing what I knowingly now know :lol: , I did this:

```
cavsfan@cavsfan-MS-7529:~$ dpkg-query -l | grep nvidia
ii  nvidia-331                                                  331.38-0ubuntu3                                 amd64        NVIDIA binary driver - version 331.38
ii  nvidia-libopencl1-331                                       331.38-0ubuntu3                                 amd64        NVIDIA OpenCL Driver and ICD Loader library
ii  nvidia-opencl-icd-331                                       331.38-0ubuntu3                                 amd64        NVIDIA OpenCL ICD
ii  nvidia-prime                                                0.5.7                                           amd64        Tools to enable NVIDIA's Prime
ii  nvidia-settings                                             331.20-0ubuntu8                                 amd64        Tool for configuring the NVIDIA graphics driver


```

It's odd that nvidia-settings is still 331.20 but who am I to complain. :P

---

### Post by ventrical on 2014-02-26
> **Cavsfan said:**
> So, knowing what I knowingly now know :lol: , I did this:

```
cavsfan@cavsfan-MS-7529:~$ dpkg-query -l | grep nvidia
ii  nvidia-331                                                  331.38-0ubuntu3                                 amd64        NVIDIA binary driver - version 331.38
ii  nvidia-libopencl1-331                                       331.38-0ubuntu3                                 amd64        NVIDIA OpenCL Driver and ICD Loader library
ii  nvidia-opencl-icd-331                                       331.38-0ubuntu3                                 amd64        NVIDIA OpenCL ICD
ii  nvidia-prime                                                0.5.7                                           amd64        Tools to enable NVIDIA's Prime
ii  nvidia-settings                                             331.20-0ubuntu8                                 amd64        Tool for configuring the NVIDIA graphics driver


```

It's odd that nvidia-settings is still 331.20 but who am I to complain. :P

 Yes .. especially when you got i,i,i,i, ya. :) lol

---

### Post by sdowney717 on 2014-02-26
> **ventrical said:**
> Could the OP please  put in what flavour is being used that prefixs the topic header because it is sometimes confusing when others  jump in with different flavours and we don't know what flavour is being used.

Thanks..

Plain Ubuntu

---

### Post by ventrical on 2014-02-27
> **sdowney717 said:**
> Plain Ubuntu


When you are creating a new topic there is an option, [prefix] , that you should use before you enter the title of your message.

Thanks..

---

### Post by fooman on 2014-02-27
i had the nvidia update as well and on reboot was brought to a black screen with a blinking cursor in upper left corner of screen.

ctrl-alt-f1 to a terminal and then all it took was a "sudo reboot"

on the second boot,  all was fine.  :)

```
Current Date/Time: Thu Feb 27 06:38:39 EST 2014
Distro Release: Ubuntu Trusty Tahr (development branch)
Kernel Release: Linux 3.14.0-031400rc3-generic
Gnome Release: GNOME Shell 3.10.4
Unity Release: unity 7.1.2

OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce GTX 480/PCIe/SSE2
OpenGL version string:  4.4.0 NVIDIA 331.49
```

---

### Post by xc3RnbFO8P on 2014-02-27
> **fooman said:**
> i had the nvidia update as well and on reboot was brought to a black screen with a blinking cursor in upper left corner of screen.

ctrl-alt-f1 to a terminal and then all it took was a "sudo reboot"

on the second boot,  all was fine.  :)

```
Current Date/Time: Thu Feb 27 06:38:39 EST 2014
Distro Release: Ubuntu Trusty Tahr (development branch)
Kernel Release: Linux 3.14.0-031400rc3-generic
Gnome Release: GNOME Shell 3.10.4
Unity Release: unity 7.1.2

OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce GTX 480/PCIe/SSE2
OpenGL version string:  4.4.0 NVIDIA 331.49
```

I hate you :)

---

### Post by sdowney717 on 2014-02-27
> **fooman said:**
> i had the nvidia update as well and on reboot was brought to a black screen with a blinking cursor in upper left corner of screen.

ctrl-alt-f1 to a terminal and then all it took was a "sudo reboot"

on the second boot,  all was fine.  :)

```
Current Date/Time: Thu Feb 27 06:38:39 EST 2014
Distro Release: Ubuntu Trusty Tahr (development branch)
Kernel Release: Linux 3.14.0-031400rc3-generic
Gnome Release: GNOME Shell 3.10.4
Unity Release: unity 7.1.2

OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce GTX 480/PCIe/SSE2
OpenGL version string:  4.4.0 NVIDIA 331.49
```

I must have held the power button in about 5 times and rebooted before giving up and uninstalling back to 304.
I did not have a cursor blinking, I had a black screen.

---

### Post by Cavsfan on 2014-03-01
> **Cavsfan said:**
> So, knowing what I knowingly now know :lol: , I did this:

```
cavsfan@cavsfan-MS-7529:~$ dpkg-query -l | grep nvidia
ii  nvidia-331                                                  331.38-0ubuntu3                                 amd64        NVIDIA binary driver - version 331.38
ii  nvidia-libopencl1-331                                       331.38-0ubuntu3                                 amd64        NVIDIA OpenCL Driver and ICD Loader library
ii  nvidia-opencl-icd-331                                       331.38-0ubuntu3                                 amd64        NVIDIA OpenCL ICD
ii  nvidia-prime                                                0.5.7                                           amd64        Tools to enable NVIDIA's Prime
ii  nvidia-settings                                             331.20-0ubuntu8                                 amd64        Tool for configuring the NVIDIA graphics driver


```

It's odd that nvidia-settings is still 331.20 but who am I to complain. :P

> **ventrical said:**
> Yes .. especially when you got i,i,i,i, ya. :) lol

Yep, I like knowing what I have and knowing how to tell what I have. :p

> **Ringi said:**
> I hate you :)

:lol: Crack me up!

Since I just have a 9800GT I'm not going to worry about the bleeding edge drivers any more.
I haven't been able to update my windows 7 driver for several months as each time I do something gets an exception error or worse.
The current stable windows driver is 334.89 but it won't even run on my PC. However I just got new fans, a new WD hard drive (5 year warranty), and a video card so I'm hoping to stretch it out a few more years.

---

### Post by monkeybrain20122 on 2014-03-03
Check if you have bumblebee installed. If yours is not an Optimus machine it will break your display, in that case just remove bumblebee and it should work fine.
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-331/+bug/1265570](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-331/+bug/1265570)

---

### Post by QDR06VV9 on 2014-03-03
> **ventrical said:**
> rc is short for runrickus and ii is short for invisible ibex?

hehehehe ahahaeaeh .. it's been a long winter.. :) lol
You are on a roll, I'm just sitting here Chuckling. :D
I read where you were running 10 Machines all trusty?, That separates the men from the boys.
With saucy I was maintaining 5 and that  was kinda a handful for this Old fart.

---

