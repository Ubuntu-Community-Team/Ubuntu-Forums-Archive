---
title: "Sudden troubles with nvidia proprietary driver"
date: 2018-02-24
forum: Ubuntu Development Version
---

### Post by Wise Ferret on 2018-02-24
Today my nvidia-390 driver (on geforce gtx770) broke down. I get only an extremely low resolution with it, although it seems to be selected in the restricted drivers window, but nvidia-settings does not show the any settings options.
When I remove the proprietary driver the opensource driver works in full resolution, but it has other problems (like gdm not recognising mouse clicks! arrrgh!)
When I re-install the nvidia driver I get these weird errors:
```
nvidia_390:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/4.15.0-10-generic/updates/dkms/

nvidia_390_modeset.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/4.15.0-10-generic/updates/dkms/

nvidia_390_drm.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/4.15.0-10-generic/updates/dkms/

nvidia_390_uvm.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/4.15.0-10-generic/updates/dkms/

depmod.......

DKMS: install completed.
Setting up nvidia-settings (390.25-0ubuntu0~gpu18.04.1) ...
Processing triggers for libc-bin (2.27-0ubuntu2) ...
Processing triggers for man-db (2.8.1-1) ...
Processing triggers for gnome-menus (3.13.3-11ubuntu1) ...
Setting up nvidia-opencl-icd-390 (390.25-0ubuntu0~gpu18.04.1) ...
Setting up libcuda1-390 (390.25-0ubuntu0~gpu18.04.1) ...
Processing triggers for initramfs-tools (0.130ubuntu3) ...
update-initramfs: Generating /boot/initrd.img-4.15.0-10-generic
/sbin/ldconfig.real: Warning: ignoring configuration file that cannot be opened: /etc/ld.so.conf.d/i386-linux-gnu_EGL.conf: No such file or directory
/sbin/ldconfig.real: Warning: ignoring configuration file that cannot be opened: /etc/ld.so.conf.d/i386-linux-gnu_GL.conf: No such file or directory
/sbin/ldconfig.real: Warning: ignoring configuration file that cannot be opened: /etc/ld.so.conf.d/x86_64-linux-gnu_EGL.conf: No such file or directory
/sbin/ldconfig.real: Warning: ignoring configuration file that cannot be opened: /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf: No such file or directory
Processing triggers for libc-bin (2.27-0ubuntu2) ...

```
Any ideas?

---

### Post by #&amp;thj^% on 2018-02-24
Are you using this PPA>>ppa:graphics-drivers/ppa
One other question have tried using "quiet splash nomodeset" yet?
That is set in "/etc/defaualt/grub"

---

### Post by Wise Ferret on 2018-02-24
I'm not using ppa:graphics-drivers/ppa. Should I?
I added "nomodeset" to the file (the splash and quiet were already there), but it did not help.

---

### Post by Wise Ferret on 2018-02-24
The driver seems to be loaded, it just doesn't work:
```
  *-display                 
       description: VGA compatible controller
       product: GK104 [GeForce GTX 770]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:16 memory:f6000000-f6ffffff memory:e8000000-efffffff memory:f0000000-f1ffffff ioport:e000(size=128) memory:c0000-dffff

```

---

### Post by #&amp;thj^% on 2018-02-24
Well I have better luck with it. (The PPA)
```
Card-2: NVIDIA GF114 [GeForce GTX 560 Ti]
           Display Server: x11 (X.Org 1.19.6 ) drivers: modesetting,nvidia
           Resolution: 1920x1080@60.00hz
           OpenGL: renderer: GeForce GTX 560 Ti/PCIe/SSE2
           version: 4.5.0 NVIDIA 390.25

```

We have to bear in mind here that Nvidia and Wayland and even with Xorg is going to be problematic for a short time to come. :(
If you want my **guess** here most likely until the next Dev/cycle...and that might be optimistic. ;)
EDIT: This seems to work for my card here, instead of using **"nomodeset" **I am using this **"nogpumanager"**
And I have to watch carefully any changes made to "/etc/X11/xorg.conf"
Jut my small effort to help. :)

---

### Post by Wise Ferret on 2018-02-24
Unfortunately, the "nogpumanager" grub option doesn't help either.

---

