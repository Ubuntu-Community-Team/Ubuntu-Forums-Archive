---
title: "M-Audio Delta 44 configuration"
date: 2009-01-11
forum: Ubuntu Studio
---

### Post by kmcgrath on 2009-01-11
Alright, I've never had to really dig into any audio configurations for linux.  I wanted to fool around with some audio editing stuff so I bought the M-Audio Delta 44 [http://www.m-audio.com/products/en_us/Delta44.html](http://www.m-audio.com/products/en_us/Delta44.html), audio card.  Basically all I want to do right now is be able to hook up 3 or 4 audio inputs and record them at the same time.  I installed the card and ubuntu picks it up:

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: M44 [M Audio Delta 44], device 0: ICE1712 multi [ICE1712 multi]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

I have Ardour running and I've started jackd with the following:
jackd -d alsa -d hw:1

Within the Jack Control I can map all the Captures to Ardour, only nothing is ever recorded in Ardour.  I can't seem to get any of the inputs to record anything.  I've tried messing around with Pluseaudio, disabling my on-board card in my systems bios, and loading up a handful of different .asoundrc files I've found trying to 'google' the problem.

So I guess my main question is... Does anyone have a Delta 44 working with Ubuntu?  And if so what is the configuration?  Or does anyone know what I should try next?

Thanks for any help,
Kevin

---

### Post by thorgal on 2009-01-11
you need the right hardware mixer app for your card, namely something called envy24control. It should be in the alsa-tools-gui package or alsa-tools package, one of them for sure. 

Install it and fire it up. Then you can set your input levels (ADC chans) and output levels (DAC chans).

---

### Post by cathalcummins on 2009-02-20
Right, another Delta 44 question. I got the sound working before but each time the PC reboots everything resets.

Running Ubuntu Studio over 8.10. AMD Athlon(tm) 64. 


```
cathal@terminal38:~$ alsamixer
No mixer elems found

cathal@terminal38:~$ asoundconf list
Names of available sound cards:
M44
cathal@terminal38:~$ cat /proc/asound/cards
 0 [M44            ]: ICE1712 - M Audio Delta 44
                      M Audio Delta 44 at 0xec00, irq 19
cathal@terminal38:~$ alsamixer -D hw:0
```

I may have badgered things up in the **alsa-base**(9th line and "**options snd-ice1712 model=delta44**") file

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
install sound-slot-0 /sbin/modprobe snd_ice1712

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe --quiet snd-ioctl32 ; : ; }
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm && { /sbin/modprobe --quiet snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer && { /sbin/modprobe --quiet snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq && { /sbin/modprobe --quiet snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi && { /sbin/modprobe --quiet snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }

# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
options snd-ice1712 model=delta44
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from beeing loaded as first soundcard
options snd-pcsp index=-2
```

or perhaps I screwed things up in the blacklisting (the last line) of the onboard card:

```

# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp
blacklist snd_hda_intel
```

Typing **envy24control** brings up the panel but alsamixer (as you can see above) does not, however when I type alsamixer -D hw:0 it does bring up the alsamixer with proper delta 44 modules on it.

Still no sound. Running **gnome-sound-properties** and testing the sounds brings up the usual;


```
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Failed to connect stream: Invalid argument
```

Jack seems fine with the card. I changed the index of M44 to zero so it'd be default.

Have I messed things up Ubuntu peeps?

I seem to remember messind with "ADC"'s and getting the sound to work before. Can't for the life of me, figure out what the hell I did.

---

### Post by Reeman on 2009-02-21
Try the envy24control or alsamixer -c 0 though off the top of my head I do not know the exact mixer functions for the delta 44 but you should set your mixer source input to hw to get line in functions working on the delta, same as the 24/96 audiophile. 

I have two ice1712 audiophiles working happy with the alc883. I can record the ganged M-audio cards in 4 channel from line in source. I have not tried all three together to get six channel at high bit rate yet... but in theory I should be able to do it as the 883 seems to work just fine and does not share any irqs with the cards in the pci slots.  

I see you have two different references to the azalia 888....mmm different from my reference to the 883. Which shows only one defined device for the intel hd audio with an lspci. My cat /proc/interrupts is fine with no spurious or shared other that the usb/ethernet combo that asus boards and most of the onboard combo stuff uses. I did shut down my single serial and reassign the irq to pci, but I left parrallel alone because I still use a parrallel hp laserjet. So the pci on my board has 3 extra irqs which is plenty (unless you use something like a pci hog sounddisaster card with firewire).  

When you do get to a mixer that is working exclusively on the M-audio you need to use the source input function to set hw. It is with radio buttons not a slider (with the envy24control) and up down arrows with alsa mixer. See [[COLOR="Blue"]this[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1074894") thread.

Hope this helps.

Reeman

---

