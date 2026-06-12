---
title: "Unusual information Ubuntu Studio 22.04"
date: 2022-06-12
forum: Ubuntu, Linux and OS Chat
---

### Post by cencar on 2022-06-12
Hi everyone,

Mx 21 install no Microphone
I'm a Linux noob and only have a limited ability with the tech. 
However, I played a hunch and ran Ubuntu Studio 22.04 off a USB and all audio worked. Internal mic, external mic & laptop speakers. 
I have been running MX linux since ver 15 on old laptops and was not concerned with mic. However, I now require to have online mic access. 
This old HP Probook runs well on MX and as a noob, I am reluctant to change distros. Also I have no use for a multimedia distro.
The data backup and different quirks that each desktop/distro require is some thing I want to avoid.

 Desktop: KDE Plasma 5.24.4 Distro: Ubuntu Studio 22.04 (Jammy Jellyfish)
Laptop System: HP product: HP ProBook 470 G3 v
  Mobo: HP model: 8102 v: KBC Version 40.73 
    UEFI: HP v: N78 Ver. 01.53 date: 11/24/2021

Audio:
  Device-1: Intel Sunrise Point-LP HD Audio driver: snd_hda_intel
  Sound Server-1: ALSA v: k5.15.0-24-lowlatency running: yes
  Sound Server-2: PulseAudio v: 15.99.1 running: yes
  Sound Server-3: PipeWire v: 0.3.48 running: yes
  
-------------------------------------------------------------------------  
  
Desktop: Xfce 4.16.0 tk: Gtk 3.24.24 info: xfce4-panel wm: xfwm 4.16.1 vt: 7 
           dm: LightDM 1.26.0 Distro: MX-21.1_x64 Wildflower October 20  2021 
           base: Debian GNU/Linux 11 (bullseye) 
Laptop System: HP product: HP ProBook 470 G3 v
           Mobo: HP model: 8102 v: KBC Version 40.73  UEFI: HP v: N78 Ver. 01.53 

Audio:     Device-1: Intel Sunrise Point-LP HD Audio vendor: Hewlett-Packard 
           driver: snd_hda_intel v: kernel alternate: snd_soc_skl bus-ID: 00:1f.3 
           chip-ID: 8086:9d70 class-ID: 0403 
           Sound Server-1: ALSA v: k5.10.0-14-amd64 running: yes 
           Sound Server-2: PulseAudio v: 14.2 running: yes 
           
The question I have would installing PipeWire on my MX Xfce work? Or would it require much more?

Thanks for any help.

---

### Post by grahammechanical on 2022-06-12
> The question I have would installing PipeWire on my MX Xfce work? Or would it require much more?

  I suggest that a better place to ask that question is in an MX Linux forum.  

PipeWire seems to be standard in Ubuntu 22.04 and may be standard in Ubuntu and its flavours from now onwards. It is not installed on your MX Linux system which is based on Debian and not on Ubuntu. It is possible that the PipeWire packages may not be available in the Debian repositories. 

PipeWire may also require other software packages (dependencies) that are also unavailable in the Debian repositories.  Is Debian going to include PipeWire in its distribution? That is a question for the Debian developers.  This is what Debian Developers say:

[https://wiki.debian.org/PipeWire](https://wiki.debian.org/PipeWire)

Regards

---

### Post by cencar on 2022-06-12
Thanks grahammechanical, for your quick response and knowledgeable information.

---

