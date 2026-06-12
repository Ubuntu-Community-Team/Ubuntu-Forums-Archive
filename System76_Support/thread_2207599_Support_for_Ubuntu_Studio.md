---
title: "Support for Ubuntu Studio?"
date: 2014-02-24
forum: System76 Support
---

### Post by skyemoor on 2014-02-24
I'm currently an Ubuntu Studio user looking for a new laptop, and System76 appears to be a natural first place to look (as I prefer small businesses for a host of reasons).

Is anyone running Studio on their System76 laptop? If so, any comments/issues?

What is the level of support at System76 for Ubuntu Studio, especially newer versions such as 13.10? I'm happy with 32 bit, though don't mind moving to 64 bit if I have to.

---

### Post by isantop on 2014-02-24
You shouldn't have too many issues running Ubuntu Studio. You may want to consider adding the relevant Ubuntu Studio packages to your system instead of installing it outright, as that would be much faster.

We do strongly recommend installing 13.10, as it's the fully supported version. I'd also advise for 64-bit, to take advantage of any extra RAM you have.

---

### Post by nico11 on 2014-02-25
I don't use Ubuntu Studio but I do use some packages such as OpenShot, Audacity, Calibre, libreoffice etc. without any problems. I especiialy like OpenShot on my Gazelle laptop as this is way faster than on my older laptop. Because I ordered mine with 16Gb internal memory and the latest quadcore i7 processor.

---

### Post by skyemoor on 2014-02-25
Thanks Ian, Studio uses a [low-latency kernel]("https://help.ubuntu.com/community/UbuntuStudio/RealTimeKernel"), and a lightweight interface (XFCE) in order to avoid glitches in audio processing, aside from all of the components that come pre-configured.


[INDENT]Real Time Kernel - Ubuntu Studio uses the Ingo Molnar PREEMPT patched real-time kernel (for more information about the real-time kernel, take a look at the RTWiki FAQ). This helps to reduce the amount of latency, which is extremely beneficial for audio work. The low levels of latency that can be achieved in Linux with the real-time kernel can also surpass those available under Windows and Mac.

System Configuration - The Ubuntu Studio team has already configured the Ubuntu Studio system to help maximize the real-time kernel. The user is included in the audio group and the limits.conf file is specifically configured.

JACK Sound System - Along with the ubiquitous Pulse Audio sound server, the powerful JACK sound server is also included in Ubuntu Studio. Both are already configured to work well together. [/INDENT]

This excellent review hits the high points - [http://desktoplinuxreviews.com/ubuntu-reviews/ubuntu-studio-13-10/](http://desktoplinuxreviews.com/ubuntu-reviews/ubuntu-studio-13-10/)

Now with that in mind, do you see any risk associated with a person loading Ubuntu Studio on a System76 laptop? If so, what? And what would be the level of support from System76?

---

### Post by cub on 2014-02-26
As already recommended in the thread by System76, add the applications you want to the existing installation.

---

### Post by skyemoor on 2014-02-26
cub, audio applications require the low-latency kernel, as noted above. Did you yourself take the approach you recommended with ardour and try multi-track recording and midi? Are you using Unity and the standard kernel?

---

### Post by cub on 2014-02-27
> **skyemoor said:**
> cub, audio applications require the low-latency kernel, as noted above. Did you yourself take the approach you recommended with ardour and try multi-track recording and midi? Are you using Unity and the standard kernel?
I have done before. I don't have any System76 hardware though. But as Ubuntu Studio only use things that are in the standard repos you can add whatever you need to your pre-installed Ubuntu, including the low latency kernel. It's easier to just install fresh from the Ubuntu Studio DVD but if that proves an issue with your System76 support I would recommend to add the applications and kernel you want to use.

---

### Post by cub on 2014-02-27
To get all you need for audio work on a standard Ubuntu do:
```
sudo apt-get update && sudo apt-get dist-upgrade && sudo apt-get install ubuntustudio-audio linux-lowlatency && sudo usermod -a -G audio $USER
```

---

