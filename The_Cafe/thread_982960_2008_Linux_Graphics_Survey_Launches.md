---
title: "2008 Linux Graphics Survey Launches"
date: 2008-11-15
forum: The Cafe
---

### Post by ssam on 2008-11-15
phoronix are run their annual linux graphics survey.

> Last year we hosted our first annual Linux Graphics Survey as really the only study that's been done to get a better understanding what the Linux community is using in their computers to fulfill their graphics needs, what their key interests are, and where they are looking for improvements. We're hosting this survey once again so we ask that between now and December 15 you take a few minutes to vote in the 2008 Linux graphics survey. 

[http://www.phoronix.com/scan.php?page=news_item&px=Njg1NA](http://www.phoronix.com/scan.php?page=news_item&px=Njg1NA)
[i forgot the link. thanks steeleyuk]

digg link as well
[http://digg.com/linux_unix/2008_Linux_Graphics_Survey_Launches](http://digg.com/linux_unix/2008_Linux_Graphics_Survey_Launches)

---

### Post by steeleyuk on 2008-11-15
[Phoronix link]("http://www.phoronix.com/scan.php?page=news_item&px=Njg1NA")

Just filled in the survey. Some of those questions might be a bit tricky for new users.

---

### Post by eternalnewbee on 2008-11-15
Hi there.
So, I went to the site to vote, but how do I find out:
1. which video driver I use  in my system.
2. Which version(s) of the X.Org server are running.
3. Which of the listed display feature(s) I use.

---

### Post by ssam on 2008-11-15
1)find the driver:
grep -i LoadModule /var/log/Xorg.0.log

one of those lines is likely to be your graphics driver. it is likely to be one of
ati, radeon, nv, nvidia, fglrx, sis, vesa, intel ...
so if you see a line

(II) LoadModule: "vesa"
then you are using
xf86-video-vesa

(if you see radeon then that is the same as ati)

2) to get your X version
dpkg -s xserver-xorg | grep -i version

Version: 1:7.4~5ubuntu3
means
X11 Release 7.4

3)which features.
TVout is if you are outputing to a TV instead of a monitor.
Multi head, is if you have more than one monitor connected
hot plug is if you add and remove monitors (or projectors) while you are logged in
i am not sure how to tell if you are using power saving

---

### Post by eternalnewbee on 2008-11-15
> 1)find the driver:
grep -i LoadModule /var/log/Xorg.0.log

one of those lines is likely to be your graphics driver. it is likely to be one of
ati, radeon, nv, nvidia, fglrx, sis, vesa, intel ...
so if you see a line

(II) LoadModule: "vesa"
then you are using
xf86-video-vesa
I'm guessing it's nvidia, right?

---

### Post by ssam on 2008-11-15
> **eternalnewbee said:**
> I'm guessing it's nvidia, right?

right :-)

---

### Post by aaaantoine on 2008-11-15
> **eternalnewbee said:**
> I'm guessing it's nvidia, right?

Looks like it, yes.

Do you know how to copy terminal contents to clipboard? (If no: Ctrl+Shift+C)

---

### Post by Sealbhach on 2008-11-15
> **steeleyuk said:**
> [Phoronix link]("http://www.phoronix.com/scan.php?page=news_item&px=Njg1NA")

Just filled in the survey. Some of those questions might be a bit tricky for new users.

Yeah, one of the options at the end of the survey is to identify yourself as a "mainstream user" but no "mainstream user" could understand some of these questions.


.

---

### Post by eternalnewbee on 2008-11-15
OK. I'm done. Thanks ssam.

---

### Post by Vadi on 2008-11-15
I'll attempt to clear up some questions as I found them a bit confusing too, but I don't have answers to all of them. Hopefully we can compile the list and modify the first post to have this information.


Which of the listed new X.Org areas are you most interested in as a end-user?

Kernel-based Mode-Setting
XvMC Improvements / VA-API / XvBA / VDPAU
DRI2
Gallium 3D
Multi-Pointer X **This is the only one I know, and this means that you can have 2 or more pointing devices being used on the screen. So you get two pointers and they behave as you'd expect from having 2 points o the screen ([http://www.youtube.com/watch?v=W0iANEFf6WI](http://www.youtube.com/watch?v=W0iANEFf6WI))**
X Input 2

Which video adapter brand(s) do you use in your Linux system(s)?

Intel
ATI / AMD
NVIDIA **Pick this if you have a Graphics by NVIDIA logo on your computer**
Matrox
VIA
SiS / XGI
Other

Which video driver(s) do you use in your Linux system(s)?

