---
title: "VMPlayer, XP guest, sound problem"
date: 2010-07-26
forum: Virtualisation
---

### Post by r_avital on 2010-07-26
Hi folks,

I know this has probably been discussed to death, and I did find some tips here and elsewhere, applied them, and the problem persists.

Host OS: Lucid 64-bit
Guest OS: Windows XP Pro 64-bit
VMWare Player version:3.1.0 build-261024

Sound works ok in Host.  lspci -v returns the following output relevant to the sound card:
```

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
        Subsystem: Micro-Star International Co., Ltd. Device 42cd
        Flags: bus master, slow devsel, latency 64, IRQ 16
        Memory at fd5f4000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel
...
01:00.1 Audio device: ATI Technologies Inc RV630/M76 audio device [Radeon HD 2600 Series]
        Subsystem: Micro-Star International Co., Ltd. Device aa08
        Flags: bus master, fast devsel, latency 0, IRQ 19
        Memory at fd6ec000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel


```XP-pro-64 guest is otherwise running fine.  In XP, under control-panel ->system -> device manager, under "Sound, video and game controllers" I have:
Audio Codecs
Legacy Audio Drivers
Legacy Video Capture Devices
Media Control Devices
Video Codecs
VMware VMaudio (VMAUDIO) (WDM)

That last one, when I look at the properties, the screen reports "this device is running properly."

In the VM's .vxd file, the lines pertaining to sound are:
sound.present = "TRUE"
sound.virtualDev = "es1371"
sound.filename = "-1"
sound.autodetect = "TRUE"
... and a bit further down:
sound.pciSlotNumber = "34"

In the VMware Player status bar, the config for the sound card is auto-detect, connected, and connect at power-on.

I've shut down the XP guest and restarted it.

After all this, trying to play a simple .wav file produces an error:  Windows cannot play xxxxx.wav, the sound card may be in use.

Any thoughts?  What did I miss?

I do understand that I need to disable the sound card for the host, in order to allow the guest to use it.  I was expecting that to be handled by the VMware Player.  Was I wrong?  If I need to do this manually, how do I disable/re-enable sound in Lucid?  

Running sudo service --status-all returns a + next to pluseaudio, and a ? next to alsa-mixer-save.  I have no other alsa entry in the output.

Thanks in advance

---

### Post by r_avital on 2010-07-26
OK, solved the problem:  The culprit was the Guest, XP - 

in Control Panel -> Sound ->Audio tab, sound playback default device: Make sure it's set to VMware VMaudio 

Duh.  It was on Line #1 Modem, which it was NEVER set to before.   How it got there, is another mystery I don't care to chase after.

And it gets funnier still - just for grins I tried to play sounds on both host and guest simultaneously, and they played.

Go Figure.

---

