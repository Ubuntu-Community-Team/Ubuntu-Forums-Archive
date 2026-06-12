---
title: "ubuntu studio - problem with soundcard"
date: 2008-09-14
forum: Ubuntu Studio
---

### Post by igetupigetdown85 on 2008-09-14
hello all!
first of, i'm new to ubuntu studio and linux in general.
i'm using ego-sys (ESI) "Waveterminal 192x" soundcard which suppose to work with ALSA (it appears on their list of soundcards).

i have installed ubuntu-studio but it doesn't recognize my sound card.
although ubuntu studio comes with the ALSA driver (i guess??!),
when i go: SYSTEM -> preferences -> SOUND,
i can see the ALSA driver, but in DEVICE i can only see the on-board intel sound device (INTEL ICH5). couldn't find the WAVETERMINAL.
i've disabled the on-board AUDIO in BIOS and now the DEVICE line is empty!
how can i make ubuntu recognize my WAVETERMINAL 192x sound-card?

many thanks,

eyal


[sorry for double posting this thread, i post it by mistake on the "multimedia and video" forum before...]

---

### Post by paulg on 2008-09-15
According to the ALSA Matrix, [support is possible]("http://www.alsa-project.org/main/index.php/Matrix:Vendor-Ego_Sys"), but that's not the same as supported.

You might try following the directions for the Juli@ from ego sys which seems to use the same envy24ht chip. Make changes where you have a specific value for your card.
[http://www.alsa-project.org/main/index.php/Matrix:Module-ice1724](http://www.alsa-project.org/main/index.php/Matrix:Module-ice1724)

Wouldn't hurt to compile the latest ALSA drivers from source if you can't get the packaged driver to work. Can always check the ALSA mailing list for help.

---

### Post by azior on 2008-11-08
After working with ubuntu on my laptop for some time, i decided to also run ubuntu on my desktop, featuring a working onboard soundchip (yay) and the waveterminal 192L soundcard. I run into the same problem as the topicstarter.

The soundcard is detected on the system by **lspci**:
```
00:0a.0 Multimedia audio controller: VIA Technologies Inc. VT1720/24 [Envy24PT/HT] PCI Multi-Channel Audio Controller (rev 01)
	Subsystem: Device 4930:4553
	Flags: medium devsel, IRQ 18
	I/O ports at 9000 [size=32]
	I/O ports at 8800 [size=128]
	Capabilities: [80] Power Management version 1
	Kernel modules: snd-ice1724
```

The Via linux-website doesn't have a driver for this chipset. The [alsa-website]("http://www.alsa-project.org/main/index.php/Matrix:Module-ice1724") tells of a way to get this chipset to work. This however doesn't do much good in my case. The onboard chipset that worked is now not accessible (but still visible in lspci) and is removed from /proc/asounds/cards (no soundcards)

After some more fiddling I got this:
```
alsamixer: function snd_ctl_open failed for default: No such file or directory
```
Also, the /proc/asound directory is missing.

I will reinstall ubuntu to restore alsa and the onboard soundcard configuration, then I will try the last step from [this]("http://www.linuxquestions.org/questions/linux-hardware-18/sound-card-not-detected-intel-82801g-alsa-1.0.14-561009/") helpful topic. It seems so much of a hassle for this old soundcard, maybe I should buy a new card that supports linux and has great functionality.

---

