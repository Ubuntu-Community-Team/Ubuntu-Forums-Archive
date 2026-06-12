---
title: "xvidcap record streaming audio - /dev/dsp doesn't work"
date: 2010-01-13
forum: Ubuntu Studio
---

### Post by nazariuskappertaal on 2010-01-13
I'm trying to record audio being played (streamed) from vlc (ie from my soundcard) but I don't know what to put as the audio source.

---

### Post by nazariuskappertaal on 2010-01-13
I used gtk-record my desktop, and increased my speaker volumes (in mixer) and capture/mux 1 to full. It allowed me to record the sound.

/dev/dsp = oss -> deprecated.

---

### Post by alexelprogramador on 2010-06-12
> **nazariuskappertaal said:**
> I used gtk-record my desktop, and increased my speaker volumes (in mixer) and capture/mux 1 to full. It allowed me to record the sound.

/dev/dsp = oss -> deprecated.

hello

I have the same problem

I only can record the audio from the integrated microphone of the laptop.

For example, if I want to record a sound of a web wich is streamming a video with own sound, its impossible to record the sound generating by alsa.

I dint understand what wants to mean with:

> capture/mux 1 to full 


Ill give you a video showing my audio preferences:

[http://img824.imageshack.us/img824/4292/test0000.mp4](http://img824.imageshack.us/img824/4292/test0000.mp4)

also ill give my lspci

```
 root@Sony:~# lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation G96 [GeForce 9600M GT] (rev a1)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. Device 4380 (rev 10)
05:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100
09:03.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
09:03.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
09:03.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
 
```pleasse.

help me with that issue

thanks all

):P

---

### Post by alexelprogramador on 2010-06-12
I found some information here:

[http://sourceforge.net/apps/mediawiki/xvidcap/index.php?title=Faq#Recording_sound_does_not_work_.28or_it_only_works_for_the_microphone.2C_not_application_output.29](http://sourceforge.net/apps/mediawiki/xvidcap/index.php?title=Faq#Recording_sound_does_not_work_.28or_it_only_works_for_the_microphone.2C_not_application_output.29)

a wiki of xvidcap :)

It talks about my trouble in this section:

> 
** Recording sound does not work (or it only works for the microphone, not application output)**

 It does!
The thing is: This is completely depending on your mixer settings!
What typically causes problems here is that alsa starts all volume controls set to zero. Desktop environments typically set the controls to sane or user-defined values on startup for playback. For recording that often needs to be done manually by the user. How this can be done depends on the platform and desktop system you're on, or even the audio hardware you're using.
Here's an example for alsamixergui:
- bump up "Mic"
- activate "Mic" as an input source (red dots instead of white dots)
- select "Mic Boost (+20db)" (light green instead of white speaker symbols) 
For the gnome volume control there are two sample screenshots here:
[http://www.jarre-de-the.net/computing/volume1.png](http://www.jarre-de-the.net/computing/volume1.png)
[http://www.jarre-de-the.net/computing/volume2.png](http://www.jarre-de-the.net/computing/volume2.png) 




it says that the trick is the mixer settings

Ive touched everithin in mixer, and also have diferent mixers to change the sound settings, but still the same. It only records the microphone.

---

### Post by thorgal on 2010-06-12
if you want to record what your soundcard is playing, you need some sort of loopback capability. Some audio chips have a switch available in the mixer application that would allow the output to be mixed back at the input. But not all chips provide this capability.

I recommend my alsa2jack trick but it will require a little fiddling with compiling, etc, not for everyone but it will do the job :

[http://alsa.opensrc.org/index.php/Jack_and_Loopback_device_as_Alsa-to-Jack_bridge](http://alsa.opensrc.org/index.php/Jack_and_Loopback_device_as_Alsa-to-Jack_bridge)

It also require that you run jack most of the time and in a stable way. That's not always the case, YMMV :)

---

### Post by alexelprogramador on 2010-06-14
thorgal

many many thanks for your response

ill try it and consider all your words

):P

---

### Post by thorgal on 2010-06-14
ah wait! you are talking about xvidcap ?

... mmmm, never got that to work without an OSS emulation of some kind. I would rather say that oss2jack would do the job, but I am not even sure. oss2jack is quite obsolete by nowadays standards. I kept a kernel patch to the deprecated fusd kernel module that is needed by oss2jack. But that is more complicated to make it run as you would have to compile a kernel module that you would need to patch with my home-made patch. Not even sure it would compile against 2.6.33+ kernels. But up to 2.6.32, it does.

I don't know, xvidcap is just annoying because of its use of /dev/dsp.

---

