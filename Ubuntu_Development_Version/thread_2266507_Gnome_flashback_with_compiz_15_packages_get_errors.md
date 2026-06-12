---
title: "Gnome flashback with compiz: 15 packages get errors from dependency problems"
date: 2015-02-23
forum: Ubuntu Development Version
---

### Post by Cavsfan on 2015-02-23
For the past 4-5 days I have gotten this:

```
cavsfan@cavsfan-MS-7529:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
15 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] Y
Setting up libgl1-mesa-glx:amd64 (10.5.0~rc1-0ubuntu1) ...
update-alternatives: warning: forcing reinstallation of alternative /usr/lib/nvidia-340/ld.so.conf because link group x86_64-linux-gnu_gl_conf is broken
update-alternatives: error: error creating symbolic link `/usr/lib/vdpau/libvdpau_nvidia.so.1.dpkg-tmp': No such file or directory
dpkg: error processing package libgl1-mesa-glx:amd64 (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of libgldi3:amd64:
 libgldi3:amd64 depends on libgl1-mesa-glx | libgl1; however:
  Package libgl1-mesa-glx:amd64 is not configured yet.
  Package libgl1 is not installed.
  Package libgl1-mesa-glx:amd64 which provides libgl1 is not configured yet.

dpkg: error processing package libgldi3:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of cairo-dock-core:
 cairo-dock-core depends on libgldi3 (= 3.4.1-0ubuntu1); however:
  Package libgldi3:amd64 is not configured yet.

dpkg: error processing package cairo-dock-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of cairo-dock-plug-ins:amd64:
 cairo-dock-plug-ins:amd64 depends on cairo-dock-core (>= 3.4.1); however:
  Package cairo-dock-core is not configured yet.
 cairo-dock-plug-ins:amd64 depends on libgl1-mesa-glx | libgl1; however:
  Package libgl1-mesa-glx:amd64 is not cNo apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                                                                  No apport report written because the error message indicates its a followup error from a previous failure.
                                         No apport report written because MaxReports is reached already
                                                                                                       No apport report written because MaxReports is reached already
                                                                                                                                                                     No apport report written because MaxReports is reached already
                No apport report written because MaxReports is reached already
                                                                              No apport report written because MaxReports is reached already
                                                                                                                                            No apport report written because MaxReports is reached already
                                                                                                                                                                                                          No apport report written because MaxReports is reached already
                                                     No apport report written because MaxReports is reached already
                                                                                                                   No apport report written because MaxReports is reached already
                                                                                                                                                                                 No apport report written because MaxReports is reached already
                            onfigured yet.
  Package libgl1 is not installed.
  Package libgl1-mesa-glx:amd64 which provides libgl1 is not configured yet.

dpkg: error processing package cairo-dock-plug-ins:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of cairo-dock-plug-ins-dbus-interface-python:
 cairo-dock-plug-ins-dbus-interface-python depends on cairo-dock-plug-ins (>= 3.4.1-0ubuntu1); however:
  Package cairo-dock-plug-ins:amd64 is not configured yet.

dpkg: error processing package cairo-dock-plug-ins-dbus-interface-python (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of cairo-dock-plug-ins-integration:amd64:
 cairo-dock-plug-ins-integration:amd64 depends on cairo-dock-core (>= 3.4.1); however:
  Package cairo-dock-core is not configured yet.

dpkg: error processing package cairo-dock-plug-ins-integration:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency No apport report written because MaxReports is reached already
                                                                               No apport report written because MaxReports is reached already
                                                                                                                                             problems prevent configuration of compiz-plugins-default:amd64:
 compiz-plugins-default:amd64 depends on libgl1-mesa-glx | libgl1; however:
  Package libgl1-mesa-glx:amd64 is not configured yet.
  Package libgl1 is not installed.
  Package libgl1-mesa-glx:amd64 which provides libgl1 is not configured yet.

dpkg: error processing package compiz-plugins-default:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of compiz-gnome:
 compiz-gnome depends on compiz-plugins-default (= 1:0.9.12.1+15.04.20150213-0ubuntu1); however:
  Package compiz-plugins-default:amd64 is not configured yet.

dpkg: error processing package compiz-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of compiz-plugins:amd64:
 compiz-plugins:amd64 depends on compiz-plugins-default (= 1:0.9.12.1+15.04.20150213-0ubuntu1); however:
  Package compiz-plugins-default:amd64 is not configured yet.
 compiz-plugins:amd64 depends on libgl1-mesa-glx | libgl1; however:
  Package libgl1-mesa-glx:amd64 is not configured yet.
  Package libgl1 is not installed.
  Package libgl1-mesa-glx:amd64 which provides libgl1 is not configured yet.

dpkg: error processing package compiz-plugins:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of cairo-dock:
 cairo-dock depends on cairo-dock-core (>= 3.4.1-0ubuntu1); however:
  Package cairo-dock-core is not configured yet.
 cairo-dock depends on cairo-dock-plug-ins (>= 3.4.1); however:
  Package cairo-dock-plug-ins:amd64 is not configured yet.
 cairo-dock depends on cairo-dock-plug-ins-dbus-interface-python (>= 3.4.1); however:
  Package cairo-dock-plug-ins-dbus-interface-python is not configured yet.
 cairo-dock depends on cairo-dock-plug-ins-integration (>= 3.4.1); however:
  Package cairo-dock-plug-ins-integration:amd64 is not configured yet.

dpkg: error processing package cairo-dock (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of compiz:
 compiz depends on compiz-plugins-default (>= 1:0.9.12.1+15.04.20150213-0ubuntu1); however:
  Package compiz-plugins-default:amd64 is not configured yet.
 compiz depends on compiz-gnome; however:
  Package compiz-gnome is not configured yet.

dpkg: error processing package compiz (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of unity:
 unity depends on libgl1-mesa-glx | libgl1; however:
  Package libgl1-mesa-glx:amd64 is not configured yet.
  Package libgl1 is not installed.
  Package libgl1-mesa-glx:amd64 which provides libgl1 is not configured yet.
 unity depends on compiz; however:
  Package compiz is not configured yet.
 unity depends on compiz-plugins-default; however:
  Package compiz-plugins-default:amd64 is not configured yet.

dpkg: error processing package unity (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on unity; however:
  Package unity is not configured yet.

dpkg: error processing package ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xscreensaver-gl:
 xscreensaver-gl depends on libgl1-mesa-glx | libgl1; however:
  Package libgl1-mesa-glx:amd64 is not configured yet.
  Package libgl1 is not installed.
  Package libgl1-mesa-glx:amd64 which provides libgl1 is not configured yet.

dpkg: error processing package xscreensaver-gl (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xscreensaver-gl-extra:
 xscreensaver-gl-extra depends on libgl1-mesa-glx | libgl1; however:
  Package libgl1-mesa-glx:amd64 is not configured yet.
  Package libgl1 is not installed.
  Package libgl1-mesa-glx:amd64 which provides libgl1 is not configured yet.
 xscreensaver-gl-extra depends on xscreensaver-gl (>= 5.04-3); however:
  Package xscreensaver-gl is not configured yet.

dpkg: error processing package xscreensaver-gl-extra (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libgl1-mesa-glx:amd64
 libgldi3:amd64
 cairo-dock-core
 cairo-dock-plug-ins:amd64
 cairo-dock-plug-ins-dbus-interface-python
 cairo-dock-plug-ins-integration:amd64
 compiz-plugins-default:amd64
 compiz-gnome
 compiz-plugins:amd64
 cairo-dock
 compiz
 unity
 ubuntu-desktop
 xscreensaver-gl
 xscreensaver-gl-extra
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Am I the only one seeing this and is this one of those wait and see situations or what?

---

### Post by dino99 on 2015-02-23
for a first step, i should purge the nvidia driver and install the latest 346.35 from the archive

---

### Post by ventrical on 2015-02-23
Hi,

```


sudo dpkg --configure -a

sudo apt-get install -f


```

---

### Post by Cavsfan on 2015-02-23
> **9d9 said:**
> for a first step, i should purge the nvidia driver and install the latest 346.35 from the archive

I have this installed which is more than my old Geforce 9800 GT video card can handle in windows 7:

```
cavsfan@cavsfan-MS-7529:~$ dpkg -l | grep nvidia
ii  nvidia-340                                           340.76-0ubuntu1                            amd64        NVIDIA binary driver - version 340.76
ii  nvidia-340-uvm                                       340.76-0ubuntu1                            amd64        NVIDIA Unified Memory kernel module
ii  nvidia-opencl-icd-340                                340.76-0ubuntu1                            amd64        NVIDIA OpenCL ICD
ii  nvidia-settings                                      346.35-0ubuntu1                            amd64        Tool for configuring the NVIDIA graphics driver

```

On second thought I might just do that. What could possibly go wrong? :p

> **ventrical said:**
> Hi,

```


sudo dpkg --configure -a

sudo apt-get install -f


```

I tried that and had the same results as above. I also tried these several times with no bueno as the result.

```
sudo apt-get autoremove
sudo apt-get clean
sudo apt-get autoclean
sudo apt-get check
sudo dpkg --configure -a
sudo apt-get -f install
sudo apt-get update
```

If it comes down to a fresh install to fix it, that isn't happening.
Everytime I get some updates they all update/upgrade then this (1st post) is spewed out on my terminal.

I don't see any ill effects.

---

### Post by Cavsfan on 2015-02-23
Would you believe I entered **sudo apt-get purge nvidia*** and it purged these:
```
nvidia-340* nvidia-340-uvm* nvidia-opencl-icd-340* nvidia-settings*
```

Plus it finished updating the 15 packages that were the problematic ones. :lolflag:

```
Setting up libgldi3:amd64 (3.4.1-0ubuntu1) ...
Setting up cairo-dock-core (3.4.1-0ubuntu1) ...
Setting up cairo-dock-plug-ins:amd64 (3.4.1-0ubuntu1) ...
Setting up cairo-dock-plug-ins-dbus-interface-python (3.4.1-0ubuntu1) ...
Setting up cairo-dock-plug-ins-integration:amd64 (3.4.1-0ubuntu1) ...
Setting up compiz-plugins-default:amd64 (1:0.9.12.1+15.04.20150213-0ubuntu1) ...
Setting up compiz-gnome (1:0.9.12.1+15.04.20150213-0ubuntu1) ...
Installing new version of config file /etc/X11/Xsession.d/65compiz_profile-on-session ...
Setting up compiz-plugins:amd64 (1:0.9.12.1+15.04.20150213-0ubuntu1) ...
Setting up cairo-dock (3.4.1-0ubuntu1) ...
Setting up compiz (1:0.9.12.1+15.04.20150213-0ubuntu1) ...
Setting up unity (7.3.1+15.04.20150219.2-0ubuntu1) ...
Setting up ubuntu-desktop (1.330) ...
Setting up xscreensaver-gl (5.30-1ubuntu1) ...
Installing new version of config file /etc/X11/app-defaults/XScreenSaver-gl ...
Setting up xscreensaver-gl-extra (5.30-1ubuntu1) ...
Processing triggers for libc-bin (2.19-15ubuntu1) ...

```

Now to install the nvidia-346 driver.

---

### Post by Cavsfan on 2015-02-23
Well, that did not go well at all. I rebooted after installing the driver and I seen some messages with the little green circle that I was not seeing before. They went by too fast to read.
But after I entered my password it would go no further. It would not even go full screen.
I figured that was too new for this card. I haven't been able to update the driver in Windows 7 for over 2 years.

So, I Cntl+Alt+F1 and logged in to tty, purged the nvidia driver and rebooted using the Nouveau driver. Now everything looks fine.

I'll try to re-install the 340.76 driver tomorrow and I should be ok then. We'll see...

---

### Post by Cavsfan on 2015-02-24
I installed nvidia-340, which installed the same drivers I had previously and rebooted.

All seems to be in order. It was just weird that purging the above driver let the 15  packages finally update.

I had to have an nVidia driver installed or else my conky would be misaligned with the missing info from it. 

I guess I won't be able to go much past the 340.76 driver though if at all. It definitely chocked on the 346.35 driver. Time will tell.

Chock this up to weirdness I guess. :p

Thanks for the posts. :)

---

