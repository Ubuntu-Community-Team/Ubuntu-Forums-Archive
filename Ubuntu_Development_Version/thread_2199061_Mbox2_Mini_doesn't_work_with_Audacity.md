---
title: "Mbox2 Mini doesn't work with Audacity"
date: 2014-01-11
forum: Ubuntu Development Version
---

### Post by Bucky Ball on 2014-01-11
**** This is now resolved. See page 3, post #22. ***

Hi all,

Using 14.04 minimal install with xfce4, Audacity 2.0.5 and this kernel:

3.13.0-2-generic

I plug in the Mbox and dmesg gives me the read out: 
```

[ 6732.317601] usb 2-1.1: Product: Mbox 2 
[ 6732.317604] usb 2-1.1: Manufacturer: Digidesign
[ 6732.317607] usb 2-1.1: SerialNumber: Digidesign
[ 6732.391436] usb-audio: Sending Digidesign Mbox 2 boot sequence...
[ 6732.895463] usb-audio: device not ready, resending boot sequence...
[ 6733.399245] usb-audio: device not ready, resending boot sequence...
[ 6733.903046] usb-audio: device not ready, resending boot sequence...
[ 6734.406828] usb-audio: device not ready, resending boot sequence...
[ 6734.910609] usb-audio: device not ready, resending boot sequence...
[ 6735.414430] usb-audio: device not ready, resending boot sequence...
[ 6740.918758] usb-audio: Digidesign Mbox 2: 24bit 48kHz
[ 6740.921732] usbcore: registered new interface driver snd-usb-audio
```

That may or may not be good, unsure. When I choose the Mbox in Audacity and attempt to record I get the attached screenshot error. 

There are other issues with Audacity in 14.04, but I'll start here. The Mbox is sitting there with its green light on and looking quite happy. Doesn't crash the computer (as it did in earlier releases), but is just not operational with Audacity. Haven't tried with anything else. The odd thing is that I installed the 13.04 kernel in 12.04 sometime ago (the drivers for the MBox are in that kernel but not 12.04) and it worked perfectly. Tried a few months later and nothing, same error as this.

---

### Post by Bucky Ball on 2014-01-12
PS: The MBox2 also doesn't show in Pulseaudio Volume Cortrol. It does in my other (12.04) installs but I get the same error (from memory or something similar) with Audacity.

... and the sample rate is fine.

* Update: When I set it to 'default' I can record, but there is a bunch of noise occurring. Oddly, I can't hear that through the headphones, only see it on the levels. :-k 

See attached screenshot for noise.

PS: I take that back. I think the MBox2 is showing up in PAVolume control, but as 'Integrated Rate Matching Hub Analogue Stereo'. ?

---

### Post by Bucky Ball on 2014-01-13
Still battling away with this. But wait, there's more. From 'aplay -L':

```
sysdefault:CARD=M2
    Mbox 2, USB Audio
    Default Audio Device
front:CARD=M2,DEV=0
    Mbox 2, USB Audio
    Front speakers
surround40:CARD=M2,DEV=0
    Mbox 2, USB Audio
    4.0 Surround output to Front and Rear speakers
surround41:CARD=M2,DEV=0
    Mbox 2, USB Audio
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=M2,DEV=0
    Mbox 2, USB Audio
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=M2,DEV=0
    Mbox 2, USB Audio
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=M2,DEV=0
    Mbox 2, USB Audio
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=M2,DEV=0
    Mbox 2, USB Audio
    IEC958 (S/PDIF) Digital Audio Output
dmix:CARD=M2,DEV=0
    Mbox 2, USB Audio
    Direct sample mixing device
dsnoop:CARD=M2,DEV=0
    Mbox 2, USB Audio
    Direct sample snooping device
hw:CARD=M2,DEV=0
    Mbox 2, USB Audio
    Direct hardware device without any conversions
plughw:CARD=M2,DEV=0
    Mbox 2, USB Audio
    Hardware device with all software conversions
```

This is just the section concerning the MBox2. There's a lot more besides about the other devices. 

