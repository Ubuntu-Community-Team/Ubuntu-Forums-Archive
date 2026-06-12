---
title: "Play vm guest audio through host with GPU passthrough"
date: 2016-12-20
forum: Virtualisation
---

### Post by vanbynight on 2016-12-20
Hi this is my first post so please lower your expectations

I've been using Ubuntu since 14.04 and have a pretty marginal understanding of what I'm doing. However I did get GPU passthrough to work quite nicely with a windows VM which was good up until I started running multiple desktops off one host.

Currently I'm using 16.10 kernel ver 4.8.0-22-generic for my KVM host and have it booting off a USB stick and passing the GPUs to guests for desktop duty. The motherboard is an ASUS X79 Sabertooth with the last bios.
 
Right now I am using a USB sound card to get sound in the VM desktops but this limits playback to one VM at a time (and no front panel audio either which isn't very GF friendly). Earlier today I tried passing through the realtek integrated audio to a guest but it has serious buzzing sounds and is not suitable for desktop use (audio seems like a crap shoot with vt-d). Since this solution didn't work I thought it would be convenient to give the VM an emulated sound card and play the output from that through the host instead.

I started by installing alsa-base on the host and it can play definitely play sounds through the speakers so that much is working. I added an ICH9 sound card to a VM using virt-manager and started it up, the card loaded drivers and appears to be working in the VM but no sound is playing through the host. I'm guessing there are some permissions issues with alsa because I don't actually login to the host on boot or start any kind of x session. I use a mic for team speak so I'd like to keep that functional too if that isn't making it incredibly complicated. 

here's a dump of my sound device on the host using ```
lspci -nnk
```

```
00:1b.0 Audio device [0403]: Intel Corporation C600/X79 series chipset High Definition Audio Controller [8086:1d20] (rev 06)
        Subsystem: ASUSTeK Computer Inc. C600/X79 series chipset High Definition Audio Controller [1043:8436]
        Kernel driver in use: snd_hda_intel
        Kernel modules: snd_hda_intel

```

and ```
aplay -L
```

```
null
    Discard all samples (playback) or generate zero samples (capture)
pulse
    PulseAudio Sound Server
default:CARD=PCH
    HDA Intel PCH, ALC892 Analog
    Default Audio Device
sysdefault:CARD=PCH
    HDA Intel PCH, ALC892 Analog
    Default Audio Device
front:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    Front speakers
surround21:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    2.1 Surround output to Front and Subwoofer speakers
surround40:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Digital
    IEC958 (S/PDIF) Digital Audio Output
dmix:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    Direct sample mixing device
dmix:CARD=PCH,DEV=1
    HDA Intel PCH, ALC892 Digital
    Direct sample mixing device
dsnoop:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    Direct sample snooping device
dsnoop:CARD=PCH,DEV=1
    HDA Intel PCH, ALC892 Digital
    Direct sample snooping device
hw:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    Direct hardware device without any conversions
hw:CARD=PCH,DEV=1
    HDA Intel PCH, ALC892 Digital
    Direct hardware device without any conversions
plughw:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    Hardware device with all software conversions
plughw:CARD=PCH,DEV=1
    HDA Intel PCH, ALC892 Digital
    Hardware device with all software conversions

```


and ```
aplay -l
```

```
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC892 Analog [ALC892 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 1: ALC892 Digital [ALC892 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

I've tried ICH6 ICH9 and ES1370 so far with no luck which is leading me to believe it is a problem with the audio service on the host. Testing with a Linux guest had the same results (sound looks like it is playing in vm just not going to host).

Also, I don't have a monitor with HDMI sound so I can't use the GPU's sound driver in the guests in case anyone is wondering why In have made this so complicated.

---

### Post by DuckHook on 2016-12-20
Welcome to the forums, vanbynight

I am far from having the expertise to help you on the technical front. However, from the general perspective, your setup is far too complicated and therefore far too brittle as well. Let me recap:

[LIST=1]
[*]You boot off a USB stick
[*]But pass through the GPU to guests (which are presumably on your system disk?)
[*]You've mashed multiple desktops onto your host
[*]Run multiple concurrent VMs
[*]Use a USB sound card
[*]Through which you also pass through guest audio
[*]And now want to split some guests off to the system sound card
[*]But wish to also maintain host audio as well
[/LIST]
Does this not strike you as being rather too Rube Goldberg-ish to be at all reliable? Even if you get it all working, what happens if/when it breaks with the next update?

Here are my observations:

[LIST=1]
[*]You are relying way too much on your USB interface, which does not have the proven bus stability to sustain the weight of your demands on it.
[*]You should seek to simplify. Complexity is the enemy of stability. In your case, you must simplify *a lot*.
[*]When running multiple VMs the first rule is: run as simple a host as is humanly possible.
[*]The second rule is: keep the host install as close to default as is humanly possible. Otherwise, you end up breaking multiple VMs trying to accommodate one, and the tail ends up wagging the dog.
[/LIST]
While I don't use KVM, the above is not VM-dependent, but applies universally.

If you continue to want tweaks and changes in order to make this convoluted pretzel work, then others will have to jump in here. While I also run multiple VMs, it is based on the KISS philosophy I've outlined, and I do not have the skill to untangle what you've described.

---

### Post by vanbynight on 2016-12-26
Thanks Duck hook

After reading up on common problems with audio passthrough nothing obvious has come up. However I did observe that an Ubuntu vm has crystal clear audio when using the default snd_hda driver. 

Seeing how the snd_hda driver is working fine I though reverting to an older/generic driver in my windows vm be might help make the Realtek audio work. I had no luck installing older Realtek drivers on the windows guest. I think the next thing to check is if windows is using MSI interrupts instead of the legacy type. I'll check and see if the Ubuntu vm is using MSI interrupts for the sound card and try and force windows to match its setup.

---

