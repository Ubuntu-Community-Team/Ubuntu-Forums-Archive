---
title: "sound problem in Windows XP under kvm-qemu"
date: 2010-10-07
forum: Virtualisation
---

### Post by DatBugler on 2010-10-07
Hi,

I'm running Windows XP under kvm-qemu using AQemu on Kubuntu 10.04, and I haven't been able to get Windows to recognize there being any sound hardware. I've tried all the options for virtual sound cards, and Windows shows them all as functioning properly, but all of the sound output and input options are greyed out as having "no devices." The only similar symptom I could find anybody talking about was  *[here]("http://forums.fedoraforum.org/showthread.php?t=224479")*, but I tried the suggestions and nothing happened. Any help would be most appreciated.

According to AQemu, I'm running the VM using these options: ```
kvm -monitor stdio -smp 2 -soundhw sb16 -vga std -m
2048 -localtime -cdrom /dev/cdrom -hda /path/to/WinXP.qcow2
-boot once=c,menu=off -net nic,vlan=1,macaddr=00:59:20:cc:93:6f
-net user,vlan=1,hostname=John -smb /path/to/share -usb
-usbdevice host:1.1 -name "Windows XP"
```

My system is Kubuntu 10.04 on an HP G72-250US laptop. I have VT enabled in the BIOS, and have tried automatic, as well as "alsa" and "oss" for the sound driver in AQemu preferences. I am using AQemu 0.8.

Here's the sound interface setup for the host system:
```

me@kubuntu:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC259 Analog [ALC259 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI 0 [INTEL HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 7: INTEL HDMI 1 [INTEL HDMI 1]                                               
  Subdevices: 1/1                                                                                              
  Subdevice #0: subdevice #0

me@kubuntu:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.23.
Compiled on Oct  2 2010 for kernel 2.6.32-25-generic (SMP).
```

---

### Post by slooksterpsv on 2010-10-08
Try, for -soundhw, es1370 instead of sb16

---

### Post by DatBugler on 2010-10-08
As I noted, I've tried all the possible options for -soundhw. With all options, Windows seems to correctly recognize the card driver itself, but fails to see any sort of speakers, volume, input, midi playback etc.

---

### Post by scrooge_74 on 2010-10-09
Is the HOST OS trying to use the sound? Are you part of the sound group?

---

### Post by DatBugler on 2010-10-09
Sound works in the host OS while I am running the virtual machine, if that's what you're asking. My user is part of the "audio" group.

Do I gather from your question that it's not possible for both the virtual and the host OS to use sound at the same time?

EDIT: When I select Intel AC97 as for -soundhw, I get the KNotification that my ALC259 sound card is no longer working, and then sound dies in the host OS.

---

### Post by scrooge_74 on 2010-10-10
I had that similar issue I can either use the sound card with the Host OS or with a Guess OS not both

---

### Post by DatBugler on 2010-10-10
Hmm. You're a step ahead of me then. The thing is that even when the VM takes the sound away from the host OS, I still don't have sound in the guest OS.

---

### Post by scrooge_74 on 2010-10-11
My experiences have being with Virtualbox the past 12 months I droped Qemu after I managed to get usb ports working on Virtualbox :D

Can you check if you have any process still working on the Host that is taking over the sound card?.

XP detects the card right?

---

### Post by Velnias on 2010-10-16
This "dirty hack" works for me on Ubuntu.

[https://bugs.launchpad.net/ubuntu/+source/libvirt/+bug/591489](https://bugs.launchpad.net/ubuntu/+source/libvirt/+bug/591489)

---