See attached alsamixer pic: 'This sound device does not have any controls' for the MBox2, although it does show controls under Pulseaudio V Control under the heading 'Integrated Rate Matching Hub Analogue Stereo'. I get no action on the level meters except for a heap of noise showing on the input tab which I can't hear either through the computer or the MBox2. (Pic #2) Truly baffled. :-k

Still digging. Any required info just ask.

PS: If I launch Audacity from a terminal and set the input and output device to the MBox2 and hit record, this is the error message:

```
Expression 'hostFormat = PaUtil_SelectClosestAvailableFormat( availableFormats, parameters->sampleFormat )' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 1720
Expression 'hostFormat = PaUtil_SelectClosestAvailableFormat( availableFormats, parameters->sampleFormat )' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 1720
```

I have looked for 'src/hostapi/alsa/pa_linux_alsa.c' but can't find the file/directory.

PPS: And a little more grist for the mill; the output of alsa-base.conf:

```
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-caiaq index=-2
options snd-usb-ua101 index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
# Keep snd-usb-audio from beeing loaded as first soundcard
options snd-usb-audio **index=-2**
```

'index=-2' which I have marked in bold on the last line of the output I tried changing to '-1'. No diff.

---

### Post by Bucky Ball on 2014-01-14
... and another clue:

```
cat /proc/asound/cards 
 0 [MID            ]: HDA-Intel - HDA Intel MID
                      HDA Intel MID at 0xd6100000 irq 44
 1 [HDMI           ]: HDA-Intel - HDA ATI HDMI
                      HDA ATI HDMI at 0xd6010000 irq 46
 2 [M2             ]: USB-Audio - Mbox 2
                      Digidesign Mbox 2 at **usb-0000:00**:1d.0-1.1, full speed
```

The section in bold in the last line tells me something. Shouldn't it be showing usb number? So, to the output of 'lsusb':

