---
title: "Jack issue: Sound card arbitrarily assigned hw:0, hw:1, hw:2 - How to force assgnment"
date: 2012-05-29
forum: Ubuntu Studio
---

### Post by tehowe on 2012-05-29
Jack works great with the lowlatency driver for me, but only sometimes.  

Maybe others are having the same problem... on some reboots, my Audigy is assigned hw:0 in which case I can leave JACK's Input and Output Device(s) set to default and everything's great.

Restart the computer and it seemingly randomly switches to hw:2 or hw:1. If I point the devices to the appropriate devices, JACK either won't start and spews errors or starts but has horrible latency. Using the realtime kernel is equally sketchy

Is there a way to force assignment on startup? I looked through the forums, so apologies if this has been covered and I missed it.

---

### Post by CrocoDuck on 2012-05-29
Have a look here: [https://help.ubuntu.com/community/UbuntuStudio/UsbAudioDevices](https://help.ubuntu.com/community/UbuntuStudio/UsbAudioDevices)

---

### Post by chkneater on 2012-05-31
something I just found out, if you don't boot out of Jack by clicking the Quit button, it can cause problem with pulseaudio later.  Try " killall qjacktcl "  or  "killall jackd "  It won't cause damage, it just stops the jack backend from running.  Once you stop it you can restart and it should work fine again.  

Also apps that you have open before you start Jack, like video or audio that don't use jack drivers have to be closed and reopened after Jack starts back up.

---

### Post by tehowe on 2012-06-07
> **chkneater said:**
> something I just found out, if you don't boot  out of Jack by clicking the Quit button, it can cause problem with  pulseaudio later.  Try " killall qjacktcl "  or  "killall jackd "  It  won't cause damage, it just stops the jack backend from running.  Once  you stop it you can restart and it should work fine again.  

Also apps that you have open before you start Jack, like video or audio  that don't use jack drivers have to be closed and reopened after Jack  starts back up.

That sounds like a good tip for keeping  things running smoothly in the current session, thanks. I've noticed  that I _often_ can't restart qjackctl after I've run it, stopped it,  done things with applications that use pulseaudio, and tried to start  qjackctl up again.

I've found out lately that there's a  pulseaudio to JACK bridge as well so hopefully stopping and restarting  jack won't be necessary. Kaj Ailomaa on the mailing list says

> The bridge is active by default on qjackctl. All you need to do is to 
choose jack as the output from the pulseaudio mixer. This will route 
pulseaudio to jack.

If you've made any settings changes to qjackctl, make sure "Enable D-Bus 
interface" is on, under "Setu"p -> "Misc".
Also, jackd2 is required (installed by default).

When you start jack, you should see "PulseAudio JACK Sink" and 
"PulseAudio JACK Source" under "Connect" -> "Audio". Second step is as 
mentioned above, to set pulseaudio to use jack as it's output (and 
input, if you want to route jack audio to pulsaudio).> Have a look here: [https://help.ubuntu.com/community/Ub...sbAudioDevices]("https://help.ubuntu.com/community/UbuntuStudio/UsbAudioDevices")> the configuration is relatively arcaneHa.  Oh well, it makes for an interesting puzzle. One of the things that's  probably a challenge when you're learning the shell is knowing where  everything's kept... I wonder if there'd be a way these days to index  bash commands semantically and config files somehow, can you add  metadata to ext4 files?... anyhow

```
:~$ cat /proc/asound/cards 
 0 [Generic        ]: HDA-Intel - HD-Audio Generic
                      HD-Audio Generic at 0xfe8bc000 irq 53
 1 [U0x46d0x81d    ]: USB-Audio - USB Device 0x46d:0x81d
                      USB Device 0x46d:0x81d at usb-0000:00:12.2-5, high speed
 2 [Audigy         ]: Audigy - SB Audigy 1 [SB0090]
                      SB Audigy 1 [SB0090] (rev.3, serial:0x511102) at 0xdc00, irq 22

``````
:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 046d:081d Logitech, Inc. HD Webcam C510
Bus 002 Device 004: ID 058f:6364 Alcor Micro Corp. Hi-Speed 7-in-1 Flash Card Reader/Writer [Sabrent]
Bus 005 Device 002: ID 046d:c046 Logitech, Inc. RX1000 Laser Mouse
Bus 005 Device 003: ID 0cf3:3005 Atheros Communications, Inc. AR3011 Bluetooth
Bus 009 Device 002: ID 1058:1140 Western Digital Technologies, Inc. 
Bus 004 Device 002: ID 04a9:2206 Canon, Inc. CanoScan N650U/N656U
Bus 002 Device 006: ID 0421:01c7 Nokia Mobile Phones N900 (Storage Mode)

```So I enter "sudo lsusb -v | less" and browse around.

It's _really_ long, but less responds to the mouse scroll wheel... looks like we should filter this list

```
sudo lsusb -v | grep Bus | less

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 046d:081d Logitech, Inc. HD Webcam C510
      (Bus Powered)
  (Bus Powered)
Bus 002 Device 004: ID 058f:6364 Alcor Micro Corp. Hi-Speed 7-in-1 Flash Card Reader/Writer [Sabrent]
      (Bus Powered)
  (Bus Powered)
Bus 005 Device 002: ID 046d:c046 Logitech, Inc. RX1000 Laser Mouse
      (Bus Powered)
  (Bus Powered)
Bus 005 Device 003: ID 0cf3:3005 Atheros Communications, Inc. AR3011 Bluetooth
Bus 009 Device 002: ID 1058:1140 Western Digital Technologies, Inc. 
Bus 004 Device 002: ID 04a9:2206 Canon, Inc. CanoScan N650U/N656U
      (Bus Powered)
  (Bus Powered)
Bus 002 Device 006: ID 0421:01c7 Nokia Mobile Phones N900 (Storage Mode)
      (Bus Powered)
  (Bus Powered)
Bus 005 Device 004: ID 041e:3f00 Creative Technology, Ltd E-Mu Xboard 25 MIDI Controller
  (Bus Powered)

```Since  my USB devices are here but not my sound card, I'll hypothesize that  USB audio devices are knocking my sound card out of top spot but they're  not the only problem - my HDMI monitors pass audio as well.

Searching Ubuntu Studio docs for HDMI came up with this

[https://help.ubuntu.com/community/SoundTroubleshootingGuide#Ad_.28Switch_default_sound_card.29](https://help.ubuntu.com/community/SoundTroubleshootingGuide#Ad_.28Switch_default_sound_card.29)

This covers 10.04-11.10. Ulp, I have 12.04

```
 :~$ aplay -l | grep card | less
card 0: Generic [HD-Audio Generic], device 3: HDMI 0 [HDMI 0]    
card 2: Audigy [SB Audigy 1 [SB0090]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]      
card 2: Audigy [SB Audigy 1 [SB0090]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
card 2: Audigy [SB Audigy 1 [SB0090]], device 3: emu10k1 [Multichannel Playback]   

```

Ok so I create a new file /etc/asound.conf putting the desired card and device number in below

```
pcm.!default {
type plug slave.pcm {
type hw card 2 device 0
}
}

```

But aren't these the same numbers that are being moved around arbitrarily? I guess it's worth a shot.

---

### Post by tehowe on 2012-06-07
...and that turns out to do nothing as my card's now randomly (?) moved to HW:3

```
card 3: Audigy [SB Audigy 1 [SB0090]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
```That's unhelpful but I've just noticed that the sound cards have a similar ID in description, it's just not under lsusb it's under 

```
:~$ cat /proc/asound/cards
 0 [Generic        ]: HDA-Intel - HD-Audio Generic
                      HD-Audio Generic at 0xfe8bc000 irq 53
 1 [U0x46d0x81d    ]: USB-Audio - USB Device 0x46d:0x81d
                      USB Device 0x46d:0x81d at usb-0000:00:12.2-5, high speed
 2 [Xboard25       ]: USB-Audio - E-MU Xboard25
                      E-MU Systems, Inc. E-MU Xboard25 at usb-0000:00:13.0-3, full speed
 3 [Audigy         ]: Audigy - SB Audigy 1 [SB0090]
                      SB Audigy 1 [SB0090] (rev.3, serial:0x511102) at 0xdc00, irq 22
```I get rid of the previous failed attempt

```
sudo mv /etc/asound.conf /etc/asound.conf.old
```So I think I might be getting the hang of this now, the doc says to create 

```
sudo nano /etc/modprobe.d/alsa-base{/CODE]

Consulting [http://alsa-project.org/main/index.php/Matrix:Main](http://alsa-project.org/main/index.php/Matrix:Main) for my Audigy's ALSA support module and trolling through the files that came up earlier in this thread like  "cat /proc/asound/cards" again I make the file alsa-base

[CODE]# ALSA config file
# controls order of PCI soundcards, USB audio and MIDI
# ref https://help.ubuntu.com/community/UbuntuStudio/UsbAudioDevices

alias snd-card-0 snd-emu10k1
alias snd-card-1 snd-usb-audio
alias snd-card-2 snd-usb-audio
alias snd-card-3 snd-hda-intel

# set desired ALSA driver to be HW:0
options emu10k1 index=0

# set USB devices to desired order
# USB webcam (audio) first, then USB MIDI controller
options snd-usb-audio index=1,2 vid=0x46d,0x041e \
pid=0x81d,0x3f00

# set Acer HDMI Intel audio to last
options snd-hda-intel index=3 vid=0xfe8b \
pid=0xc000

```After restarting, 

```
:~$ cat /proc/asound/cards
 0 [U0x46d0x81d    ]: USB-Audio - USB Device 0x46d:0x81d
                      USB Device 0x46d:0x81d at usb-0000:00:12.2-5, high speed
 1 [Xboard25       ]: USB-Audio - E-MU Xboard25
                      E-MU Systems, Inc. E-MU Xboard25 at usb-0000:00:13.0-3, full speed
 2 [Audigy         ]: Audigy - SB Audigy 1 [SB0090]
                      SB Audigy 1 [SB0090] (rev.3, serial:0x511102) at 0xdc00, irq 22
```

So, that's successfully knocked out that pesky HDMI audio connection, but  fails to stop the other three soundcards from moving around. At least I've improved the odds. 

:~$ uncle
uncle: command not found

---

### Post by sgx on 2012-06-08
Hi, I put the device name found within brackets, in the
qjackctl Input Device/Output Device fields, so if you
type Audigy in that field, it should not switch.

The other two are probably both the xboard25, you could try
booting with it unplugged, and with the Audigy now detected and placed
with uniformity, the kernel will probably send the xboard to the same location each time,
assuming no other usb device was inserted.
Cheers

interesting reading:

[http://www.penguinproducer.com/2011/11/using-multiple-devices-with-jack/](http://www.penguinproducer.com/2011/11/using-multiple-devices-with-jack/)

[http://jackaudio.org/multiple_devices](http://jackaudio.org/multiple_devices)

---

### Post by tehowe on 2012-06-08
> **sgx said:**
> Hi, I put the device name found within brackets, in the
qjackctl Input Device/Output Device fields, so if you
type Audigy in that field, it should not switch.

The other two are probably both the xboard25, you could try
booting with it unplugged, and with the Audigy now detected and placed
with uniformity, the kernel will probably send the xboard to the same location each time,
assuming no other usb device was inserted.
Cheers

interesting reading:

[http://www.penguinproducer.com/2011/11/using-multiple-devices-with-jack/](http://www.penguinproducer.com/2011/11/using-multiple-devices-with-jack/)

[http://jackaudio.org/multiple_devices](http://jackaudio.org/multiple_devices)

On my setup the ordering of the soundcards still refuses to stay put after naming the Jack Input/Output to "Audigy", however your suggestion about unplugging the XBoard on restart was spot on. Since I'd managed to disable the HDMI Audio, unplugging the Xboard and my USB camera before restart forces the Audigy to end up as Sound Card 0, HW:0, and so the proper startup order is to plug those devices in after 12.04 comes up. Ensuring that the JACK sync is cross-connected also means Pulse and JACK play nicely together.

Not an ideal, full-auto solution (why you no work, alsa-base) but one I can definitely live with. Thanks! Solved, unless someone wants to correct me on alsa-base config.

There's a thread on getting MIDI set up properly on this system (Audigy Platinum, XBoard25, Juno106) here as well in case it's of use to anyone. The Audigy MIDI in/out doesn't respond but the XBoard25 can be used a MIDI hub as a workaround. [http://ubuntuforums.org/showthread.php?t=1988834](http://ubuntuforums.org/showthread.php?t=1988834)

---

### Post by chkneater on 2012-08-11
It seems like the only time that jack won't start with the right card (I have one card, onboard which is turned off of course, and the HDMI output to my TV, which for some reason jack detects two HDMI and 3 or 4 ports on my soundcard, dunno why)  I theorize that not STOPping jack before quiting might be part of the problem, but I've come to except the error messages and know right away that it's interfacing with the wrong card... AGAIN!!!

---

