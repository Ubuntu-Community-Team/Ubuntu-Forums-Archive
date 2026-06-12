---
title: "installed xubuntu on pang4n and sound is not working"
date: 2009-02-19
forum: System76 Support
---

### Post by mandarb777 on 2009-02-19
Hi new to posting, not too new to the forums so much helpful information here.  Additional disclaimer I have only been using ubuntu specifically and linux (started on Fedora 9) in general for about three months.

Anyways on to my problem. 
I have a pangolin performance.  I have switch around different different desktop managers (gnome-ubuntu is okay, I did not like kde (too flashy, pretty but I like simple) xubuntu is what I settled on, feels just right)
so I did a fresh install of xubuntu 32-bit intrepid everything worked fine.  I did a fresh install of xubuntu upgrading to the 64-bit version intrepid and now everything is good except it seems to missing the sound card drivers.  it beeps during boot but the volume control applet isn't showing the intel hda like before.
I have used the system 76 driver installation and I flashed the bios (updating is always good). Still nothing.

Does anyone know where I might get the sound card driver?

Thanks,
Dave

Ps. sorry for any misspelling, also panp4n not pang4n (whoops)

---

### Post by Lee_Machine on 2009-02-19
mandarb,

The driver will be there out of the box.

I'm not familiar with xfce, but lets see if I can help. In terminal type sudo alsamixer

Make sure that it's not muted. Use your up arrow to turn it up. Use the m key to toggle from mute to unmute.

Does this work?

For future use you can install xfce,gnome,and kde on one install Xfce and Gnome both use GTK+. Meaning they are very similar, and work side by side very well. 

To install xfce type sudo aptitude update && sudo aptitude install xubuntu-desktop

---

### Post by mandarb777 on 2009-02-19
I tried that and no luck.  However while scouring the nets I came across some cmds that shed some light on the situation.  I'm just not sure how to fix it now

The cmds and results

daves-pngln@DavesLaptop:~$ aplay
ALSA lib confmisc.c:768: (parse_card) cannot find card '0'
ALSA lib conf.c:3513: (_snd_config_evaluate) function snd_func_card_driver returned error: No such file or directory
ALSA lib confmisc.c:392: (snd_func_concat) error evaluating strings
ALSA lib conf.c:3513: (_snd_config_evaluate) function snd_func_concat returned error: No such file or directory
ALSA lib confmisc.c:1251: (snd_func_refer) error evaluating name
ALSA lib conf.c:3513: (_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3985: (snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2196: (snd_pcm_open_noupdate) Unknown PCM default
aplay: main:583: audio open error: No such file or directory
daves-pngln@DavesLaptop:~$ aplay -l
aplay: device_list:215: no soundcards found...
daves-pngln@DavesLaptop:~$ lspci | grep audio
daves-pngln@DavesLaptop:~$ ##### note: As you can see nothing.

Where do I go from here?
Dave

---

### Post by Lee_Machine on 2009-02-19
just to make sure the computer is not seeing your sound card try this:

sudo lspci -v

and look for this

  Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
	Subsystem: CLEVO/KAPOK Computer Device 0806
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at f4600000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
	Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [130] Root Complex Link <?>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

The above grep audio should show it, but I like to make sure.

Do you see this? The numbers might not match up.

---

### Post by mandarb777 on 2009-02-19
Okay I did that and here is what I got:

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
	Subsystem: CLEVO/KAPOK Computer Device 0806
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at f4600000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
	Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [130] Root Complex Link <?>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

so it is there but I'm still not getting any sound.  
dave

---

### Post by Lee_Machine on 2009-02-19
You can also recompile ALSA with the appropriate driver. This way with the newest release you get sound over HDMI.

But my best bet since this is a fresh install is to reinstall ubtunu (try live cd to make sure sound works) and then install xfce.

Here is how to recompile ALSA...not easy. when I did it I messed up my sound for two days until I found the issue.

[http://bugtrack.alsa-project.org/main/index.php/Matrix:Module-intel8x0#Quick_installation](http://bugtrack.alsa-project.org/main/index.php/Matrix:Module-intel8x0#Quick_installation)

---

### Post by mandarb777 on 2009-02-19
thanks much.  
Dave

---

### Post by Lee_Machine on 2009-02-19
I also found this howto sound guide

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

the the part: Getting the ALSA drivers from a *fresh* kernel

---

### Post by Lee_Machine on 2009-02-19
wow further looking at it, I find it to be quite comprehensive. Im going to bookmark that one :p

---

### Post by kwacka on 2009-05-03
Don't know if this helps but Xubuntu seems to set sound to mute at reboot.

Until I find an answer I've set xfce4-mixer to start automatically on boot so it can be set.

---

