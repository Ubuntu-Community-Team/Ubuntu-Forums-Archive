---
title: "Share with us your Disco Installation/Upgrade experience"
date: 2019-04-20
forum: Ubuntu, Linux and OS Chat
---

### Post by cariboo on 2019-04-20
Disco Dingo was released April 18 2019, so it's time for a new poll. Please tell us about your experience upgrading, or doing a fresh install of Disco.

Keep in mind that this thread is only for your experience, if you are having problems, please create a thread in the support forums.

The previous poll can be found here:

[https://ubuntuforums.org/showthread.php?t=2417102](https://ubuntuforums.org/showthread.php?t=2417102)

---

### Post by Frogs Hair on 2019-04-20
Been using a bug-free Budgie since March.
 
```
System:
  Host: dual Kernel: 5.0.0-13-generic x86_64 bits: 64 Desktop: Budgie 10.5 
  Distro: Ubuntu 19.04 (Disco Dingo) 
CPU:
  Topology: Quad Core model: AMD Athlon II X4 645 bits: 64 type: MCP 
  L2 cache: 2048 KiB 
  Speed: 800 MHz min/max: 800/3100 MHz Core speeds (MHz): 1: 800 2: 800 
  3: 800 4: 800 
Graphics:
  Device-1: NVIDIA GF108 [GeForce GT 730] driver: nvidia v: 390.116 
  Display: x11 server: X.Org 1.20.4 driver: nvidia 
  unloaded: fbdev,modesetting,nouveau,vesa resolution: 1680x1050~60Hz 
  OpenGL: renderer: GeForce GT 730/PCIe/SSE2 v: 4.6.0 NVIDIA 390.116 

```

---

### Post by oldos2er on 2019-04-20
Upgrade ran like a hot knife through butter; smooth, relatively fast, and successful. Xubuntu, FWIW.

---

### Post by Dennis N on 2019-04-21
I did 3 upgrades:

1 x Ubuntu 18.10 uefi --> Ubuntu 19.04
1 x Ubuntu 18.10 bios --> Ubuntu 19.04
1 x Xubuntu 18.10 uefi --> Xubuntu 19.04

All were in a QEMU/KVM virtual machine and upgraded with the Software Updater tool. One package in both the Ubuntu upgrades failed to install (the same one in each), but the Updater notified that it would run dpkg --configure -a and apparently that took care of it. In Xubuntu, there were no glitches.

Three gnome shell extensions needed updating; another required replacement by a similar extension. Except for that, everything is as it was before, so no time had to be spent installing software and customizing the installations. I am happy with the results.

---

### Post by Erik1984 on 2019-04-29
Seemed to work. Sadly I never not get a nice graphical upgrade prompt in **[COLOR=#3399ff]Kubuntu [/COLOR]**18.10 although the software sources/update settings seemed right. Not a major issue as **do-release-upgrade** did the trick just fine (so that's why I still consider the upgrade itself as flawless). So now it's goodbye Cosmic Cuttlefish and hello Disco Dingo :P 

For Kubuntu this release seems a bit boring as in I don't notice much difference graphically. Sad thing is that Amarok is gone now, no longer in the repositories. Have to find a new default music player (KDE/Qt friendly). But that's another topic.

---

### Post by deadflowr on 2019-05-06
Upgraded.
Only issue is [lpbug]1825420[/lpbug]
The stated workaround works fine.
(Prior to reboot you need to run
```
sudo dpkg --configure -a
```
It tells you to do so.)

Other than that all is good and running fine.

---

### Post by gargarr on 2019-06-16
Recently I changed from home use of Windows/10 based OS local home computer to a flash of Ubuntu without much debian or great linux experience/knowledge.

The download from the Ubuntu site was easy to navigate and download. The instructions were easy to understand and verify the integrity of the .iso. Overall, that process went very well.

Then during the installation part, that process was very easy to understand and maneuver with the very basic understand I had on the entire OS. Following the provided on screen instructions, I was able to do all the proper and recommended install and security best practices.

Being I don't have any great linux user experience background, I dual use the experience by learning how to do most interactions and installs via the CLi while also using GUI to help supplement the very many requirements I am doing to learn how to best use this system.

Also, the install I chose was not to dual-boot. I figured, if I was going to learn Linux then I am going to use it 100% of the time.

Thanks for your hard work! I am really enjoying the experience. :)

---

### Post by kpatz on 2019-06-16
I installed 19.04 in a fresh Virtualbox VM a few weeks ago, have played some with it, no issues so far that I recall.  If I had any at installation I've long since gotten past them and forgotten what they were, but AFAIK it was a smooth install.

I only install non-LTS releases in VMs to play with... I use LTS releases for physical boxes.

---