### Post by mc4man on 2018-02-24
390.25-0ubuntu0~gpu18.04.1 package is from the graphics driver ppa so you must have the ppa enabled
Ubuntu repos did get a 390 build about 20 hrs. ago  ( in 18.04 proposed)though it seems to not be available any more..
[https://launchpad.net/ubuntu/+source/nvidia-graphics-drivers-390](https://launchpad.net/ubuntu/+source/nvidia-graphics-drivers-390)

(- the new one in proposed may be a first attempt to resolve the mesa 18.x/libglvnd issue..

What version of mesa are you using? 18.0.0~rc4-1ubuntu1 (proposed) or 17.3.3 (current non proposed version

---

### Post by #&amp;thj^% on 2018-02-24
Have you just by chance looked in "/etc/X11/" for multiple "xorg.conf" files yet?
That has been a problem for me as I stated in my last post.

---

### Post by Wise Ferret on 2018-02-24
No multiple xorg.conf files (in fact, not even one - just xorg.cong.failsafe).
I removed the mamarley repo, which was indeed on my system, but nvidia-390 was not from there but from bionic.
My mesa is from proposed. I wish I could keep proposed, because libreoffice 6 :-)

---

### Post by Wise Ferret on 2018-02-24
Sorry, the drivers are indeed taken from graphics driver ppa. However, after I remove all the nvidia packages I cannot just remove the ppa and install 384, because it makes me remove half of gnome with it...
Should I just wait for the 390 to reach proposed?

---

### Post by mc4man on 2018-02-24
> **Wise Ferret said:**
> Sorry, the drivers are indeed taken from graphics driver ppa. However, after I remove all the nvidia packages I cannot just remove the ppa and install 384, because it makes me remove half of gnome with it...
Should I just wait for the 390 to reach proposed?
I would wait for the nvidia drivers to update to the new mesa that you got from proposed. The Ubuntu repo nvidia packages were updated to reflect a 'breaks on' the new mesa, the ppa driver packages never were but that doesn't mean they'd work correctly (with new mesa, ect.

Shouldn't be that long, otherwise you could try downgrading mesa but likely not worth the hassle.
(- or do a fresh install & don't upgrade mesa from -proposed..

Edit: the 390 build ib 18.04 proposed failed on arm so were not published. But looking at the amd64 build it's going to be packaed in a different way than before. I'd be patient & let things square up & settle.

---

### Post by Wise Ferret on 2018-02-24
Thanks for the reassurance!

---

### Post by mc4man on 2018-02-25
> **Wise Ferret said:**
> Thanks for the reassurance!
For curiosity grabbed the 390 source from -proposed, had it rebuilt in LP excluding armhf & installed it on an install with full on -proposed.
Seemed to work ok though it would be better suited for a desktop as currently there is no provision for hybrid cards on laptops (optimus) or least none I could see. ( nvidia-prime use alternatives which aren't used in the upcoming driver..

So it looks like desktop cards should be ok, laptop hybrids remain to be seen (and for me could be a moot point if prime synchronization remains broken on the 4.15 kernel.

---

### Post by Wise Ferret on 2018-02-27
390 reached proposed. My desktop is working fine again - hooray!

---

### Post by fthx on 2018-02-27
390 came out of proposed and went in release this morning and my desktop (with optimus) came out of order...
Was quite hard to solve it, I'm back to nouveau.

Don't know what was wrong, there are many changes in nvidia packaging. I had issues with GL alternatives and prime, but it was a total mess.
Any advice/experience would be appreciated :-) as I plan to go back to proprietary Nvidia.

---

### Post by #&amp;thj^% on 2018-02-27
What repo is mesa from?
```
apt policy mesa-utils
```
And:
```
 apt policy nvidia-driver-390
nvidia-driver-390:
  Installed: 390.25-0ubuntu1
  Candidate: 390.25-0ubuntu1
  Version table:
 *** 390.25-0ubuntu1 500
        500 http://us.archive.ubuntu.com/ubuntu bionic/restricted amd64 Packages
        100 /var/lib/dpkg/status

```

---

### Post by mc4man on 2018-02-27
> **fthx said:**
> 390 came out of proposed and went in release this morning and my desktop (with optimus) came out of order...
Was quite hard to solve it, I'm back to nouveau.

Don't know what was wrong, there are many changes in nvidia packaging. I had issues with GL alternatives and prime, but it was a total mess.
Any advice/experience would be appreciated :-) as I plan to go back to proprietary Nvidia.
Likely if you did a fresh install it would sort of work out for you.
Current deal on an optimus laptop as seen here - 
nvidia-prime is useless
So if you want nvidia then install the 390 drivers. You should then boot to nvidia drivers. 
If using nvidia drivers & want to use Intel then remove the nvidia driver package & reboot
(- there may be some command to switch back & forth, no idea, not documented

So atm & maybe from here on out no switching via nvidia-prime/prime profiles

Additionally - 
If one still has the 4.13 kernel & the 4.15 kernel, 
While you can get the kernel modules to build for both only the 4.15 kernel will boot to nvidia, 4.13 will revert back to intel.
Why does that matter? Well the 4.15 kernel doesn't support Prime Synchronization while the 4.13 & earlier do. 

So for optimus owners - 
If you only want to use nvidia then you're in luck.
If you love screen tearing you're doubly in luck

Otherwise optimus owners have been doubly screwed by this move..

---

### Post by fthx on 2018-02-28
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-390/+bug/1752053](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-390/+bug/1752053)

---

### Post by fthx on 2018-02-28
As in :
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-390/+bug/1752053/comments/7](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-390/+bug/1752053/comments/7)
I'm quite surprised that this big update was not secured by correct depends/breaks. I know we are beta-testers, I know the risks, I repair my Ubuntu alone, but anyway when some packages are pushed in release, they shouldn't depend on some others waiting in proposed without any conflict prompted.

From a positive POV now : if an Ubuntu dev read this topic, could it be possible to briefly explain what is the Nvidia plan in Ubuntu ? What will replace prime-select to switch GPU ?

---

### Post by mc4man on 2018-02-28
> **fthx said:**
> 
From a positive POV now : if an Ubuntu dev read this topic, could it be possible to briefly explain what is the Nvidia plan in Ubuntu ? What will replace prime-select to switch GPU ?
Maybe file a bug report & possibly that question will be answered.

---

### Post by fthx on 2018-03-05
So, the situation that *I* do experience running latest nvidia-390 and gnome*-3.27.9x packages from proposed :
- nouveau : ok, GDM has two options X and Wayland, the X session shows some graphical glitches during GNOME loading, GNOME offers a right-click option to launch an app with dGPU (still very poooooor performances)
- nvidia-390 : ok, GDM has no options, the X session is booted but does not offer any GPU switching, I have to use Nvidia GPU

Well, I still do not understand:
- why the Wayland session was available running nvidia-390 and no more is
- how to use Intel iGPU running nvidia-390

I don't know what is pending, if someone knows, please share :-) .

---

### Post by #&amp;thj^% on 2018-03-05
> **fthx said:**
> 
I don't know what is pending, if someone knows, please share :-) .
I don't think any of us know what will be in regards to Prime-Select>>>Currently Broken.
For now you either use Nvidia or to use your Intel GPU remove the nvidia driver.
Sorry best "I" can offer ATM>>>but i have heard no news for nvidia-prime at all, and that not a promising out look.
BTW nvidia-prime is not written by Nvidia it is a Canonical addition.
Regards

---

### Post by mc4man on 2018-03-05
> **1fallen said:**
> I don't think any of us know what will be in regards to Prime-Select>>>Currently Broken.
For now you either use Nvidia or to use your Intel GPU remove the nvidia driver.
Sorry best "I" can offer ATM>>>but i have heard no news for nvidia-prime at all, and that not a promising out look.
BTW nvidia-prime is not written by Nvidia it is a Canonical addition.
Regards
For all of a day or so I was able to - 
log into X > nvidia driver
log into wayland > intel driver
So that meant something pretty simple was able to switch gpu's/drivers in use.
I even filed a bug based on that happening.., [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-390/+bug/1753127](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-390/+bug/1753127)

Then all of a sudden the wayland option in the login greeter disappeared (why, no idea.. or maybe why the option was present, really no idea.

To me the bigger issue is that Ubunt's combo of nvidia driver (3.90.25) & kernel (4.15) prevent the use of Prime Sync
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-390/+bug/1752739](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-390/+bug/1752739)

---

### Post by #&amp;thj^% on 2018-03-05
> **mc4man said:**
> For all of a day or so I was able to - 
log into X > nvidia driver
log into wayland > intel driver
So that meant something pretty simple was able to switch gpu's/drivers in use.
I even filed a bug based on that happening.., [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-390/+bug/1753127](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-390/+bug/1753127)

Interesting>>>I wish I had a hybrid here to play with (Or maybe not ;)). Here I was unsuccessful in wayland with nvidia>>bounce back to login.
Tried in GDM and Lightdm.
> **mc4man said:**
> 
To me the bigger issue is that Ubunt's combo of nvidia driver (3.90.25) & kernel (4.15) prevent the use of Prime Sync
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-390/+bug/1752739](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-390/+bug/1752739)
+1 and I know how irritating these things can become to us the users.

---

### Post by mc4man on 2018-03-05
> **1fallen said:**
> Interesting>>>I wish I had a hybrid here to play with (Or maybe not ;)). Here I was unsuccessful in wayland with nvidia>>bounce back to login.
Tried in GDM and Lightdm.

