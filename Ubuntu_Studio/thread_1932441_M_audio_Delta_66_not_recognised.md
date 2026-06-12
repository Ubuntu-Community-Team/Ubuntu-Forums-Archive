---
title: "M audio Delta 66 not recognised"
date: 2012-02-27
forum: Ubuntu Studio
---

### Post by Sylos on 2012-02-27
Hello all.

So it appears I have a little problem with getting my M audio to run. Heres the story.

The card is a Delta 66 that has been happily running for me in my old rig using ubuntu 10.04 32 bit. I have just built my new i5 rig (especially for studio work) and dropped the card into it. I then installed Ubuntu Studio 10.04 64 bit. And for some reason the card is not being recognised.

So.... heres the useful stuff:

lspci:
```
06:01.0 Multimedia audio controller: VIA Technologies Inc. ICE1712 [Envy24] PCI Multi-Channel I/O Controller (rev 02)
```

aplay -l
```
aplay: device_list:223: no soundcards found...

```


modinfo snd-ice1712
```
filename:       /lib/modules/2.6.32-38-preempt/kernel/sound/pci/ice1712/snd-ice1712.ko
license:        GPL
description:    ICEnsemble ICE1712 (Envy24)
author:         Jaroslav Kysela <perex@perex.cz>
srcversion:     4EF7DFC4AC667CA4F45B7D8
alias:          pci:v00001412d00001712sv*sd*bc*sc*i*
depends:        snd-pcm,snd,snd-i2c,snd-mpu401-uart,snd-ice17xx-ak4xxx,snd-cs8427,snd-ak4xxx-adda,snd-ac97-codec
vermagic:       2.6.32-38-preempt SMP preempt mod_unload modversions 
parm:           index:Index value for ICE1712 soundcard. (array of int)
parm:           id:ID string for ICE1712 soundcard. (array of charp)
parm:           enable:Enable ICE1712 soundcard. (array of bool)
parm:           omni:Enable Midiman M-Audio Delta Omni I/O support. (array of bool)
parm:           cs8427_timeout:Define reset timeout for cs8427 chip in msec resolution. (array of int)
parm:           model:Use the given board model. (array of charp)
parm:           dxr_enable:Enable DXR support for Terratec DMX6FIRE. (array of int)
```


dmesg |grep ICE
```
[    8.578681] ICE1712 0000:06:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    8.578923] ICE1712 0000:06:01.0: PCI INT A disabled
[    8.578928] ICE1712: probe of 0000:06:01.0 failed with error -5
[  203.117400] ICE1712 0000:06:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[  203.117441] ICE1712 0000:06:01.0: PCI INT A disabled
[  203.117447] ICE1712: probe of 0000:06:01.0 failed with error -5
```


I read in some other chatter on forums about adding the following to /etc/modprobe.d/alsa-base.conf
```
options snd-ice1712 model=delta66
```

But that has done nothing either.

If it makes any difference the MB is a Gigabyte GA-Z68AP-D3.

Im starting to get a little worried now. Although this PC is dual booted to allow a normal ubuntu install for general use I spec'd and built it for recording.... and now my beloved M-audio that did work out of the box isnt recognised properly.

Any help is gratefully recieved.

PS: I have disabled on-board sound in bios (although I actually want it enabled in the end - but first things first).

Cheers

---

### Post by gordintoronto on 2012-02-27
Have you actually shut down the computer since you disabled the on-board audio?

You might find a solution here, or on a page it links to:
[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/577872](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/577872)

---

### Post by Sylos on 2012-02-28
Hello and thanks for the reply.

I have restarted numerous times since altering the bios and the onboard is no longer shown on the os (it worked before turning it off from the BIOS).

The posts you linked to seem to be based around pulseaudio which I have removed. It also appears that the people there have already got the card recognised but are having issues with set up.


I have found a post from a single user stating that there may be a problem with my Gigabyte motherboard and using the m-audio cards. The MB uses a PCIe to PCI bridge and this user suspected that this may be the causes of his Audiophile not working. The problem is that I havent been able to find any other info to show that this is the problem.

Can anyone verify if this is the issue and whether it could be fixable?

Any other suggestions will also be gratefully received.

Cheers

---

### Post by sgx on 2012-02-28
Hi, i would shut off all non audio devices in the bios,
and install the 32 bit version. Change spci lots if possible.

Beyond that, using boot options may help, a couple are mentioned here:

[https://help.ubuntu.com/community/DebuggingIRQProblems](https://help.ubuntu.com/community/DebuggingIRQProblems).
Cheers

---

### Post by Sylos on 2012-02-28
> **sgx said:**
> Hi, i would shut off all non audio devices in the bios,
and install the 32 bit version. Change spci lots if possible.

Beyond that, using boot options may help, a couple are mentioned here:

[https://help.ubuntu.com/community/DebuggingIRQProblems](https://help.ubuntu.com/community/DebuggingIRQProblems).
Cheers

Hi sgx and thanks for the advice.

I'll give that a shot although I have tried from a live disc of varying ubuntu versions (32 and 64) and aplay -l always gives the same result. Im not sure if it would always detect it from live anyway (i've never tried before). I even tried an old Hardy custom disc I made using remstersys years ago but still the same.

I just tried another pci slot but the issue persist.

Im gonna contact Maudio and see if they have anything to say about it. Probably also contact Gigabyte and see if they can shed any light.

In the meantime any other suggestions will be much appreciated.

Cheers

EDIT: Just being reading this:

[http://www.rme-audio.de/forum/viewtopic.php?id=12432](http://www.rme-audio.de/forum/viewtopic.php?id=12432)

My buttocks just pinched the seat. MB is rev.1.0 so not up to date. I feel ill!

---

### Post by Sylos on 2012-02-28
Ok - Progress!

I removed my NVIDIA 7900GT from the PCIe x16 slot and plugged the MB into the TV via the onboard HDMI. Booted into studio and found that aplay -l registers the card and envy24control starts.

So - now to the problem of why the hell the x16 slot is hogging the whole damned PCI array.  

I have an old PCI graphics card Im gonna try. I dont have a HDMI capable monitor so I need some kind of card (and of course VGA died a long time ago). I just hope the PCI graphics doesnt hog the array as well!

If anyone has any ideas as to how to stop the nvidia from stealing it Id be happy to listen/read.

Cheers

---

### Post by gordintoronto on 2012-02-28
> **Sylos said:**
> ... pulseaudio which I have removed.

That would have been a useful fact to include in your first post.

I suggest that a vanilla installation of the latest version of Ubuntu is much more likely to produce a solution than what you have done.

---

### Post by Sylos on 2012-02-29
> **gordintoronto said:**
> That would have been a useful fact to include in your first post.

I suggest that a vanilla installation of the latest version of Ubuntu is much more likely to produce a solution than what you have done.

Hello again and thanks for the advice.

In order to make the OP more readable (and partly because I fogot somethings) I tried to keep it to a minimum of useful info. I apologise if that lead to people like yourself looking down dead end avenues trying to provide support.

Unfortunately I have also got a vanilla vetrsion of 11.10 on another partition and that has the same issue. I tried with a few Live CD's of different Buntus both 32 and 64 bit and all have the same issue.

So far the only thing to card the card recognised has been to remove the NVIDIA.

```
[    8.578681] ICE1712 0000:06:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    8.578923] ICE1712 0000:06:01.0: PCI INT A disabled
```

I dont pretend to really understand what that means but given the experience when I removed the NVIDIA I am assuming (perhaps incorrectly) that the cards are perhaps sharing the irq or the NVIDIA is blocking the Maudio from obtaining one.

Tonight I am planning to experiment with some irq boot options:

pci=routeirq
pci=biosirq

Im also going to check the irq's using

```
cat /proc/interrupts
```

And see if there are any obvious issues. As I dont really understand such things I will probably end up posting the results up here.:p

Thank you for taking the time help. It is much appreciated as I am (obviously) floundering in the dark a bit here. 

Cheers

EDIT: May also try removing the NVIDIA driver from Jockey and see if the issue occurs using the default driver.

---

### Post by Sylos on 2012-02-29
So .......

```
01:00.0 VGA compatible controller [0300]: nVidia Corporation G71 [GeForce 7900 GT/GTO] [10de:0291] (rev a1)
	Subsystem: nVidia Corporation Device [10de:042b]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 16
	Region 0: Memory at f8000000 (32-bit, non-prefetchable) [size=16M]
	Region 1: Memory at e0000000 (64-bit, prefetchable) [size=256M]
	Region 3: Memory at f9000000 (64-bit, non-prefetchable) [size=16M]
	Region 5: I/O ports at cf00 [size=128]
	[virtual] Expansion ROM at fa000000 [disabled] [size=128K]
	Capabilities: [60] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [68] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
		Address: 0000000000000000  Data: 0000
	Capabilities: [78] Express (v1) Endpoint, MSI 00
		DevCap:	MaxPayload 128 bytes, PhantFunc 0, Latency L0s <1us, L1 <4us
			ExtTag- AttnBtn- AttnInd- PwrInd- RBE- FLReset-
		DevCtl:	Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
			RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop+
			MaxPayload 128 bytes, MaxReadReq 512 bytes
		DevSta:	CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr- TransPend-
		LnkCap:	Port #0, Speed 2.5GT/s, Width x16, ASPM L0s L1, Latency L0 <1us, L1 <4us
			ClockPM- Suprise- LLActRep- BwNot-
		LnkCtl:	ASPM Disabled; RCB 128 bytes Disabled- Retrain- CommClk-
			ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
		LnkSta:	Speed 2.5GT/s, Width x16, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [128] Power Budgeting <?>
	Kernel driver in use: nvidia
	Kernel modules: nvidia-current, nvidiafb, nouveau


06:01.0 Multimedia audio controller [0401]: VIA Technologies Inc. ICE1712 [Envy24] PCI Multi-Channel I/O Controller [1412:1712] (rev 02)
	Subsystem: VIA Technologies Inc. Device [1412:d632]
	Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Interrupt: pin A routed to IRQ 16
	Region 0: I/O ports at dfc0 [size=32]
	Region 1: I/O ports at dff0 [size=16]
	Region 2: I/O ports at dfe0 [size=16]
	Region 3: I/O ports at df80 [size=64]
	Capabilities: [80] Power Management version 1
		Flags: PMEClk- DSI- D1- D2+ AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Kernel modules: snd-ice1712

```

It appears that the NVIDIA and the Maudio are both trying to use irq 16 - and I assume as the nvidia got there first poor old mr Maudio is getting shut out.

I've tried the following boot parameters:

noapic
pci=routeirq
pci=noacpi
pci=biosirq

All to no avail.

Anyone got any ideas how to mandate different irqs?

Cheers

---

### Post by sgx on 2012-02-29
nvidia 6200 passive cooled pci card is less than $50,
might be a good option.

Does lsmod list the snd_ice1712 in it's output?

does jackd start when given this command?    jackd -d alsa -r 44100

AVlinux developer uses Delta 1010s, maybe trying that distro would be an option.

[http://www.bandshed.net/AVLinux.html](http://www.bandshed.net/AVLinux.html)

---

### Post by gordintoronto on 2012-02-29
> **Sylos said:**
> It appears that the NVIDIA and the Maudio are both trying to use irq 16 - and I assume as the nvidia got there first poor old mr Maudio is getting shut out.


Congrats on figuring that out! I wish I had a silver bullet for you.

Do you have docs for the Delta 66? Any chance there is some way to change its IRQ?

Hmmm. Post number 8 in this thread might be useful:
[http://www.linuxquestions.org/questions/slackware-14/disabling-irq-16-a-879964/](http://www.linuxquestions.org/questions/slackware-14/disabling-irq-16-a-879964/)

The file name might be inaccurate, and the command needs to be preceded by sudo.

---

### Post by jejeman on 2012-03-01
> **Sylos said:**
> So .......
Anyone got any ideas how to mandate different irqs?Once the motherboards had this option in bios.

---

### Post by Sylos on 2012-03-01
> **sgx said:**
> nvidia 6200 passive cooled pci card is less than $50,
might be a good option.

Does lsmod list the snd_ice1712 in it's output?

does jackd start when given this command?    jackd -d alsa -r 44100

AVlinux developer uses Delta 1010s, maybe trying that distro would be an option.

[http://www.bandshed.net/AVLinux.html](http://www.bandshed.net/AVLinux.html)

Hello sgx.

lsmod:
```
Module                  Size  Used by
ppdev                   6471  0 
snd_ice1712            65411  0 
snd_ice17xx_ak4xxx      3155  1 snd_ice1712
snd_ak4xxx_adda         8572  2 snd_ice1712,snd_ice17xx_ak4xxx
snd_cs8427              7978  1 snd_ice1712
snd_ac97_codec        125298  1 snd_ice1712
snd_pcm_oss            41384  0 
snd_mixer_oss          16385  1 snd_pcm_oss
snd_pcm                86589  3 snd_ice1712,snd_ac97_codec,snd_pcm_oss
snd_page_alloc          8596  1 snd_pcm
ac97_bus                1450  1 snd_ac97_codec
snd_i2c                 5582  2 snd_ice1712,snd_cs8427
nvidia              10833434  32 
snd_mpu401_uart         6889  1 snd_ice1712
snd_seq_dummy           1782  0 
snd_seq_oss            31621  0 
snd_seq_midi            5989  0 
snd_rawmidi            23042  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event      7331  2 snd_seq_oss,snd_seq_midi
snd_seq                57823  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23223  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    72032  14 snd_ice1712,snd_ak4xxx_adda,snd_cs8427,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_i2c,snd_mpu401_uart,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8394  1 snd
lp                      9400  0 
parport                37470  2 ppdev,lp
fbcon                  39612  71 
tileblit                2487  1 fbcon
font                    8053  1 fbcon
bitblit                 5875  1 fbcon
softcursor              1565  1 bitblit
xhci                   43009  0 
vga16fb                12757  1 
vgastate                9921  1 vga16fb
usbhid                 40892  0 
hid                    84176  1 usbhid
r8169                  39426  0 
mii                     5237  1 r8169

```

So that looks pretty good to me.

I have an old FX5200 PCI card lying around so I will give that a shot and see if it works ok.

Tryin to start jackd gives:

```
jackd 0.118.0
Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details


Memory locking is unlimited - this is dangerous. You should probably alter the line:
     @audio   -  memlock    unlimited
in your /etc/limits.conf to read:
     @audio   -  memlock    6133185
no message buffer overruns
JACK compiled with System V SHM support.
loading driver ..
SSE2 detected
apparent rate = 44100
creating alsa driver ... hw:0|hw:0|1024|2|44100|0|0|nomon|swmeter|-|32bit
control device hw:0
control open "hw:0" (No such file or directory)
ALSA lib pcm_hw.c:1401:(_snd_pcm_hw_open) Invalid value for card
ALSA lib pcm_hw.c:1401:(_snd_pcm_hw_open) Invalid value for card
ALSA: Cannot open PCM device alsa_pcm for playback. Falling back to capture-only mode
cannot load driver module alsa

```

I assume the failure to connect to the card is resulting in the failure for hw:0

As for the AVlinux idea I did download and burn the iso the other day. I booted into it LIVE and did aplay- l but got the same message as with US about no cards. Do you think installing would make any difference?

Thanks for your time.

Cheers

---

### Post by Sylos on 2012-03-01
For some reason I missed other posts before my previous reply - doh!

gordintoronto - Thanks. I am actually pretty impressed with how well I have a done figuring it out so far. I think blind luck may be carrying me forward here. :lolflag:
I'll check out your link and see what I can figure out.

jejeman -  Sadly the half decent MB i forked out for only has IRQ settings for the serial port and something else (parallel I think) nothing for the PCI's. I tried altering all the settings I recognise (and a few I dont but that I dont think are critical). The MB is an overclocker so I am trying to be careful not to do anything that could result in component damage is I dont yet know anything about OC'ing (that will come later - much later by the look of it!)

Thanks to one and all for the help so far!

EDIT: Trying to enable msi for the nvidia but Sadly /etc/modprobe.d/nvidia.conf does not appear to exist. Anyonw know where its equivalent would be?

EDIT 2: Adding "options nvidia NVreg_EnableMSI=1" to /etc/modprobe.d/nvidia-graphics-drivers.conf has no effect - even with the pci=msi boot parameter.

---

### Post by sgx on 2012-03-01
install envy24control (alsa-tools-gui has it)  edit a file:

sudo gedit /etc/modprobe.d/alsa-base.conf   add a line:

options snd-ice1712 model=delta66

into the /etc/modprobe.d/alsa-base.conf file

Reboot, and run commands

modprobe snd-seq

modprobe snd-ice1712

jackd -d alsa -r 44100

jackd terminal output should finish much like this:

JACK compiled with System V SHM support.
loading driver ..
apparent rate = 44100
creating alsa driver ... hw:0|hw:0|1024|2|44100|0|0|nomon|swmeter|-|32bit
control device hw:0
configuring for 44100Hz, period = 1024 frames (23.2 ms), buffer = 2 periods
ALSA: final selected sample format for capture: 32bit integer little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 32bit integer little-endian
ALSA: use 2 periods for playback


run envy24control, go to the analog tab, (possibly must scroll
to the right)  raise the levels of the DAC

substitute 1010lt for delta66 above, if it fails, and repeat.

Cheers

---

### Post by Sylos on 2012-03-02
> **sgx said:**
> install envy24control (alsa-tools-gui has it)  edit a file:

sudo gedit /etc/modprobe.d/alsa-base.conf   add a line:

options snd-ice1712 model=delta66

into the /etc/modprobe.d/alsa-base.conf file

Reboot, and run commands

modprobe snd-seq

modprobe snd-ice1712

jackd -d alsa -r 44100

jackd terminal output should finish much like this:

JACK compiled with System V SHM support.
loading driver ..
apparent rate = 44100
creating alsa driver ... hw:0|hw:0|1024|2|44100|0|0|nomon|swmeter|-|32bit
control device hw:0
configuring for 44100Hz, period = 1024 frames (23.2 ms), buffer = 2 periods
ALSA: final selected sample format for capture: 32bit integer little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 32bit integer little-endian
ALSA: use 2 periods for playback


run envy24control, go to the analog tab, (possibly must scroll
to the right)  raise the levels of the DAC

substitute 1010lt for delta66 above, if it fails, and repeat.

Cheers

Thanks sgx.

I have tried altering the /etc/modprobe.d/alsa-base.conf with both the delta66 and delta1010 options already. It seems to do nothing. I didnt try modprobing snd-seq though so I'll try again with that in as well.

Modprobing snd_ice1712 seems to have no effect. Terminal output shows it is being loaded at boot but the card is just not being seen.

I've tried to get the nvidia card to use MSI but it doesnt seem to work. Cat /proc/interrupts still shows the card using apic and not msi. I assume that MSI is enabled at the kernel level as my ethernet card is shown as being MSI.

I also tried adding a line to alsa-base.conf "options snd_ice1712 enablemsi=1" but that failed on unkown parameter I think.

As I have nothing to loose I may try installing AVLinux as the suggestion for MSI is mentioned on their forums so I may have more success.


I have read that the irq can be forced but only if you know teh memory assignment? Not quite sure how that works to be honest.

Thought: could using dual channel memory have an bearing on the irq's?

Sadly I do feel like Im running out of options to try.

---

### Post by sgx on 2012-03-02
These are small, but worth testing, both work fine with my maudio pci and usb cards. The download links are in the first post.

[http://www.murga-linux.com/puppy/viewtopic.php?t=72402](http://www.murga-linux.com/puppy/viewtopic.php?t=72402)  378 meg

[http://www.pclinuxos.com/forum/index.php/topic,101747.0.html](http://www.pclinuxos.com/forum/index.php/topic,101747.0.html) 230 meg

this one uses synaptic, just install qjackctl and phasex in the live session to test, the wireless should be easy to configm follow to applications menu to 'Configure your computer.

Login as root and root in the live session. :popcorn:

---

### Post by Sylos on 2012-03-03
UPDATE:
I cant seem to install AVlinux. The live cd boots but the remastersys installed refuses to see my partitions to install to see the process fails.

I have tried using my old PCI FX5200 card and this allows the maudio to be registered. However, running an ardour session goes Xrun crazy. So that seems to be a waste of time.
](*,)](*,)](*,)](*,)(*,)](*,):cry:

---

### Post by sgx on 2012-03-03
[https://help.ubuntu.com/community/HowToJACKConfiguration](https://help.ubuntu.com/community/HowToJACKConfiguration)

[https://help.ubuntu.com/community/HowToQjackCtlConnections](https://help.ubuntu.com/community/HowToQjackCtlConnections)

Thats great news, now it's just tightening a few xrun screws, these links should get you in the ballpark. If you post your

/home/sylos/.jackdrc file, people can see if something can be
modified to your advantage. Try recording with timemachine, to
see if it's free from pops and anomalies. Timemachine is just a
big record button with a meter, connect your instrument output
to it in the audio tab of qjackctl.

Audacity loads and edits the tm.w64 files, vlc can play them.

Cheers

---

### Post by Sylos on 2012-03-03
> **sgx said:**
> [https://help.ubuntu.com/community/HowToJACKConfiguration](https://help.ubuntu.com/community/HowToJACKConfiguration)

[https://help.ubuntu.com/community/HowToQjackCtlConnections](https://help.ubuntu.com/community/HowToQjackCtlConnections)

Thats great news, now it's just tightening a few xrun screws, these links should get you in the ballpark. If you post your

/home/sylos/.jackdrc file, people can see if something can be
modified to your advantage. Try recording with timemachine, to
see if it's free from pops and anomalies. Timemachine is just a
big record button with a meter, connect your instrument output
to it in the audio tab of qjackctl.

Audacity loads and edits the tm.w64 files, vlc can play them.

Cheers

Thanks for the help sgx but sadly I dont think that this issue can be configured out.

I copied all my previous ardour sessions across from my old rig and loaded one up. I just played it as is and the sound was all jumpy and crackly and I watched qjackctl just racking up xruns at several per second. It seems that the PCI Nvidia is stealing bandwidth from the card (probably not the right term but meh). My old rig was an AMD atholn 2ghz with 768mb ram. If the new one cant even play a file created on it I dont think I can get it running properly.

I then unplugged the Nvidia and tried with the onboard GPU through HDMI into my TV. Same jack settings, same file - No xruns. I actually ran 2 of my biggest Ardour sessions at once playing and there were no xruns!

I hate to admit it, but for all my research prior to building this rig I appear to have got myself into a real problem area. 

I've started a thread in the Mutlimedia sectiont to see if I can get more advice on enabling MSI for the PCIe NVIDIA 7900gt. Otherwise I think my options are:
1. Buy usb audio card - I dont really want to as it will be more limited in terms of tracks I can have and my Maudio has got good preamps.
2. Buy new MB - Dont want to as it seems likely I will get the same issue with almost all sandybridge MBs.
3. Buy a HDMI capable monitor - probably the best bet in my opinion. Allows me to get decent performance without the risk of further failure.

For now Im not going to give up but Im running out of faith about being able to find a fix. I think this is a MB issue. It seems whatever I do the PCIe and PCI cards are always on the same IRQ. Ordinarily it is IRQ 16. If I boot with noapic I get both on IRQ 12. Just cant seem to separate them. I think perhaps the OS is seeing anything connected to the PCIe bridge as being the same IRQ.

May try and flash the BIOS and see if that helps. The manufacturers website mentions nothing about PCI fixes for the different versions but its worth a shot before shelling out another £100 on a monitor.

Cheers

EDIT: just for claritys sake; latency in jack was already set to 21ms so I don think making it any higher is a good idea.

---

### Post by sgx on 2012-03-04
[http://www.spinics.net/lists/linux-audio-users/](http://www.spinics.net/lists/linux-audio-users/)

The brain-trust resides in this mail-list, might be
lucky to ask them, now that you have defined the problem.

My .jackdrc  for comparison:

/usr/bin/jackd -P70 -t1000 -dalsa -r44100 -p256 -n2 -D -Chw:0,0 -Phw:0,0

In qjackctl setup panel, the only box ticked, is Realtime,
and MIDI Driver is 'none'

You can start jackd from a terminal with that first line,
then start qjackctl, which will use those parameters.

Capture hard  ware  and Playback hard  ware  -Chw:0,0 -Phw:0,0
should be changed to what is shown for the Delta, in qjackctl Setup panel

Input  Device  >
Output Device >   dropdown list.

For what its worth, I always use AMD chip motherboards with nVidia motherboard graphics,
and an AGP slot for the video card. Have not yet found a distro that would not use the mAudio card.

Cheers

---

### Post by Sylos on 2012-03-05
> **sgx said:**
> [http://www.spinics.net/lists/linux-audio-users/](http://www.spinics.net/lists/linux-audio-users/)

The brain-trust resides in this mail-list, might be
lucky to ask them, now that you have defined the problem.

My .jackdrc  for comparison:

/usr/bin/jackd -P70 -t1000 -dalsa -r44100 -p256 -n2 -D -Chw:0,0 -Phw:0,0

In qjackctl setup panel, the only box ticked, is Realtime,
and MIDI Driver is 'none'

You can start jackd from a terminal with that first line,
then start qjackctl, which will use those parameters.

Capture hard  ware  and Playback hard  ware  -Chw:0,0 -Phw:0,0
should be changed to what is shown for the Delta, in qjackctl Setup panel

Input  Device  >
Output Device >   dropdown list.

For what its worth, I always use AMD chip motherboards with nVidia motherboard graphics,
and an AGP slot for the video card. Have not yet found a distro that would not use the mAudio card.

Cheers

Thanks for the link. I cant seem to find a way of starting a thread or joining the site - any ideas how one does that?

I know what you mean about using the more traditional hardware but these AGP cards are expensive and its seems to be quite limiting in terms of what MB and CPU you can use. I built the designed this build to be as up to date as possible without spending huge amounts of money, the idea being that it would serve me for years with out needing to upgrade. Thats why I went with OCing capabilities - in years to come when it starts to feel slow I just ramp up the Vcore and the multiplier and crank another 1ghz out of it.

I seem to remember in the thread I started asking for advice on what hardware to get that you advised to stay away from flashy features that were windows trendsetters - I guess you can say I told you so now. ;)

On a related note: does anyone know if MB HDMI out provides the same analog signal you get from a DVI out port on a graphics card. Im just wondering if I can get a HDMI to DVI cable and then use my DVI to VGA adapter to run the HDMI into my VGA monitor. I really doubt it (I assume its all digital signal) but I might as well ask.

Cheers

---

### Post by jejeman on 2012-03-05
There should be no analog signal in HDMI, only digital. 
Look at the HDMI/DVI cables and you will see if there are pins for analog signal.

---

### Post by sgx on 2012-03-05
> **Sylos said:**
>  I cant seem to find a way of starting a thread or joining the site - any ideas how one does that?

[http://lists.linuxaudio.org/listinfo/linux-audio-user](http://lists.linuxaudio.org/listinfo/linux-audio-user)

Yeah, you'd think being linux guys, they'd automatically
put it right there where people read. ;) But, somehow,
found a better place off in a dusty corner.

This could be a season where motherboard improvements will outpace
the linux kernel downstream developement, putting us in
jeopardy when old trusted gear falls dead, and must be replaced.
Time to start keeping a list of the good stuff :)

---

### Post by sgx on 2012-03-05
[http://www.m-audio.com/index.php?do=support.faq&ID=80d7b56e35ea51e73104295aec1f755b](http://www.m-audio.com/index.php?do=support.faq&ID=80d7b56e35ea51e73104295aec1f755b)

This is mAudio page about IRQs that might come in handy
at some point, IRQ 16 is virtual, 0-15 are assignable.
Lots of learning curve here :)

---

### Post by Sylos on 2012-03-06
> **jejeman said:**
> There should be no analog signal in HDMI, only digital. 
Look at the HDMI/DVI cables and you will see if there are pins for analog signal.

Thanks jejeman. I did find an adapter that has the full dvi-i analog and didgital pins but if the HDMI out port is only outputting the digital then i guess the analog pins will just be redundant. If it comes to it I may stump the £4 and just get one - its worth a shot to save me £100 on a new monitor.

I've got an ongoing ticket with Gigabyte about my PCI/PCIe issue. I have found some other issues asides the IRQ conflict. I tried switching the NVIDIA 7900gt into the x4 PCIe slot but it just freezes when trying to initialise the graphical splash screen (after grub and the initial loading screen). Seems odd to me. I know using the x4 slot would reduce performance but the 7900GT is old and not hugely demanding. A freeze seems to suggest that there may be a hardware issue. I await the response from Gigabyte on that front.

sgx: Thanks for the extra reading. I seem to be becoming quite well up on IRQs now. Sadly it just seems to lead me closer to the conclusion that it cant be changed from the OS, so if the BIOS sets it that way, Im stuck with it.

On the general hardware for linux audio users front, I do think there is a bit of an issue upon us. Reading the RME users forum they seemed to sugest that almost all Sandybridge MBs have issues with throughput to the PCI slots making use of high end profesional cards impossible. Lower end cards should supposedly work as the throughput is less demanding. But if the IRQ conflict issue Im having happens on a lot of MBs (and Im assuming it isnt just a chip defect in my case) then it could pose a difficult choice for people upgrading audio rigs. If you want the best performance you really dont want to go USB due to the limitations of the interface speed, Firewire is better if the device is supported but still the best way for top performance on multi track set ups is PCI/e. 

I am pretty annoyed that the manufacturers dont give any technical info that lets you know that the PCI slots arent run by a traditional PCI controller (or whatever you call it). The tech specs always just say how many of each type of slot. It defines that some PCIe slots run slower when others are in use but says nothing on the PCI slots being on a bridge to PCIe and definitely doesnt say anything along the lines "If your planning on installing a half decent audio capture card then you, my son, are humped!". Probably wouldnt be good marketing I suppose.

Hey ho. I'll wait and see what Gigabyte have to see (took em over a week to respond to my first message) and see what comes of that before I go any further (I dont want to waste anybodies time if it IS a MB defect causing this). I already filed a bug report on launchpad (first time I've ever done that - I feel I've become a man at last :D) and I have been advised to try the lastest Dev Kernel to see if the issue persist. That should provide me with enough breakage to amuse me for a little while :D

Cheers

---

### Post by Sylos on 2012-03-13
Okey kokey pig in a pokey......

During my recent testing of this issue I have tried installing the latest NVIDIA driver from the NVIDIA website.

Having run the gauntlet of manual install I ran "nvidia-settings" from the terminal and got this output:

```
ALSA lib confmisc.c:768:(parse_card) cannot find card '0'
ALSA lib conf.c:4154:(_snd_config_evaluate) function snd_func_card_driver returned error: No such file or directory
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:4154:(_snd_config_evaluate) function snd_func_concat returned error: No such file or directory
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib conf.c:4154:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:4633:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib confmisc.c:768:(parse_card) cannot find card '0'
ALSA lib conf.c:4154:(_snd_config_evaluate) function snd_func_card_driver returned error: No such file or directory
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:4154:(_snd_config_evaluate) function snd_func_concat returned error: No such file or directory
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib conf.c:4154:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:4633:(snd_config_expand) Evaluate error: No such file or directory

```

Now thats an awful lot of alsa stuff for a graphics card command. And look how it says that my sound card isnt found.

I have no idea what this means! Anyone got any ideas?

Cheers

---

### Post by jejeman on 2012-03-14
Hello Sylos,

I've also recently upgraded my pc and have shared IRQ beetwen PCI-E & PCI. 
```
 16:       1463       2264       1480       2261   IO-APIC-fasteoi   ehci_hcd:usb1, ohci1394, nvidia
```
My motherboard is MSI H55M-P31, which also has no IRQ options in BIOS. Although I don't use PCI audio card, I'm using PCI firewire card for firewire audio card. And I have much worst performance than before hardware upgrade. 
Here something that I find out.
On Ubuntu Studio 10.04 I get much better performance if I disable IOACPI in BIOS. 
On Xubuntu 11.04 with lowlatency kernel it's all working fine, no need for disabling IOACPI, but still not like before.

I see that you have already tried disableing acpi, but I wanted to share this anyway.
We can see that not just those who use pci audio cards are affected with this, but also those who use firewire cards.

---

### Post by Sylos on 2012-03-14
Scratch the above. Seems to just be permissions related because as a normal user it cant access the /dev/dsp/ folder. My user is a member of the audio group so I would have thought access would be permitted.

Anyhow, using "sudo nvidia-settings" means I dont get all the alsa output so another dead end there.

---

### Post by Sylos on 2012-03-14
> **jejeman said:**
> Hello Sylos,

I've also recently upgraded my pc and have shared IRQ beetwen PCI-E & PCI. 
```
 16:       1463       2264       1480       2261   IO-APIC-fasteoi   ehci_hcd:usb1, ohci1394, nvidia
```
My motherboard is MSI H55M-P31, which also has no IRQ options in BIOS. Although I don't use PCI audio card, I'm using PCI firewire card for firewire audio card. And I have much worst performance than before hardware upgrade. 
Here something that I find out.
On Ubuntu Studio 10.04 I get much better performance if I disable IOACPI in BIOS. 
On Xubuntu 11.04 with lowlatency kernel it's all working fine, no need for disabling IOACPI, but still not like before.

I see that you have already tried disableing acpi, but I wanted to share this anyway.
We can see that not just those who use pci audio cards are affected with this, but also those who use firewire cards.


Somehow missed your post there jejeman - sorry.

Sad to hear you are also having problems. I may have something of use for you though.

I was recomended to install the development kernel (linux-image-3.3.0-030300rc6-generic_3.3.0-030300rc6.201203032235_amd64.deb) and that did shift my IRQ's about so that the NVIDIA and Maudio were on seperate IRQs (16 and 12 I believe) - BUT my problem persists.

Also, I installed the latest NVIDIA driver from the NVIDIA website (the 295.20 for my card) which has allowed me to enable MSI (message signalled interrupts) for the NVIDIA which was not functioning with the official supported drivers available through Jockey/repos. My NVIDIA now sits on IRQ 30 (a theoretical IRQ as I think only 15 are hardwired). Again, it hasnt fixed my problem but as your issue is different it may help you out. MSI is definitely recomeneded for improving performance. If you want to enable MSI I think I posted what I did earlier in this thread.

Let me know how you get on - it would be nice to see some success. :p

Cheers

---

### Post by Sylos on 2012-04-15
Hello again everyone.

So Im still wrestling the beast with this one. I have posted up on the alsa-user mailing list and following a couple of early responses things have gone a little quiet. Anyhow, I was advised to removed then reinsert the snd-ice1712 module and check dmesg to see if there are any errors and there were:

```
[ 7838.014939] ICE1712 0000:06:00.0: PCI INT A -> GSI 19 (level, low) -> 
IRQ 19
[ 7838.014967] ice1712: Using board model M Audio Delta 66
[ 7838.014971] invalid EEPROM (size = 145)
[ 7838.014987] ICE1712 0000:06:00.0: PCI INT A disabled
[ 7838.014996] ICE1712: probe of 0000:06:00.0 failed with error -5
```

So error 5 seems to be a general I/O error (couldnt find anymore info on that). EEPROM is something to do with writing to chips I believe - but I know nothing more than this.

Im trying to get a handle on where the problem is arising. I need to work out if this is alsa based or kernel based.

As always, any ideas or info would be gratefully received.

Cheers

---

### Post by sgx on 2012-04-16
Hi, If you have multiple pci slots, try it in the others,
with no other pci cards or usb devices connected.
Turn off all the networking, bluetooth, webcam, power mangement,
etc in the bios (take notes, never just 'restore defaults')

If you got this card used, take a pencil erasure and clean the cards pci connector, and inspect the card for soot :evil:

Does it work in XP? (sorry, didn't read the thread yet ;)
Cheers

[http://www.murga-linux.com/puppy/viewtopic.php?t=72402](http://www.murga-linux.com/puppy/viewtopic.php?t=72402)

link in the first post to Puppy Studio, and audio/video
linux setup which works fine as a live CD
with my maudio pci and usb cards

---

### Post by Sylos on 2012-04-16
> **sgx said:**
> Hi, If you have multiple pci slots, try it in the others,
with no other pci cards or usb devices connected.
Turn off all the networking, bluetooth, webcam, power mangement,
etc in the bios (take notes, never just 'restore defaults')

If you got this card used, take a pencil erasure and clean the cards pci connector, and inspect the card for soot :evil:

Does it work in XP? (sorry, didn't read the thread yet ;)
Cheers

[http://www.murga-linux.com/puppy/viewtopic.php?t=72402](http://www.murga-linux.com/puppy/viewtopic.php?t=72402)

link in the first post to Puppy Studio, and audio/video
linux setup which works fine as a live CD
with my maudio pci and usb cards

Cheers for the thoughts sgx but I have (sadly) been through most of the above. Havent tried puppy studio but I dont think it will do me much good. Will give it a shot anyway.

The problem is the card works fine in this mobo when my pcie graphics card is not present - kicks up the above error when it is. Frankly I dont see how or why. The MB specs show that the PCIe x 16 slot has independent lanes to the CPU - the PCI slots are then bridged into the second PCIe x16 (running at x4) slot. So you would think the installation of the graphics card wouldnt make any difference to how the PCI slots/cards run. But it does. When the graphics card is absent the card works flawlessly with no eeprom error - install the graphics card and the error comes up and my card isnt recognised by alsa/asound etc. It's annoying the crap outta me.

Anyhow, Im trying to find out if the kernel module is the bit causing the issue. Im trying to get a handlle on where to turn to in order to try and get a resolution. 

Would it be bad form/ettiquette to send such a querry to the linux-audio-devs mailing list (not sure if they would frown on such lowly folk as myself asking support querries on their list).

Cheers

---

### Post by sgx on 2012-04-17
Different kernels can yield different results, and are assembled by people of varying skills and resources. Also the hardware sniffing can fail miserably in one linux, and excel in another.

Two different distros here, but one rejects the video card.
And two recent versions of a third distro, also where
just one of them fails, despite the same release devs.

I always cringe when I see interrupt 19. If folks from
the list get this fixed, it could be an important one,
that will have implications for other hardware that fails
in just certain pairings. Could be the first domino.
:popcorn:
Those who seek knowledge, are never lowly.

---

### Post by Sylos on 2012-04-17
IT LIIIIIIIIIIIIIIIIIIIIIIIIIIIIIIIIIIIIIVVVVVVVVVVVVVVVVVVVVVVEEEEEEEEEEEEEESSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSS!

#sylos churns the butter#
#sylos does the running man#
#sylos mows the lawn#
#sylos does every dance known to man all at once and breaks a hip-- drag!#


I tried installing my old soundblaster card alongside the Maudio - at first the soundblaster was hogging jack (both cards are HW:0 under aplay -l) so I blacklisted the soundblaster module and there she is - my maudio - working and playing my biggest ardour file with no X-runs!


Whoop Whoop!

Havent tried recording yet but that will come soon.

It seems the issue is having another card in the other PCI slot (I tested with an old NVIDIA PCI grpahics card way back and found it registered the Maudio but was unusable as the NIVIDIA took all the bandwidth). But the presence of a redundant soundblaster card all appears well so far. It doesnt seem to matter what type of card - just anything will do.

Damn it yeah - expletive - yeah. Happiest man in town right now!

A big thank you to everyone who looked at this post and any other bit of crap I have posted on the web (or IRC) about this issue. Your time is much appreciated.

However, I would say dont buy one of these boards - they can be an *** to configure!

:guitar::guitar::guitar::guitar::guitar::guitar:

---

### Post by Sylos on 2012-04-17
Well - spoke too soon there!

The card works for playback but I cant get any level through on the input.

That sucks major ***!

---

### Post by Sylos on 2012-04-17
Nevermind!

Im a major neewb - didnt remove pulseaudio or set envy24control levels.

All works again now - Sylos goes back to dancing (on broken hip).

Anyone know where I should direct the outcome of this for a possible fix (maybe kernel bug report?)


Cheers

---

### Post by jejeman on 2012-04-17
Wow, that is one interesting solution. So, you occupay one more pci slot and it works? What about nvidia in pcie slot, is it working well? How does your irq table looks now?

---

### Post by Sylos on 2012-04-17
> **jejeman said:**
> Wow, that is one interesting solution. So, you occupay one more pci slot and it works? What about nvidia in pcie slot, is it working well? How does your irq table looks now?

Yeah - mind blogger eh? But I have just tested with an old modem card and that didnt do it. So far I've found my old PCI NVIDIA GFX5500 card and the soundblaster card seem to do the trick.

the irq's show the Maudio on IRQ 19 (not great I guess) and the NVIDIA on IRQ 16.

But I plan on installing the NVIDIA driver from the website again and using MSI for that which should bump the card down a little.

I still dont get why or how this is the case. It makes no sense. But I suppose there is an issue with how the kernel is seeing the card (possibley due to the bridge chip being used to go PCI to PCIe lanes).

Do you reckon there is any mileage in opening up a new bug report with this?

Im happy for now at least. It may turn out to have crap performance but Im just happy to have anything at the moment.

Cheers

---

### Post by sgx on 2012-04-17
The mailing list would be good to send the info to. Likely they
already represent the brains of many forums, and some of the
key developers will be sure to see it.
Glad you can use your Delta! :D

---

### Post by cryptozoon on 2012-11-29
Sylos

I have been getting identical results from using Ubuntu studio 12.04 64 bit with the Gigabyte GA-Z68AP-D3, an Nvidia GTX560ti, and an M-audio delta audiophile 2496. 

  lspci returns 06:00.0 Multimedia audio controller: VIA Technologies Inc. ICE1712 [Envy24] PCI Multi-Channel I/O Controller (rev 02)
modinfo snd-ice1724 returns what seems to be the proper module, /lib/modules/3.2.0-33-lowlatency/kernel/sound/pci/ice1712/snd-ice1724.ko
But running envy24control returns No ICE1712 cards found

I have been watching the efforts of Mr. Sylos (aka. Sisyphus) and have been mirroring efforts to fix the M-Audio bug that was supposed to be sooo easy to fix.. A sysadmin basically slammed a thread on me because I tried to reply to a post older than a few years. A long post of mine in the Ubuntu forum was never answered. The M-audio card was listed in [http://alsa-project.org/main/index.php/Matrix:Module-ice1712](http://alsa-project.org/main/index.php/Matrix:Module-ice1712). As far as the Gigabyte MB and the Nvidia gtx 560ti compatibility, I had not seen any issues in my searches. Most hits I found were circa 2009. I erroneously thought that the issues would have been cleared up in four years of work. I scheduled time for a shiny new build with the parts mentioned and then suffered a concussion when an old lady talking on her cell rear ended me with her Suburban. After that, it took only seventeen tries and two months to get a dual boot win7/Ubuntu machine running.

  I will study the work of my hero Sylos, and in the mean time adapt an older pentium machine to run the studio package, that's probably all its worth. I don't have the persistence that sylos does and I tire easily, now.   I'll use my fancy machine for Windows7 and 3D movie playback that behaves with only minor fiddling (less than 12.04 lts) Thanks again, Sylos.

---

### Post by Sylos on 2012-11-30
> **cryptozoon said:**
> Sylos

I have been getting identical results from using Ubuntu studio 12.04 64 bit with the Gigabyte GA-Z68AP-D3, an Nvidia GTX560ti, and an M-audio delta audiophile 2496. 

  lspci returns 06:00.0 Multimedia audio controller: VIA Technologies Inc. ICE1712 [Envy24] PCI Multi-Channel I/O Controller (rev 02)
modinfo snd-ice1724 returns what seems to be the proper module, /lib/modules/3.2.0-33-lowlatency/kernel/sound/pci/ice1712/snd-ice1724.ko
But running envy24control returns No ICE1712 cards found

I have been watching the efforts of Mr. Sylos (aka. Sisyphus) and have been mirroring efforts to fix the M-Audio bug that was supposed to be sooo easy to fix.. A sysadmin basically slammed a thread on me because I tried to reply to a post older than a few years. A long post of mine in the Ubuntu forum was never answered. The M-audio card was listed in [http://alsa-project.org/main/index.php/Matrix:Module-ice1712](http://alsa-project.org/main/index.php/Matrix:Module-ice1712). As far as the Gigabyte MB and the Nvidia gtx 560ti compatibility, I had not seen any issues in my searches. Most hits I found were circa 2009. I erroneously thought that the issues would have been cleared up in four years of work. I scheduled time for a shiny new build with the parts mentioned and then suffered a concussion when an old lady talking on her cell rear ended me with her Suburban. After that, it took only seventeen tries and two months to get a dual boot win7/Ubuntu machine running.

  I will study the work of my hero Sylos, and in the mean time adapt an older pentium machine to run the studio package, that's probably all its worth. I don't have the persistence that sylos does and I tire easily, now.   I'll use my fancy machine for Windows7 and 3D movie playback that behaves with only minor fiddling (less than 12.04 lts) Thanks again, Sylos.

Hello there and I have to say - sorry to hear you are suffering with the same problem I had. :(

Before I say anything more I will say up front that my knowledge is severely limited so I cant really say what the problem is for sure. What follows is just my understanding of teh problem that I gained from googling and using my own logic (and that may well lead to incorrect conclusions - but the important thing is finding a solution regardless of the reason):

So....
It seems to me that ubuntu/general debian based distros have a problem with addressing the card when the PCIe slots are filled with graphics cards. This I believe is the reason for the EEEPROM error showing in dmesg I refered to in the thread. My suspicion is that this is all related to the evil bridge chips they use on the mobo to run PCI slots thorugh PCIe controllers. Both PCI slots run through this little chip and I reckon that it plays a major part in the trouble (my conjecture - cant prove it!). Its worth noting that when I installed the soundblaster card that solved the problem for me both cards were given the same HW identifier when running aplay -l etc (which suggests to me that the bridge chip is screwing it up). Anyhow, either way it seems unable to properly address the chip on the soundcard properly.

It seems that installing an additional PCI card in the available slot addresses this problem. I said earlier in the thread that any card will work but Im not so sure about that anymore. I did try with an old ethernet card and that didnt seem to do anything. That may be because I didnt have the right modules loaded for that card or because the card was dead - Im not sure. It may require a bit of trial and error with whatever cards you have available.

Once you get a card that works for the job I suggest blacklisting its modules to stop it taking up any bandwidth (when I tried it with a PCI graphics that I used to run the monitor the performance of the soundcard was awful - the graphics card just ate too much bandwidth and strangled my M-audio.

Once running I have found mine to be adequate for the recording I do (and Im not good at recording so I have a LOT of tracks in Ardour which help me avoid the need to be a better musician and engineer). This will also get better when Ardour3 gets a final release as it uses more than one CPU core (unlike ardour 2 that crams everything into 1 core).

...and thats what I know.

Thank you for the kind words although I wouldnt say Im a hero -  just a man with a stubborn attitude towards things.

I wont say that I can do anything to help BUT feel free to PM me or post back on here and I will do anything I can to assist. 

Cheers
:guitar:

---