```
Bus 002 Device 004: ID 046d:c52e Logitech, Inc. 
**Bus 002 Device 003: ID 0dba:3000 ** 
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 04f2:b128 Chicony Electronics Co., Ltd 
Bus 001 Device 003: ID 0930:0508 Toshiba Corp. Integrated Bluetooth HCI
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

'Bus 002 Device 3' is where it should be showing up I think, so I have the identifier number-wise for the device. So the MBox2 is kinda half recognised. At this point:

alsa recognises it, names it as the MBox2, but won't show controls;
PAVControl shows it under a different name;
lsusb doesn't show it but has a the numbers ...

No doubt this will get ironed out in a future update, but I may as well keep a record of my progress with it on 14.04 LTS here as I go. Might provide some tips for future travellers.

---

### Post by Bucky Ball on 2014-01-14
After some more research, I edited /etc/modprobe.d/alsa-base.conf, commented out anything with 

```
options snd-usb-audio index=-2
```

as that can apparently prevent the USB device from getting not just 2 but any slot, then I added the last six lines at the end of the file underneath '# My options for the default setup' (which are commented out because they didn't work; they made the MBox2 vanish, didn't check other audio) . 

```
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
# options snd-usb-audio index=-2
options snd-usb-caiaq index=-2
options snd-usb-ua101 index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
# Keep snd-usb-audio from beeing loaded as first soundcard
[b]# options snd-usb-audio index=-2
# options snd-usb-audio index=2 vid=0dba \ pid=3000
# My options for the default setup
# alias snd-card-0 snd-hda-intel
# alias snd-card-1 snd-hda-ati
# alias snd-card-2 snd-usb-audio
# options snd-hda-intel index=0
# options snd-hda-ati index=1
# options snd-usb-audio index=2 vid=0dba pid=3000[/b]
```

The stuff at the bottom of the file in bold is what I've tried at various times. All ideas gratefully accepted.

PS: Just to mention something else I noticed: being a minimal install I have neither libav-tools or ffmpeg installed. Perhaps that is preventing the MBox from being correctly recognised?

---

### Post by QDR06VV9 on 2014-01-14
Try this It worked for me.
_Just above the line_ <# Prevent abnormal drivers from grabbing index 0>
I had to add This
```
*options snd_hda_intel index=1*
```
Then I rebooted.
From here [http://ubuntu4me.blogspot.com/2012/03/ubuntu-default-sound-card-select.html](http://ubuntu4me.blogspot.com/2012/03/ubuntu-default-sound-card-select.html)
Just read this from your last post
```
I have neither libav-tools or ffmpeg installed. Perhaps that is preventing the MBox from being correctly recognised?
```
I do have those installed!

---

### Post by Bucky Ball on 2014-01-14
@runrickus: Thanks. Would be handy if I was having trouble getting my default card picked up, but I'm not. Your suggestions and link have given me a few ideas though so I'm going to investigate some more. 

This:[QUOTE=runrickus]

Just above the line <# Prevent abnormal drivers from grabbing index 0>[/QUOTE]

... makes me think I should try my option lines where you suggest, above that line.

* Update: And I did. My latest escapade ...

```
# My New experiment ...
# alias snd-card-0 snd-hda-intel
# alias snd-card-1 snd-hda-intel
# alias snd-card-2 snd-usb-audio
# alias snd-card-3 snd-usb-audio
# options snd-hda-intel index=0
# options snd-hda-intel index=1
# options snd-usb-audio index=2 vid=0dba pid=3000
# options snd-usb-audio index=3 vid=0dba pid=3000
```

Didn't work (which is why they're commented out). Leaves the MBox switched off, although regular audio working fine.

* Further update: I tried the low latency kernel

3.11.0-11-lowlatency

... as I thought it might overcome the 'Error while opening sound device. Please check the input device settings and the project sample rate' issue. It didn't. :-k

---

### Post by Bucky Ball on 2014-01-14
Just spotted something:
```

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: MID [HDA Intel MID], device 0: ALC272 Analog [ALC272 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: M2 [Mbox 2], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

Card 0 and card 2 are both device 0. I'm thinking this is wrong.

---

### Post by QDR06VV9 on 2014-01-14
BuckyBall Maybe just maybe this will shed some info
[http://www.zamaudio.com/?p=97](http://www.zamaudio.com/?p=97)
Hope you get this working I am interested in the Mbox

---

### Post by Bucky Ball on 2014-01-14
Thanks for that but was my first port of call about a year ago. The driver (great work from the developer) has been accepted into alsa and is built in to the kernel now so these instructions aren't necessary for the more recent kernels. I have a feeling this is something to do with 14.04 being a bit undercooked for now and hoping it will come together as the release gets closer.

The driver has been in the kernel since the 3.9 kernel from memory. I installed that kernel in a 12.04 install about a year ago, the MBox2 worked faultlessly with Audacity, I forgot about it and when I tried to use it again with that kernel about six months later, nothing. Couldn't get it to work. 

I'll keep plugging away as being able to record things 'on the fly' using Ubuntu and via the MBox is a vital missing piece of the puzzle for me and Ubuntu. I'm a musician and musicologist so I'm not just doing this for the heck of it. I need to boot into Windows for anything audio and I'd rather not. I use Ubuntu for everything else. ;)

PS: The MBox2 is a great little piece of technology, vastly improved by the fact that it can (apparently) be used with Linux now and one is no longer locked into the Mac/Windows/ProTools loop with the device. It is old, but perfect for my needs (I also have an eight channel audio interface running on the desktop but not exactly portable and booting the desktop and Ardour to record one compositional idea on an acoustic guitar is overkil ... besides, by the time all that's up and running there's a good chance I would have forgotten what I wanted to record ... an occupational hazard!).

---

### Post by Bucky Ball on 2014-01-14
Just for an experiment, I tried the MBox in the 3.9.0-030900-generic kernel with 12.04. It worked perfectly with kernel once, when I tried it out about a year ago, but has never done so since. This time no different. Hit record with the MBox set as input and output device in Audacity and exactly the same error message I'm getting in 14.04; 'Error while opening sound device. Please check the input device settings and the project sample rate.' I've checked again and again and it is set to 24bit/48khz, just like the MBox. :-k

---

### Post by Bucky Ball on 2014-01-15
After update to kernel 3.13.0-3-generic I am getting a little further. 

```
[  108.515195] usb 2-1.1: new full-speed USB device number 4 using ehci-pci
[  108.640510] usb 2-1.1: config 1 interface 2 has no altsetting 1
[  108.640515] usb 2-1.1: config 1 interface 3 has no altsetting 1
[  108.640519] usb 2-1.1: config 1 interface 4 has no altsetting 1
[  108.640521] usb 2-1.1: config 1 interface 5 has no altsetting 1
[  108.645245] usb 2-1.1: New USB device found, idVendor=0dba, idProduct=3000
[  108.645250] usb 2-1.1: New USB device strings: Mfr=1, Product=2, SerialNumber=1
[  108.645253] usb 2-1.1: Product: Mbox 2 
[  108.645256] usb 2-1.1: Manufacturer: Digidesign
[  108.645259] usb 2-1.1: SerialNumber: Digidesign
[  108.723160] usb-audio: Sending Digidesign Mbox 2 boot sequence...
[  109.226769] usb-audio: device not ready, resending boot sequence...
[  109.730348] usb-audio: device not ready, resending boot sequence...
[  110.233866] usb-audio: device not ready, resending boot sequence...
[  110.737360] usb-audio: device not ready, resending boot sequence...
[  111.240906] usb-audio: device not ready, resending boot sequence...
[  111.744668] usb-audio: device not ready, resending boot sequence...
[B][  117.245576] usb-audio: Digidesign Mbox 2: 24bit 48kHz
[  117.248590] usbcore: registered new interface driver snd-usb-audio[/B]
```

These last two lines in bold weren't there before, dmesg was ending with '[  111.744668] usb-audio: device not ready, resending boot sequence...'. Hasn't changed anything else, though. I'm convinced there must be a tweak somewhere to get the MBox recognised because it is recognised when I plug in. My guess is somewhere in 'alsa-base.conf'. What I've tried in there so far is not quite right, perhaps.

---

### Post by QDR06VV9 on 2014-01-15
> **Bucky Ball said:**
> 

The driver has been in the kernel since the 3.9 kernel from memory. I installed that kernel in a 12.04 install about a year ago, the MBox2 worked faultlessly with Audacity, I forgot about it and when I tried to use it again with that kernel about six months later, nothing. Couldn't get it to work. 

That has been the case for three others I know that use Mbox2, I will follow this Thread with great interest;)
Thanks for the updates.