xf86-video-intel (Intel)
xf86-video-ati (ATI R100+ Open-Source Driver)
xf86-video-radeonhd (ATI R500+ Open-Source Novell Driver)
fglrx (Binary ATI Driver)
NVIDIA (Binary NVIDIA Driver) **Pick this if you have a Graphics by NVIDIA logo on your computer**
xf86-video-nv (Open-source NVIDIA driver with 2D support)
xf86-video-nouveau (Reverse-engineered NVIDIA driver)
xf86-video-via
OpenChrome (VIA OpenChrome Driver)
Unichrome (VIA Unichrome Driver)
VESA (xf86-video-vesa)
Other

How do you acquire your video driver(s) on your Linux system(s)?

From vendor's website
Building from source using git
Building from source using a released driver or snapshot
Using the distribution-supplied driver or from a package repository **Pick this if Ubuntu installed the drivers for you**
Third-party installation script
Other

Which version(s) of the X.Org server are running on your Linux system(s)?

X11 Release 6.8.x
X11 Release 6.9
X11 Release 7.0
X11 Release 7.1
X11 Release 7.2
X11 Release 7.3 **Pick this if you're on Ubuntu 8.04 "Hardy Heron"**
X11 Release 7.4 **Pick this if you're on Ubuntu 8.10 "Intrepid Ibex"**
Git Master
Other

Which of the listed display feature(s) do you use on your Linux system(s)?

TV-Out
Multiple Display Heads **Pick this if you use more than one monitor**
Output Hot-plugging
GPU Power Saving Modes (i.e. PowerPLAY, DynamicClocks) **Pick this if you're on a laptop**

How do you configure your display(s) on your Linux system(s)?

Modifying xorg.conf manually
Using a graphical utility (i.e. nvidia-settings, displayconfig-gtk, system-config-display) **Pick this if Ubuntu did this for you**
XRandR
Vendor-specific text-based utility (nvidia-xconfig or aticonfig)
Other

Do you use a compositing window manager / desktop effects?

Yes, Compiz / Compiz Fusion **Pick this if you have the cube**
Yes, KWin
Yes, Other **Pick this if you use the metacity compositing ([http://tombuntu.com/index.php/2008/11/14/metacity-compositing-effects-in-ubuntu-810/](http://tombuntu.com/index.php/2008/11/14/metacity-compositing-effects-in-ubuntu-810/))**
No **Pick this if in System - Preferences - Appearance - Visual Effects it says "None"**

What are your key interests or concerns with Linux video drivers?

Licensing / open-source **Pick this if you want nVidia and ATI drivers to be open-source**
OpenGL performance **Pick this if you want more FPS in games**
Image quality
Display-related features
2D performance
Video playback / acceleration **Pick this if you want video playing faster on your computer**
Ease of installation/maintenance
Stability **Pick this if you don't want drivers crashing**
Suspend / Hibernate **Pick this if you want suspend/hibernate to work on your laptop**
Multi-GPU Rendering
Other

Which of the below tasks do you actively use on your Linux system(s)?

Gaming
Data Visualization
Video playback
Visual Desktop Effects (i.e. Compiz "Eye Candy")
GPU Computing (i.e. CUDA)

How would you classify your usage of Linux?

Enthusiast Gamer
Professional 2D
Professional 3D
Mainstream User

---

### Post by ssam on 2008-11-15
> **Vadi said:**
> 
Kernel-based Mode-Setting
XvMC Improvements / VA-API / XvBA / VDPAU
DRI2
Gallium 3D
Multi-Pointer X **This is the only one I know, and this means that you can have 2 or more pointing devices being used on the screen. So you get two pointers and they behave as you'd expect from having 2 points o the screen ([http://www.youtube.com/watch?v=W0iANEFf6WI](http://www.youtube.com/watch?v=W0iANEFf6WI))**
X Input 2


**Kernel-based Mode-Setting**. moves more hardware control to the kernel. this allows native resolution virtual terminals (CTRL+ALT+F1), quick VT switches (no flickering at boot), simplifies multi users stuff, lets kernel display a panic message if X is running (makes debugging X crashes easier).

**XvMC Improvements / VA-API / XvBA / VDPAU**. video decoding acceleration. good for watching HD video without skipping.

**DRI2** new direct rendering. i think this solves the issue of running 3D apps at the same time as compiz.

**Gallium 3D** new acceleration stuff. a generic interface over different drivers. lets you do GPGPU (general purpose computation on GPUs) for example video decoding.

---

### Post by rebel789 on 2008-11-15
Get cool freestuff at
[http://www.prizerebel.com/index.php?r=487360](http://www.prizerebel.com/index.php?r=487360)

---

### Post by Vadi on 2008-11-15
Thanks for posting that. I remembered DRI2, but being an nVidia user that doesn't bother me (thankyfully).

---