+1 and I know how irritating these things can become to us the users.
My impression was that Desktop nvidia users should be able to get a working wayland session thru eglstreams if nvidia_drm kms was enabled . I guess that's no longer the case? ( well certainly you won't get kms now.., but previously with kernel 4.13 you could.

---

### Post by #&amp;thj^% on 2018-03-05
> **mc4man said:**
> My impression was that Desktop nvidia users should be able to get a working wayland session thru eglstreams if nvidia_drm kms was enabled . I guess that's no longer the case? ( well certainly you won't get kms now.., but previously with kernel 4.13 you could.
Yep just wasted 30 minutes trying with "nvidia_drm kms" and a few other tweaks but the same old bounce back:lolflag:
I'll wait a bit to see if any changes come about. Thanks mc4man.

---

### Post by fthx on 2018-03-12
Any news about Optimus GPU switching support running Nvidia 390 ?

---

### Post by mc4man on 2018-03-14
> **fthx said:**
> Any news about Optimus GPU switching support running Nvidia 390 ?

Here's quote from email concerning bug I have on prime sync from Alberto Milone 
```
prime-select is not supposed to work yet, and I am working on it. It is
a separate problem.

As for the main problem, I am going to fix it by patching the nvidia driver for Linux 4.15.
 
```

---

### Post by fthx on 2018-03-15
ok thanks, great to hope for better days (prime select+sync).

