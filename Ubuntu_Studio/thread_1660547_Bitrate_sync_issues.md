---
title: "Bitrate sync issues?"
date: 2011-01-05
forum: Ubuntu Studio
---

### Post by MorphMaker on 2011-01-05
Hello all! 

My audio has stumped me......again.

Machine is as follows:
 Asus m4a79t deluxe,
 AMD 955 black edition 3.2G,
 4G Gskill DDR3(it's speed escapes me ATM, but it's fast),
 Nvidia 250gtx,
 m-audio delta 1010,
Ubuntu Studio 10.04

I'm trying to use this machine as a DAW. For the most part, everything works great, except one issue.

I'm using JACK with ALSA drivers. Input comes from the Delta 1010, usually directly into Ardour. Output goes to the onboard audio, for monitoring purposes during a session/mix down/ etc. The issue is a sizzling noise that occurs when routed this way.  

If audio travels this path -->in to delta 1010>jack (system capture 1>system playback 1)> out of jack> on board sound/-- I get the sizzling/crackling noise.

If, however, audio travels -->in to delta 1010>jack (same as above)> out of jack> delta 1010] this does not occur.

The only thing I change is the output in JACK's setup from my onboard sound to the Delta (then obviously where I physically connect my monitors, back of MOBO for HDA, out1 on the back of the Delta for the other). 

The end result with path 1 above, is a recording with waves of overbearing sizzling/crackling that come and go. I have not tried path 2 yet, as path 1 is my preferred setup due to budget constraints.

 If I change JACK's sample rate, it seems to have an effect on the pitch of the sizzle and it's duration-higher sample rates equate to a higher pitch sizzle with a shorter duration, lower sample rates equal lower pitched sizzle with a much longer duration.

Anybody got any ideas? I can try to be more specific if need be. Thanks in advance!!

---

### Post by Pablo_F on 2011-01-05
Hi, 

Sorry if this is OT but I don't see why you are using the onboard card at all. 

With a delta 1010 there are at least two ways that you can monitor your recordings. 

1. Use the internal mixer of the card. You can access it by means of the alsa tool called "envy24control". 

2. Select "ardour does monitoring". (Options -> Monitoring).

The second option is easier but you need a low latency setting (512 frames / period or less). Anyway, with your card you can get a low enough latency to do software monitoring. Then, you don't want to connect system: captures to system: playbacks in jack conections. Connect system: captures to the audio track in ardour and ardour masters to system: playbacks. 

You can also use a bus for monitoring purposes, from master outs to system: playbacks 3 and 4 for example.


jack with two different cards is not a good idea. If you still want to monitor with the onboard, use alsa_out. See man "alsa_out".  "alsa_out -jonboard -dhw:Intel" for example. 

See "cat /proc/asound/cards" for the names of the cards (between square brackets) and use names in qjackctl and alsa_out, instead of numbers, which can change in different boots.

Cheers! Pablo

---

### Post by MorphMaker on 2011-01-05
Thanks for the reply!

I don't normally run system:capture to system: playback, this was done in an effort to isolate JACK and hardware so I could further try to diagnose what's causing it. Under normal circumstances, I run system:captures to ardour audio track, then I monitor the master out of ardour, which works flawlessly untill the sizzling returns. 

It seems to be originating from somewhere between the delta and ardour, because ardour actually records it! I can produce a sound clip with specs if you'd like. 

It's confusing me because if it's originating BEFORE ardour can record it, that means it's either JACK, or the delta 1010.
 I've ran audio from the delta, straight through JACK (system:captures to system:playback) and right back out of the delta via headphones and never once had this occur. However, as soon as I change the output to onboard audio, then route straight through JACK, it's back. The only thing changed is the output source in JACK's setup page. This then leads me to believe it's the onboard audio not playing nice, which would be AFTER ardour would have a chance to record it. 

The reason I'm running in from the delta and out to the onboard sound is because I don't own a mixer, or a nice set of monitors.....yet. Therefore, I currently only have my computer speakers (which is awful,I know...actual monitors will come this spring), or my studio headphones (which ARE actually made for this purpose). Like I said earlier, budget constraints are currently keeping me from just using the delta for everything. /sad/

---

### Post by MorphMaker on 2011-01-06
Well, after doing some messing around, hardware AND software related, I've decided my best bet is to use the delta as the primary sound device. After some testing, I've found that going this route gives me crystal clear audio while recording and monitoring. However, now it's not in stereo, and I have NO sound when JACK isn't running.

I'm using a 1/4" TRS connector from the delta to my powered "monitors" ( I swear I can't wait till spring, these things drive me nuts!) and all I get is mono sound.  I suppose it's time to cruise the forums looking for answers! 

I may or may not update this thread, depends on weather or not I find what I'm looking for, and also if there's replys besides myself.....I don't wanna be that crazy guy arguing with himself......out loud......in public.......

):P

