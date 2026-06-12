---
title: "alsa-base.conf set audio card as device 0"
date: 2009-11-05
forum: Ubuntu Studio
---

### Post by jeebustrain on 2009-11-05
I'm still working on getting my x64 Karmic studio working. Now I'm running into an issue around my multiple midi/audio devices. Everytime I reboot, the IDs change on all my hardware. This is an output of cat /proc/asound/cards:
```

 0 [U49            ]: USB-Audio - USB Axiom 49
                      M-Audio USB Axiom 49 at usb-0000:00:13.2-2, full speed
 1 [Anniv          ]: USB-Audio - MIDISPORT 4x4 Anniv
                      M-Audio MIDISPORT 4x4 Anniv at usb-0000:00:13.0-2, full speed
 2 [Finger         ]: USB-Audio - USB Trigger Finger
                      M-Audio USB Trigger Finger at usb-0000:00:13.4-1, full speed
 3 [M1010          ]: ICE1712 - M Audio Delta 1010
                      M Audio Delta 1010 at 0xe800, irq 21

```

Ideally, I'd like the Delta1010 as hw0. The order of the other items doesn't really matter much to me, though it'd be nice to set them to be the same order. 

I know I have to edit /etc/modprobe.d/alsa-base.conf. I tried adding this at the bottom

options snd-ice1712 index=0