---

### Post by fthx on 2018-03-15
[https://lists.ubuntu.com/archives/bionic-changes/2018-March/009954.html](https://lists.ubuntu.com/archives/bionic-changes/2018-March/009954.html)

---

### Post by mc4man on 2018-03-15
> **fthx said:**
> [https://lists.ubuntu.com/archives/bionic-changes/2018-March/009954.html](https://lists.ubuntu.com/archives/bionic-changes/2018-March/009954.html)
The patch works but, at least here, there are some issues.
If I version, i.e
options nvidia_390_drm modeset=1
Then nothing happens, kms is not enabled for nvidia

If I don't version, 
options nvidia_drm modeset=1
Then modeset for nvidia_drm is enabled but no boot in gdm

If however I switch to lightdm then it boots & prime sync is realized..

Edit: regarding gdm, forget that, based on this page, doesn't work
[http://us.download.nvidia.com/XFree86/Linux-x86_64/390.25/README/kms.html](http://us.download.nvidia.com/XFree86/Linux-x86_64/390.25/README/kms.html)

---

### Post by fthx on 2018-03-15
I tried to add a module option in nvidia file in /etc/modprobe.d, no sync.
I added **nvidia-drm.modeset=1** in grub boot options and I get sync on both X and (appearing) Wayland sessions. No problems with GDM here.

Note that the sync is very easy to see in GNOME : overview and desktops dock discovering animation shows what's running... :-)

Me : Quadro M1000M

---

### Post by mc4man on 2018-03-15
> **fthx said:**
> I tried to add a module option in nvidia file in /etc/modprobe.d, no sync.
I added **nvidia-drm.modeset=1** in grub boot options and I get sync on both X and (appearing) Wayland sessions. No problems with GDM here.

Note that the sync is very easy to see in GNOME : overview and desktops dock discovering animation shows what's running... :-)

Me : Quadro M1000M

Edit: nothing to do with how kms is enabled, gdm3 won't work on some hardware

---

### Post by fthx on 2018-03-15
Uh oh, as previously, the Wayland session runs Intel, not Nvidia...

---

### Post by mc4man on 2018-03-15
> **fthx said:**
> Uh oh, as previously, the Wayland session runs Intel, not Nvidia...

That's what I saw a couple of weeks ago, then after a few days the wayland session option disappeared. 
Will have to try again on fresh install. 
Sorta  gives a means to switch drivers, obviously not ideal. 
Wayland, nvidia & Optimus hardware seems to be a bit of a pipe dream

---

### Post by fthx on 2018-03-15
I checked powertop and I get roughly 10 W (idle) with Wayland session. When the Nvidia GPU is really disabled, I get less than 4 W (idle).

---

### Post by mc4man on 2018-03-15
Did a fresh install, updated, installed nvidia-driver-390
1. as soon as nvidia driver is detected the option for wayland is removed
2. gdm3 does not work with nvidia_drm/kms, doesn't matter how it's enabled
3. lightdm works fine, kms is enabled for nvidia_drm, prime sync works

So clearly different hardware is going to be treated differently, on this machine NVIDIA GK107M [GeForce GT 755M]

For me easiest way is to just create a file in /etc/modprobe.d, never needs any attention, is ignored if nvidia drivers are removed.

For info sake - 
```
sudo nano /etc/modprobe.d/zz-nvidia-modeset.conf
```
insert
```
options nvidia_drm modeset=1
```
save, exit nano , run
```
sudo update-initramfs -u
```
reboot with lightdm (- at least for my nvidia chipset

---

### Post by mc4man on 2018-03-16
na

---

### Post by fthx on 2018-03-21
Bump !

[https://bugs.launchpad.net/ubuntu/+source/nvidia-prime/+bug/1757180](https://bugs.launchpad.net/ubuntu/+source/nvidia-prime/+bug/1757180)
[https://lists.ubuntu.com/archives/bionic-changes/2018-March/010643.html](https://lists.ubuntu.com/archives/bionic-changes/2018-March/010643.html)

---

### Post by mc4man on 2018-03-21
> **fthx said:**
> Bump !

[https://bugs.launchpad.net/ubuntu/+source/nvidia-prime/+bug/1757180](https://bugs.launchpad.net/ubuntu/+source/nvidia-prime/+bug/1757180)
[https://lists.ubuntu.com/archives/bionic-changes/2018-March/010643.html](https://lists.ubuntu.com/archives/bionic-changes/2018-March/010643.html)
Yeah, it now works thru prime-select, not yet in nvidia-settings
The end result will be a longer time to switch, the method takes a bit longer & will require a reboot. 
gdm3 previously required a reboot so nothing new to those users, lightdm did thru a log out/in, likely no more..

---

### Post by #&amp;thj^% on 2018-03-21
> **mc4man said:**
> Yeah, it now works thru prime-select, not yet in nvidia-settings
The end result will be a longer time to switch, the method takes a bit longer & will require a reboot. 
gdm3 previously required a reboot so nothing new to those users, lightdm did thru a log out/in, likely no more..

+1 ;)
He just released the fix about 40 mins ago.
It seems to be now working on my specs:
```
 apt policy nvidia-prime
nvidia-prime:
  Installed: 0.8.6
  Candidate: 0.8.6
  Version table:
 *** 0.8.6 500
        500 http://us.archive.ubuntu.com/ubuntu bionic-proposed/main amd64 Packages
        500 http://us.archive.ubuntu.com/ubuntu bionic-proposed/main i386 Packages
        100 /var/lib/dpkg/status
     0.8.5 500
        500 http://us.archive.ubuntu.com/ubuntu bionic/main amd64 Packages

```
Hardware:
```
 inxi -xxx -G
Graphics:  Card-1: Intel HD Graphics 530 bus-ID: 00:02.0 chip-ID: 8086:1912
           Card-2: NVIDIA GF114 [GeForce GTX 560 Ti]
           bus-ID: 01:00.0 chip-ID: 10de:1200
           Display Server: x11 (X.Org 1.19.6 )
           drivers: modesetting (unloaded: fbdev,vesa)
           Resolution: 1920x1080@60.00hz
           OpenGL: renderer: Mesa DRI Intel HD Graphics 530 (Skylake GT2)
           version: 4.5 Mesa 18.0.0-rc4 (compat-v: 3.0) Direct Render: Yes


```
And Wayland:
```
pinxi -xxx -G
Graphics:
  Card-1: Intel HD Graphics 530 driver: i915 v: kernel bus ID: 00:02.0 
  chip ID: 8086:1912 
  Card-2: NVIDIA GF114 [GeForce GTX 560 Ti] driver: N/A bus ID: 01:00.0 
  chip ID: 10de:1200 
 **_ Display Server: wayland_** (X.Org 1.19.6) driver: modesetting 
  unloaded: fbdev,vesa,nvidia resolution: 1920x1080~60Hz 
  OpenGL: renderer: Mesa DRI Intel HD Graphics 530 (Skylake GT2) 
  version: 4.5 Mesa 18.0.0-rc4 compat-v: 3.0 direct render: Yes 

```
Driver:
```
 apt policy nvidia-390
nvidia-390:
  Installed: 390.42-0ubuntu1+gpu18.04.1
  Candidate: 390.42-0ubuntu1+gpu18.04.1
  Version table:
 *** 390.42-0ubuntu1+gpu18.04.1 500
        500 http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu bionic/main amd64 Packages
        100 /var/lib/dpkg/status

```

---

### Post by fthx on 2018-03-21
Well, it seems to be fine, Xorg or Wayland with nvidia-drm.modeset=1 in grub.

There is one small issue : I use TLP for power settings and I have to remove nvidia & nouveau from (default) excluded PM modules to really offload the Nvidia GPU. If not, powertop shows high power usage (~12 W) because the Nvidia GPU is powered on. Once the trick done, I get ~3.7 W running Wayland and ~4 W running Xorg, with no radio & lowest brightness. Quite normal (~ NV 384 from Artful) & good for a Xeon CPU.

---

### Post by fthx on 2018-03-22
Ok :
[https://lists.ubuntu.com/archives/bionic-changes/2018-March/010751.html](https://lists.ubuntu.com/archives/bionic-changes/2018-March/010751.html)
[https://lists.ubuntu.com/archives/bionic-changes/2018-March/010756.html](https://lists.ubuntu.com/archives/bionic-changes/2018-March/010756.html)

I was running Intel and no prime option was displayed. Once I prime-selected Nvidia and rebooted, all was fine.
The nvidia-settings deserves a better appeareance during GPU switch : since the change takes now a few seconds, it would be nice to display a progress bar or a running cursor.
BUT it works !

---

### Post by mc4man on 2018-03-22
> **fthx said:**
> Ok :



The nvidia-settings deserves a better appeareance during GPU switch : since the change takes now a few seconds, it would be nice to display a progress bar or a running cursor.

They better fix that, give a clear example here of possible issue

[https://bugs.launchpad.net/ubuntu/+source/nvidia-prime/+bug/1758214](https://bugs.launchpad.net/ubuntu/+source/nvidia-prime/+bug/1758214)

---

### Post by donp1217 on 2018-03-26
> **mc4man said:**
> Did a fresh install, updated, installed nvidia-driver-390
1. as soon as nvidia driver is detected the option for wayland is removed
2. gdm3 does not work with nvidia_drm/kms, doesn't matter how it's enabled
3. lightdm works fine, kms is enabled for nvidia_drm, prime sync works

So clearly different hardware is going to be treated differently, on this machine NVIDIA GK107M [GeForce GT 755M]

For me easiest way is to just create a file in /etc/modprobe.d, never needs any attention, is ignored if nvidia drivers are removed.

For info sake - 
```
sudo nano /etc/modprobe.d/zz-nvidia-modeset.conf
```
insert
```
options nvidia_drm modeset=1
```
save, exit nano , run
```
sudo update-initramfs -u
```
reboot with lightdm (- at least for my nvidia chipset

How do you switch back to LightDM in 18.04? With GDM and the Nvidia 390 drivers I have massive screen tearing. If I set options nvidia_drm modeset=1 to cure the screen tearing as I did in previous versions of Ubuntu, Gnome won't load. Will switching to LightDM fix this?

---

### Post by fthx on 2018-03-26
did you try to include the modeset boot option in grub rather than in nvidia conf file ?

---

### Post by donp1217 on 2018-03-26
> **fthx said:**
> did you try to include the modeset boot option in grub rather than in nvidia conf file ?

No, I haven't tried that. Would the correct line to insert into the grub file be:

GRUB_CMDLINE_LINUX="nvidia-drm.modeset=1"

?

---

### Post by mc4man on 2018-03-26
> **donp1217 said:**
> How do you switch back to LightDM in 18.04? With GDM and the Nvidia 390 drivers I have massive screen tearing. If I set options nvidia_drm modeset=1 to cure the screen tearing as I did in previous versions of Ubuntu, Gnome won't load. Will switching to LightDM fix this?

Just install lightdm, you'll get a popup to choose which one to use.
If already installed then go 
```
sudo dpkg-reconfigure lightdm
```

---

### Post by mc4man on 2018-03-26
What happens is gnome-shell crashes at the log in/lock screen when nvidia_drm (kms) is enabled with GeForce m cards.
Best option is to switch to lightdm, an alternate is to autologin, though in that case one can't log out or use the lockscreen..

---

### Post by donp1217 on 2018-03-26
> **mc4man said:**
> Just install lightdm, you'll get a popup to choose which one to use.
If already installed then go 
```
sudo dpkg-reconfigure lightdm
```

Thank you. Installing lightdm and adding the line "GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nvidia-drm.modeset=1"" to my /etc/default/grub file and updating grub got me working with the Nvidia 390 driver tear free.

---

### Post by andrw0830 on 2018-03-28
Hey just wanted to let you know. The Graphics PPA released Nvidia 390.48 driver. Installing with nvidia-prime though doesn't give you the option to switch back to Nvidia. With 390.42, I used prime-select to switch to Intel but since the update to 390.48, I can no longer switch to Nvidia with error that 'profile Nvidia is already set'. Is anyone else experiencing the same issue? I might have to get rid of that PPA and just use Ubuntu's source for Nvidia since I believe that still has 390.42.

---

### Post by mc4man on 2018-03-28
> **andrw0830 said:**
> Hey just wanted to let you know. The Graphics PPA released Nvidia 390.48 driver. Installing with nvidia-prime though doesn't give you the option to switch back to Nvidia. With 390.42, I used prime-select to switch to Intel but since the update to 390.48, I can no longer switch to Nvidia with error that 'profile Nvidia is already set'. Is anyone else experiencing the same issue? I might have to get rid of that PPA and just use Ubuntu's source for Nvidia since I believe that still has 390.42.
Did you already try to switch thru nvidia-settings > prime profiles? and if so did you let the process complete? (takes 15-20 sec, no indication it's doing anything until done..

---

### Post by andrw0830 on 2018-03-29
> **mc4man said:**
> Did you already try to switch thru nvidia-settings > prime profiles? and if so did you let the process complete? (takes 15-20 sec, no indication it's doing anything until done..

nvidia-settings doesn't have prime profiles listed. If I try to type in sudo prime-select intel, even though Intel is already active, it says that drivers don't support prime. So there is a conflict somewhere as Prime thinks Nvidia profile is active when my Intel card is in fact. I tried to go back to 390.42 using official Ubuntu nvidia driver and prime still doesn't work. I tried purging nvidia* and libnvidia* files and reinstalling to no avail. Whatever prime 0.8.6 did to switch to Intel, seem to have made Intel stay the default Graphics card with no way now to switch back to Nvidia. 

When I do a new install of nvidia with nvidia-prime, I do get a error during build as the libnvidia-decode and encode:i386 packages say can't be configured. I had to run sudo apt-get -f install to force it to install those dependencies. Is there anything else I can do? The Graphics PPA screwed up my computer and removing that PPA is now not helping.

---

### Post by mc4man on 2018-03-29
> **andrw0830 said:**
> nvidia-settings doesn't have prime profiles listed. If I try to type in sudo prime-select intel, even though Intel is already active, it says that drivers don't support prime. So there is a conflict somewhere as Prime thinks Nvidia profile is active when my Intel card is in fact. I tried to go back to 390.42 using official Ubuntu nvidia driver and prime still doesn't work. I tried purging nvidia* and libnvidia* files and reinstalling to no avail. Whatever prime 0.8.6 did to switch to Intel, seem to have made Intel stay the default Graphics card with no way now to switch back to Nvidia. 

When I do a new install of nvidia with nvidia-prime, I do get a error during build as the libnvidia-decode and encode:i386 packages say can't be configured. I had to run sudo apt-get -f install to force it to install those dependencies. Is there anything else I can do? The Graphics PPA screwed up my computer and removing that PPA is now not helping.
If i was you I'd just do a fresh install & move on. Clearly some things with nvidia drivers can get screwed up & become hard if not impossible to fix.

---

### Post by andrw0830 on 2018-03-29
> **mc4man said:**
> If i was you I'd just do a fresh install & move on. Clearly some things with nvidia drivers can get screwed up & become hard if not impossible to fix.

I finally figured it out. When ever I tried doing a clean install of nvidia-390, I noticed that it was trying to install i386 packages for my amd64 system. I was able to remove the i386 architecture from using dpkg. While that fixed the install of 'sudo apt-get install nvidia-390 nvidia-prime', I still didn't have the Nvidia card drivers loaded when I rebooted. I looked in /etc/mobprobe.d/ folder and saw there was a blacklist-nvidia.conf file. Removed that and updated the kernel 'sudo update-initramfs -u' and rebooted and Nvidia drivers loaded properly and now I have Prime Profiles showing up in nvidia-settings. I don't know how it got messed up (maybe using prime-select while on 390.42 when nvidia-settings was broken), but now it is working like it should. Thanks everyone!

---

### Post by vijayk-kannan on 2018-03-31
For me I am not able to load nvidia driver eventhough I login to x , if I select nvidia through prime-select command looping at boot :-( , My system MSI PE60 7RD , 250GB SSD,, Ubuntu 17.10 Nvidia driver 390, showing processor off when I do nvida-smi , nvidia settings doesnt show prime profiles ? Could you please help me on this ?

---

### Post by cruzer001 on 2018-04-11
Package: nvidia-dkms-390

It's been a couple of months since I tried running a nvidia driver, I want to give the 390 driver a try even though I expect its still not usable.

Why does the 390 driver have its own dkms package?  Will there be any conflicts with the the dkms package I currently run from the repositories (running virtualbox)?

---

### Post by stephen-c1udulq on 2018-04-11
Same here, I am unable to switch to nvidia adapter on my laptop since installing nvidia-driver-390.  Updated to bionic and lost graphics output. Oops!

Intel works but had to manually run prime-select at the console.  Switching to nvidia yields:

```
# sudo prime-select nvidia
Info: selecting the nvidia profile
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.15.0-13-generic
Found initrd image: /boot/initrd.img-4.15.0-13-generic
Found linux image: /boot/vmlinuz-4.13.0-38-generic
Found initrd image: /boot/initrd.img-4.13.0-38-generic
Found linux image: /boot/vmlinuz-4.13.0-37-generic
Found initrd image: /boot/initrd.img-4.13.0-37-generic
Found linux image: /boot/vmlinuz-4.13.0-36-generic
Found initrd image: /boot/initrd.img-4.13.0-36-generic
Adding boot menu entry for EFI firmware configuration
done
Traceback (most recent call last):
  File "/usr/bin/prime-select", line 294, in <module>
    switcher.enable_profile(arg)
  File "/usr/bin/prime-select", line 114, in enable_profile
    self._enable_nvidia()
  File "/usr/bin/prime-select", line 150, in _enable_nvidia
    os.unlink(self._blacklist_file)
FileNotFoundError: [Errno 2] No such file or directory: '/etc/modprobe.d/blacklist-nvidia.conf'
```

---

### Post by mc4man on 2018-04-11
> **stephen-c1udulq said:**
> Same here, I am unable to switch to nvidia adapter on my laptop since installing nvidia-driver-390.  Updated to bionic and lost graphics output. Oops!

Intel works but had to manually run prime-select at the console.  Switching to nvidia yields:

```
# sudo prime-select nvidia
Info: selecting the nvidia profile
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.15.0-13-generic
Found initrd image: /boot/initrd.img-4.15.0-13-generic
Found linux image: /boot/vmlinuz-4.13.0-38-generic
Found initrd image: /boot/initrd.img-4.13.0-38-generic
Found linux image: /boot/vmlinuz-4.13.0-37-generic
Found initrd image: /boot/initrd.img-4.13.0-37-generic
Found linux image: /boot/vmlinuz-4.13.0-36-generic
Found initrd image: /boot/initrd.img-4.13.0-36-generic
Adding boot menu entry for EFI firmware configuration
done
Traceback (most recent call last):
  File "/usr/bin/prime-select", line 294, in <module>
    switcher.enable_profile(arg)
  File "/usr/bin/prime-select", line 114, in enable_profile
    self._enable_nvidia()
  File "/usr/bin/prime-select", line 150, in _enable_nvidia
    os.unlink(self._blacklist_file)
FileNotFoundError: [Errno 2] No such file or directory: '/etc/modprobe.d/blacklist-nvidia.conf'
```

you can likely solve using 1 of  2 ways
1. remove most of nvidia packages, reboot, then re-install nvidia-driver-390. sudo apt purge nvidia* should suffice, after that you could run sudo apt autoremove if desired.
or
2. go 
```
sudo nano /etc/modprobe.d/blacklist-nvidia.conf
```
Paste this in (though probably just creating the file would be good enough..
```
# Do not modify
# This file was generated by nvidia-prime
blacklist nvidia
blacklist nvidia-drm
blacklist nvidia-modeset
alias nvidia off
alias nvidia-drm off
alias nvidia-modeset off
```
Then save & exit nano (ctrl+o enter ctrl+x
follow with 
```
sudo prime-select nvidia
```

---

### Post by fargoth on 2018-06-05
Does prime-select still requires reboot (as opposed to simple logout/login in 17.10 or 16.04)? Are there any plans to solve this?

If it's not going to be fixed, I'll have to downgrade to 16.04 from my 17.10.

---

### Post by fargoth on 2018-06-05
Found some sort of a solution:

[https://github.com/matthieugras/Prime-Ubuntu-18.04](https://github.com/matthieugras/Prime-Ubuntu-18.04)

---

### Post by slickymaster on 2018-06-05
18.04 is no longer in development. Thread closed.

---

