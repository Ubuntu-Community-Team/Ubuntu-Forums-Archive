---
title: "Ubuntu Studio 11.04 sound issue"
date: 2011-08-17
forum: Ubuntu Studio
---

### Post by chkneater on 2011-08-17
I have a problem with my sound after install UbuntuStudio 11.04, there is no sound applet!!  I can't find any sound controls and anytime I try to use Jack or audacity, they work fine but there is no sound at all, and I've checked ports and stuff.  Is there an applet I can download to sit on the task bar or am I missing one that is already there?

---

### Post by jejeman on 2011-08-17
Add on panel: indicator applet

---

### Post by chkneater on 2011-08-17
thanks alot, i was able to find correct one out of three indicator applets that had the volume control, but now I'm having issues getting audio to work on any sound player like audacious.

---

### Post by jejeman on 2011-08-17
Now.
What is youre soundcard, and sound system you are trying (pulse, jack)?
Close all audio related programs and issue following commands, and give us back outputs.
```
lspci |grep Audio
```
```
aplay -l
```

---

### Post by chkneater on 2011-08-17
lspci | grep Audio lists my video card ? instead of my sound card which is a new card.  Aplay says "no soundcards found..."

I had a similar issue when I got this card at first when I was using it with 9.04 but I was a able to fix it, but I don't remember what I did and I don't think that it be relevant anyway. 

But yeah, I think that is the issue, it's wanting to recognize the stupid video card as the sound card.  Is there a way to correct this?

Oh, and I want to use Jack and whatever base soundsystem this distro is using Alsa, Pulse, hell I'll settle for OSS at this point!

---

### Post by jejeman on 2011-08-17
Well, that is interesting. Tell us what kind of soundcard is it, integrated? And what kind of graphic card is it, also. Is it a laptop? Do you have hdmi output? Just tell us more about your computer.
Give us the whole lspci output.
```
lspci
```

---

### Post by chkneater on 2011-08-17
The video card is an ATI radeon WITH hdmi output.

lspci: 

hellkiller@hellkiller:~$ lspci
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:0f.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
02:00.0 VGA compatible controller: ATI Technologies Inc Cedar PRO [Radeon HD 5450]
02:00.1 Audio device: ATI Technologies Inc Manhattan HDMI Audio [Mobility Radeon HD 5000 Series]
03:0a.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
hellkiller@hellkiller:~$ 


Notice those last two lines? It lists the audio DEVICE as the video card (the ATI) and the multimedia controller as the soundcard it SHOULD be using?

---

### Post by jejeman on 2011-08-17
You have two audio cards, both should be listed in aplay. What outputs this command
```
sudo lshw -C multimedia
```

---

### Post by chkneater on 2011-08-17
hellkiller@hellkiller:~$ lspci
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:0f.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
02:00.0 VGA compatible controller: ATI Technologies Inc Cedar PRO [Radeon HD 5450]
02:00.1 Audio device: ATI Technologies Inc Manhattan HDMI Audio [Mobility Radeon HD 5000 Series]
03:0a.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
hellkiller@hellkiller:~$

Hey fellas', felt obligated to let you know I found the solution and fixed the audio.  Here's the output of aplay -l :

hellkiller@hellkiller:~$ sudo aplay -l
[sudo] password for hellkiller: 
**** List of PLAYBACK Hardware Devices ****
card 0: CMI8738 [C-Media CMI8738], device 0: CMI8738-MC6 [C-Media PCI DAC/ADC]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: CMI8738 [C-Media CMI8738], device 1: CMI8738-MC6 [C-Media PCI 2nd DAC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CMI8738 [C-Media CMI8738], device 2: CMI8738-MC6 [C-Media PCI IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Generic [HD-Audio Generic], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


The way I fixed it was by removing the sound packages with the purge option and then reinstalling them.  I also had to reinstall the gdm package and the ubuntu-desktop and ubuntustudio-desktop packages since they have a lot of vital dependencies.  Once I reinstalled I rebooted and had sound right away.  There is a tutorial with the exact commands, I'll try to find it and post a link.

This is what I used to get my audio working with a fresh installation of 11.04 UbuntuStudio 64bit.

sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils

sudo apt-get install linux-sound-base alsa-base alsa-utils

sudo apt-get install gdm ubuntu-desktop (and also ubuntustudio-desktop if you wish)

---