But it doesn't seem to do anything. I haven't changed anything else in the file (it's all default). Is there something else I need to change? I've been trying to find some examples online but I haven't found anything that I've been able to use.

---

### Post by AutoStatic on 2009-11-06
Besides the line *options snd-ice1712 index=0* you have to add extra lines for the USB devices. Could you post the output of **lsusb** with everything attached?

---

### Post by jeebustrain on 2009-11-06
thanks for the reply - here's the output of both lsusb and lspci 
(note: I had to walk my wife through this from work and she emailed me screenshots. I used MS OneNote here at work to extract the text, so there might be a typo here and there)

```

brainstem@coltrane:-$ lsusb

Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID ld6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 0763:0117 Midiman Trigger Finger
Bus 006 Device 001: ID ld6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 006: ID 046d:c222 Logitech, Inc. G15 Keyboard / LCD
Bus 004 Device 005: ID 046d:c508 Logitech, Inc. Cordless Trackball
Bus 004 Device 004: ID 046d:c221 Logitech, Inc. G15 Keyboard / Keyboard
Bus 004 Device 003: ID 0763:0199 Midiman Axiom 49
Bus 004 Device 002: ID 046d:c223 Logitech, Inc. G15 Keyboard / USB Hub
Bus 004 Device 001: ID ld6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 007: ID 0409:0058 NEC Corp. HighSpeed Hub
Bus 001 Device 001: ID ld6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 0763:1060 Midiman
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

brainstem@coltrane:-$ lspci

00:00.0 Host bridge: ATI Technologies Inc RD790 Northbridge only dual slot PCI-e_GFX and HT3 K8 part 
00:02.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (external gfx0 port A) 
00:04.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (PCI express gpp port A) 
00:06.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (PCI express gpp port c) 
00:07.0 PCI bridge: aTI Technologies Inc RD790 PCI to PCI bridge (PCI express gpp port D) 
00:12.0 SaTA controller: aTI Technologies Inc sB600 Non-Raid-5 saTA 
00:13.0 USB Controller: ATI Technologies Inc sB600 USB (OHCI0) 
00:13.1 USB controller: ATI Technologies Inc sB600 USB (OHCI1) 
00:13.2 usB Controller: ATI Technologies Inc SB600 USB (OHCI2) 
00:13.3 usB controller: ATI Technologies Inc SB600 uSB (OHCI3) 
00:13.4 UsB controller: ATI Technologies Inc SB600 USB (oHC14) 
00:13.5 USB Controller: aTI Technologies Inc SB600 USB Controller (EHCI) 
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14) 
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE 
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge 
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge 
00:18.0 Host bridge: Advanced Micro Devices [AMD] KB [Athlon64/Opteron] HyperTransport Technology Configuration 
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteronl Address Map 
00:18.2 Host bridge: Advanced Micro Devices [AMD] KB [Athlon64/Opteronl DRAw Controller 
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athton64/Opteron] Miscellaneous Control 
01:00.0 vGA compatible controller: nVidia Corporation G94 [GeForce 9600 GTJ (rev a1) 
02:00.0 IDE interface: Marvell Technology Group Ltd. 88sE6121 saTA II Controller (rev b1) 
03:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet controller (rev 12) 
04:00.0 IDE interface: Marvell Technology Group Ltd. 88SE6121 SATA II Controller (rev b2) 
05:06.0 Multimedia audio controtler: vIA Technologies Inc. 1CE1712 [Envy24] PCI Multi-channel I/O Controller (rev 02) 
05:08.0 FireWire (IEEE-1394): Agere Systems FW322/323 (rev 70) 

```

---

### Post by VertexPusher on 2009-11-06
> **jeebustrain said:**
> I'm still working on getting my x64 Karmic studio working. Now I'm running into an issue around my multiple midi/audio devices. Everytime I reboot, the IDs change on all my hardware. This is an output of cat /proc/asound/cards:
```

 0 [U49            ]: USB-Audio - USB Axiom 49
                      M-Audio USB Axiom 49 at usb-0000:00:13.2-2, full speed
 1 [Anniv          ]: USB-Audio - MIDISPORT 4x4 Anniv
                      M-Audio MIDISPORT 4x4 Anniv at usb-0000:00:13.0-2, full speed
 2 [Finger         ]: USB-Audio - USB Trigger Finger
                      M-Audio USB Trigger Finger at usb-0000:00:13.4-1, full speed
 3 [M1010          ]: ICE1712 - M Audio Delta 1010
                      M Audio Delta 1010 at 0xe800, irq 21

```Ideally, I'd like the Delta1010 as hw0.
Forget card numbers. As you can see in the list above, each card also has a name. And card names never change.

So if you want Jack to always connect to the Delta card, don't enter "hw:0" but "hw:M1010" instead. This also works for subdevices, e.g. "hw:M1010,1" instead of "hw:0,1".

---

### Post by jeebustrain on 2009-11-06
> **VertexPusher said:**
> Forget card numbers. As you can see in the list above, each card also has a name. And card names never change.

So if you want Jack to always connect to the Delta card, don't enter "hw:0" but "hw:M1010" instead. This also works for subdevices, e.g. "hw:M1010,1" instead of "hw:0,1".


hmm.. interesting. so what would be the syntax I would use in the alsa-base.conf?

---

### Post by VertexPusher on 2009-11-06
> **jeebustrain said:**
> hmm.. interesting. so what would be the syntax I would use in the alsa-base.conf?
Don't edit that file. Just enter "hw:M1010" in Jack's preferences window.

---

### Post by jeebustrain on 2009-11-06
genius! thanks, I'll be sure to try that tonight.

---

### Post by AutoStatic on 2009-11-06
Cool! Didn't know that, that's a way better solution.

---

### Post by jeebustrain on 2009-11-08
great! I tried it yesterday and it worked perfectly. 

Unofortunately I seemed to have blown up gnome and xorg by updating my nvidia drivers to the newest 190s. So I'm going to spend a couple hours trying to clean it up (been trying to re-add everything via console but running into lots of dependency errors) and if I can't get it working soon, I'm just going to blow it up and start over with a fresh (non-RC) version of Karmic.

---

### Post by paddedcell on 2009-11-08
Yea, I had to use the alpha numeric in my .asoundrc to get the multi working. Great!!

iain

---

### Post by foresto on 2009-11-12
My /etc/modprobe.d/alsa-base settings stopped working properly when I upgraded to Karmic.  Rather than figuring out a new syntax, I set my default sound card using the asoundconf program.  It created ALSA config files in my home directory, which is much less intrusive than editing kernel module configuration files.

Unfortunately, asoundconf seems to have disappeared in Karmic, but it may make a reappearance according to this bug report:
[https://bugs.launchpad.net/ubuntu/+source/asoundconf-gtk/+bug/378675](https://bugs.launchpad.net/ubuntu/+source/asoundconf-gtk/+bug/378675)

I couldn't wait, so I grabbed it from one of the source code repositories.  It's a self-contained python program, so packaging wasn't an issue.
[https://code.launchpad.net/asoundconf-ui](https://code.launchpad.net/asoundconf-ui)

---

### Post by VertexPusher on 2009-11-13
I always edit my .asoundrc file manually. Once you know the syntax, you can do quite interesting things with it. For example, I have a normal soundcard (Intel HDA) and a webcam microphone which I use most of the time (for Skype, Google Talk, SLVoice). So instead of selecting the webcam mic in each application, I defined a default PCM device using the normal soundcard for playback and the webcam mic for recording:
```
pcm.!default {
    type asym
    playback.pcm {
        type plug
        slave.pcm dmix:NAME_OF_SOUNDCARD
    }
    capture.pcm {
        type plug
        slave.pcm dsnoop:NAME_OF_WEBCAM
    }
}
```
"plug" is a sample rate converter. "dmix" is a stream mixer. "dsnoop" enables multiple applications to access the microphone simultaneously. If you prefer exclusive access, replace "dsnoop" with "hw".

---

### Post by markbuntu on 2009-11-13
jack now uses dbus, which makes available the names of devices which is why you can set the hw: by name. asoundconf is being deprecated along with a lot of other alsa stuff like dmix and dsnoop etc. Do not expect these things to work for much longer and do not expect you can install them in the future without breaking other stuff.

---