---

### Post by Bucky Ball on 2014-01-15
Cut a long story short, one of the comments on the Zamaudio thread said that updating the MBox firmware should fix some issues, and I'm hoping this one. So, a merry chase was had attempting to find the correct firmware update. I've had the MBox since 2007 and never updated and there are new updates, but they need to be installed in XP. No problem. Just reinstalled XP on my audio box so download firmware update 1.43 but won't install. Throws an error that a .dll file is missing. Search for a fix for that. None can I find.

So, look for earlier version that might work. Find one. Launches fine and looking promising, but message saying needs Pro-Tools installed to continue. I would normally have Pro-Tools installed on the desktop, but have just done an overhaul, reinstalled XP and Xubuntu, but not configured. Windows hasn't even got a PDF reader yet. Phew.

This is getting off the track of Ubuntu and 14.04 but just saying where I'm at with it. At the end of three or four hours of screwing around with Windows. To bed and start afresh tomorrow by installing Pro-Tools on the XP box and trying again ...

---

### Post by Bucky Ball on 2014-01-16
Managed to update the MBox firmware from 140 to 143. No different. I have read mention on a 22 firmware updater but can't find that, despite hours of hunting it down ...

---

### Post by Bucky Ball on 2014-01-16
* Update: I think I'm getting somewhere!

I muttered an incantation, spun around four times, performed a magic ritual facing the moon and got this at the end of 'dmesg' after plugging the MBox 2 Mini in:

```
[   26.104179] usb-audio: Digidesign Mbox 2: 24bit 48kHz
[   26.107274] usbcore: registered new interface driver snd-usb-audio
[   45.560223] 3:4:2: cannot set freq 48000 to ep 0x85
[  106.300580] retire_capture_urb: 183 callbacks suppressed
[  106.526380] usb 2-1.1: USB disconnect, device number 3
```