---

### Post by MorphMaker on 2011-01-06
well, I thought I had this figured out. I switched off the on-board sound in BIOS, rebooted. Nothing. Not a single sound device is found anywhere. aplay -l says there's not one. alsamixer says no device is installed. 
So, I purged and reinstalled alsa (and all of it's associated utils, etc) still nothing. I reinstalled envy24 and ICE1712 drivers....nothing has changed. there are still no audio devices installed. Now, I've switched on-board audio back on in the BIOS.....nothing, there are still no sound devices installed......FML

---

### Post by Pablo_F on 2011-01-06
> However, now it's not in stereo, and I have NO sound when JACK isn't running.

This is a known issue with pulseaudio. See:

[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/178442](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/178442)

There are several workarounds. The easiest one comes from comment #30. At least you will have playback from pulseaudio.


> I'm using a 1/4" TRS connector from the delta to my powered "monitors" and all I get is mono sound.

Sure. You have mono in/out connectors in the Delta 1010. I think you need a Stereo Mini Plug to Left/Right Mono Plugs, as shown in [http://www.audiogear.com/Audio-Adapters-Miniplug.html](http://www.audiogear.com/Audio-Adapters-Miniplug.html)

Cheers! Pablo

---

### Post by Pablo_F on 2011-01-06
> nothing, there are still no sound devices installed.....

First off all, see if the hardware is recognised by lspci. In a terminal:

**lspci | grep i audio**

---

### Post by MorphMaker on 2011-01-06
output of lspci | grep i audio

bee@ebm-workstation1:~$ lspci | grep i audio
grep: audio: No such file or directory
bee@ebm-workstation1:~$ 

the delta 1010 has balanced outs compatible with TRS connectors. I have a male 1/4"trs to female 1/8" (or 3.5mm, i forget) adapter that my speakers are plugged into, which is also a balanced connector. They're a 2.1 set of boston acoustics made for computers. Why wouldn't this give me stereo sound? Not that it matters now, I have NO sound! lol!!

---

### Post by Pablo_F on 2011-01-06
The balanced outputs are still mono, not stereo. If I understand correctly, you are trying to connect a balanced mono signal to an **unbalanced stereo** input via TRS connectors. This does not work. 

Well, the important thing, double-check lspci (without the grep filter, just in case). If you still don't see the m-audio check that:

The card is correctly inserted in the PCI slot.
The BIOS is OK.

Cheers! Pablo

---

### Post by MorphMaker on 2011-01-06
Here is the out put of lspci without the the grep filter


00:00.0 Host bridge: ATI Technologies Inc RD790 Northbridge only dual slot PCI-e_GFX and HT3 K8 part
00:02.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (external gfx0 port A)
00:06.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (PCI express gpp port C)
00:07.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (PCI express gpp port D)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
**00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)**
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Link Control
**01:06.0 Multimedia audio controller: VIA Technologies Inc. ICE1712 [Envy24] PCI Multi-Channel I/O Controller (rev 02)**
02:00.0 FireWire (IEEE 1394): VIA Technologies, Inc. Device 3403
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
04:00.0 VGA compatible controller: nVidia Corporation G92 [GeForce GTS 250] (rev a2)


I believe It shows it listed as a multimedia audio controller, provided that ICE1712 is the correct card, no?

BTW, thanks a million for the help!!

---

### Post by Pablo_F on 2011-01-06
> I believe It shows it listed as a multimedia audio controller, provided that ICE1712 is the correct card, no?

Yes! 

It is all right now. You should have sound through alsa-jack. I hope the drivers (snd-ice1712 kernel module for the m-audio) are loaded. If you want to check, look at:

cat /proc/asound/cards
cat /proc/asound/modules


However, you won't have sound through pulseaudio (the default ubuntu audio server) out of the box. Read above.

Cheers! Pablo

---

### Post by MorphMaker on 2011-01-06
This where it goes wrong.....


/proc/asound  doesn't exist.  output of cat/proc/asound/*anything in this position* comes back that there is no such file or directory. Sure enough, when I navigate to  /proc and look for asound, there's nothing there! Weird, right!?

---

### Post by Pablo_F on 2011-01-07
Hi, yes it is weird.

Try reinstalling linux-sound-base and alsa-base. Even, all the alsa related packages.

Cheers, Pablo

---

### Post by cchhrriiss121212 on 2011-01-07
^ If that does not help, try using:
aplay -l
Which will also show whether or not the ice module is loaded.

---

### Post by MorphMaker on 2011-01-07
aplay -l says there are no sound cards installed. alsamixer says there are no sound cards installed.

I'm just going to try a fresh install and see how well that works. With any liuck I'll have the sound devices I want, and xorg will let me have both monitors again. :fingerscrossed:

---