Not sure what changed, but I noticed I had left a couple of lines of my experimental code in /etc/modprobe.d/alsa-base.conf so commented them out, changed the USB cable and the port I was plugging into (the other was an eSATA/USB combo port), upgraded firmware to 143, as mentioned previously, plugged in the MBox and got that output.

The new output info explains a lot, not that I'm any the wiser as to how I fix it, but it has confirmed a few things, the last three lines in particular.

```
[   45.560223] 3:4:2: cannot set freq 48000 to ep 0x85
```

Could explain why I am getting the message with Audacity:

> Error while opening sound device. Please check the input device settings and the project sample rate.

I have Audacity set for the correct frequency (48khz and 24bit; the Linux driver is apparently locked to this) but when I plug in the MBox 'cannot set freq 48000'. So naturally there's a problem. These two things appear to be connected.

As for it not being picked up in PAVControl and having 'no controls' in alsamixer:

```
usb 2-1.1: USB disconnect, device number 3
```

The lights are on but nobodies home. The MBox is plugged in, which is probably why it's detected, at least by alsamixer and Audacity, but is disconnected, which is why nothing can access its controls and PAVControl doesn't show it or any controls for it.

Well there's plenty to research there. Better get to it! Again! ...

PS: I think I will try to get this working on a released kernel running in 12.04 and post a new thread in ***Multimedia & Video ***about this as a) it might see more action and, b) I'm unsure if these issues are 14.04 specific. I'll post a link to any new thread here if/when I do create one, runrickus, as I know you want to follow. ;)

---

### Post by QDR06VV9 on 2014-01-16
> **Bucky Ball said:**
> * Update: I think I'm getting somewhere!

_I muttered an incantation, spun around four times, performed a magic ritual facing the moon_ **and got this** at the end of 'dmesg' after plugging the MBox 2 Mini in:
PS: I think I will try to get this working on a released kernel running in 12.04 and post a new thread in ***Multimedia & Video ***about this as a) it might see more action and, b) I'm unsure if these issues are 14.04 specific. I'll post a link to any new thread here if/when I do create one, runrickus, as I know you want to follow. ;)
Some times thats the only way I can get things just to work:Dlol
Thanks for posting your research!! I will also keep a keen eye on your ***Multimedia & Video thread.:)***
Regards

---

### Post by Bucky Ball on 2014-01-19
I'll leave this open and get back to as things progress with 14.04, but for the moment I have been attempting to get it working in 12.04. I can confirm that in 12.04, after running this:

```
git clone [https://github.com/zamaudio/alsa-driver.git](https://github.com/zamaudio/alsa-driver.git)
cd alsa-driver
git checkout mbox2
cd alsa
./gitcompile
sudo make install
```

... from the excellent work done by Damien Zammit on the [Zamaudio site]("http://www.zamaudio.com/?page_id=170"), the MBox 2 Mini is recognised and running in full duplex. All controls are working: I have a guitar and headphones into the MBox and it is crystal clear. Unfortunately, still not recognised as having any controls and can't record in Audacity. 

I have posted a thread regarding my hijinks with the MBox and 12.04 [HERE]("http://ubuntuforums.org/showthread.php?t=2200411&p=12904379#post12904379").

As for this thread, I'm not convinced that the problems are 14.04 specific and it is better to try to get it working on a stable system so I have some comparison. I have at least established that the MBox driver from Zamaudio, now part of alsa so the MBox should be working out of the box in newer releases, is not working on 14.04. There are similarities in what is happening in the two releases, but I can't say anything apart from the behaviour of the driver is specifically 14.04 related at this point. 

Tempted to give the Zamaudio method above a go in 14.04 to see if it works, but would rather leave the install untouched and on dailies to see how it develops and if this is actually resolved without my intervention (and how 14.04 develops generally). I will also look into posting a bug maybe as this should be working ootb. ;)

---

### Post by QDR06VV9 on 2014-01-19
> **Bucky Ball said:**
> I'll leave this open and get back to as things progress with 14.04, but for the moment, I have moved to attempt to get it working in 12.04. I can confirm that in 12.04, after running this:

```
git clone [https://github.com/zamaudio/alsa-driver.git](https://github.com/zamaudio/alsa-driver.git)
cd alsa-driver
git checkout mbox2
cd alsa
./gitcompile
sudo make install
```

... from the excellent work done by Damien Zammit on the [Zamaudio site]("http://www.zamaudio.com/?page_id=170"), the MBox 2 Mini is recognised and running in full duplex. All controls are working: I have a guitar and headphones into the MBox and sounds crystal clear. Unfortunately still not recognised as having any controls and can't record in Audacity. 

Have now headed back to 12.04 for further experimentation with this and posted a thread about the MBox and 12.04 [HERE]("http://ubuntuforums.org/showthread.php?t=2200411&p=12904379#post12904379"). As for this thread, I have at least established that the MBox driver from Zamaudio, now part of alsa so the MBox should be working out of the box in newer releases, is not working on 14.04. I can't proceed with this until the device is connecting properly and I am at least getting audio, even if I can't record with it. There are similarities in what is happening in the two releases, but I can't say anything apart from the driver issue is specifically 14.04 related at this point. 

Tempted to give the Zamaudio method above a go in 14.04 to see if it works, but would rather leave the install untouched and on dailies to see how it develops and if this is actually resolved without my intervention. I will also look into posting a bug maybe as this should be working ootb. ;)
Bucky Ball
I found this with some more looking
```
The current status in the mainline kernel is that playback is supported  but users have reported issues with loud static noises appearing  sporadically. [COLOR=#ff0000]Capture is not supported currently at all[/COLOR].
```
From here [http://www.zamaudio.com/?p=953](http://www.zamaudio.com/?p=953) 
Trying to get hold of friend now to see if he has any more input on this.
Thanks for the second link for your thread;)

---

### Post by Bucky Ball on 2014-01-19
That link is about the original MBox. Different beast, different driver. This is a an MBox 2 Mini, second generation (there was also a third, which is mentioned on that link). ;)

This is for MBox 2 (the regular MBox 2 driver works for the Mini also):

[http://www.zamaudio.com/?p=97](http://www.zamaudio.com/?p=97)

---

### Post by QDR06VV9 on 2014-01-19
Mea Culpa Just saw that! Been reading on it for while now.

---

### Post by Bucky Ball on 2014-01-20
Confirmed. The MBox 2 Mini works using Ubuntu 14.04 LTS minimal install kernel 3.13.0-4-generic running xfce4! Whether I was doing something wrong or the latest updates fixed it I've no idea, but disregard previous comments to the contrary; the driver is working in 14.04 and it's working sweetly, and here's what I did.

QJactl:

1/ Boot up, plug in the MBox, check that the last couple of lines of output from dmesg identify the MBox 2 Mini:

```

[  358.301960] usb-audio: Digidesign Mbox 2: 24bit 48kHz
[  358.304940] usbcore: registered new interface driver snd-usb-audio
```

and are NOT 'device not ready, resending boot sequence...'. Confirmation can take a little while so keep checking: if it never comes the driver is not working or something else is wrong;

2/ Launch QJackctl, unconnect everything in 'Connections' and 'Patchbay';
3/ Open 'Setup'. See first attached pic for mine; 
4/ At the far right of the 'Input' and 'Output' device section there is an '>' which, when clicked, gives you device options; 
5/ You should have 'hw:M2,0' in there ('USB audio') and that's the MBox (as in my pic).

If that doesn't work (you'll find out later) the last number could be different (meaning hw:M2,*) so experiment by typing things into the input/output device sections manually rather than choosing a default. This might be an option if 'USB audio' isn't listed in the drop down box as anything, but your 'USB audio' device should be in that list and labelled 'hw:M2,*'. So I imagine whatever you try manually should start with 'hw:M2,'.

Audacity:

1/ Launch QJackctl and start jack then Launch Audacity (Audacity wouldn't co-operate with me without jack being started);
2/ See the second pic for the device settings: Jack audio connection kit, system, system, 1 mono channel.
3/ Start recording!

So, as if by magic, all is working fine. Records/plays back in 48kHz/24bit great, and all monitored with headphones plugged directly into the MBox. Fantastic! I bought the box for the ProTools that came with it seven years ago and have used it about three times! Just so happens that right now (actually, a few years ago) it is perfect for my situation. Thrilled out of my mind.

Good luck future travellers, and thanks to all those working so hard on 14.04 and particularly the Zamaudio people for their tireless work on this driver. It's just made my day. ;)

PS: I can not get the MBox working without having QJackctl launched and started. I.e. I can not get Audacity to work with the MBox directly. The original error occurs. Nothing has changed there. If anyone has any luck with that method (device settings would be 'Alsa; Mbox, Mbox, 1 mono channel') I'd be interested to hear about it.

PPS: Just to confirm that this is still not working in 12.04 Xubuntu with the identical parameters and settings with the git patch for the MBox driver installed. There is no 'hw:M2,0' option in QJackctl 'Setup'.

PPPS: Just to show off, the third pic shows Pulseaudio using the MBox as the output device for VLC playing a 48kHz/24bit FLAC file! Notice the drop down device box says 'Integrated Rate Matching Hub Anaglogue Stereo' Instead of MBox2, which it shows is what it shows in 12.04 and everywhere else. No doubt this will change.

---

### Post by QDR06VV9 on 2014-01-20
Great Stuff Bucky Ball!
Thanks again for posting all your research:popcorn:
I am now on the hunt for Mbox2!!
Regards

---

### Post by Bucky Ball on 2014-01-20
All good. My dinky MBox 2 Mini has no midi in/outs, two channel analogue input only, but by all accounts, midi is working, too for the regular MBox 2, so you might keep that in mind if you're wanting to use midi. 

Have fun! ;)

---

### Post by QDR06VV9 on 2014-01-21
> **Bucky Ball said:**
> All good. My dinky MBox 2 Mini has no midi in/outs, two channel analogue input only, but by all accounts, midi is working, too for the regular MBox 2, so you might keep that in mind if you're wanting to use midi. 

Have fun! ;)
Thanks Again! Been checking all the specs for the Mbox2 models, Decisions Decisions.

---

### Post by Bucky Ball on 2014-01-21
You should pick an old one up pretty cheap I'd think. Here's mine:

[http://www.ebay.com/itm/Digidesign-MBox-M-Box-2-Mini-USB-Interface-/251426475926?pt=US_Computer_Recording_Interfaces&hash=item3a8a2f8f96](http://www.ebay.com/itm/Digidesign-MBox-M-Box-2-Mini-USB-Interface-/251426475926?pt=US_Computer_Recording_Interfaces&hash=item3a8a2f8f96)

You'd possibly find one cheaper. I just grabbed that one with no research. ;)

---

### Post by QDR06VV9 on 2014-01-21
> **Bucky Ball said:**
> You should pick an old one up pretty cheap I'd think. Here's mine:

[http://www.ebay.com/itm/Digidesign-MBox-M-Box-2-Mini-USB-Interface-/251426475926?pt=US_Computer_Recording_Interfaces&hash=item3a8a2f8f96](http://www.ebay.com/itm/Digidesign-MBox-M-Box-2-Mini-USB-Interface-/251426475926?pt=US_Computer_Recording_Interfaces&hash=item3a8a2f8f96)

You'd possibly find one cheaper. I just grabbed that one with no research. ;)

WOW Service handed on a Sliver Platter You RocK..
Found one with all the CDs(5) 1 Day left to bid 
But Im not sure I can remember how to turn on windows....to install the CDs:redface:(Humour Here)

---

### Post by Bucky Ball on 2014-01-21
> **runrickus said:**
> 
But Im not sure I can remember how to turn on windows....to install the CDs:redface:(Humour Here)

Ha! I was just going to say, what do you need the CDs for? lol. ;)

I've just this minute switched off the desktop. Recently reinstalled with 12.04 minimal running xfce4 desktop environment, QJackctl, Ardour, Audacity, Firefox and that's it! I have an old Hoontech audio interface connected to that and was up and experimenting with Ardour and a guitar in no time. And that is on a P4 with 1Gb of RAM. Inspired to stick an SSD and 4Gb of RAM in there now. :-k

---

