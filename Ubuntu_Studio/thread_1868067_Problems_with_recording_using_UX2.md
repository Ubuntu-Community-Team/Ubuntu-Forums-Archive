---
title: "Problems with recording using UX2"
date: 2011-10-23
forum: Ubuntu Studio
---

### Post by aza484 on 2011-10-23
Hi All,

I'm new round these parts and would really appreciate your expert opinions/guidance.

I've managed to get an old laptop into working condition again and installed ubuntu studio 11.10. My problem is that I have a Line6 UX2 USB interface and while I can record using the guitar and/or instrument inputs, neither of the mic xlr in's or the stereo line in's at the back work at all. 

Has anyone managed to get these working?

Thanks a lot!

---

### Post by jejeman on 2011-10-23
Give us output from folowing commands
```
lsusb
```
```
aplay -l
```

---

### Post by aza484 on 2011-10-24
> **jejeman said:**
> Give us output from folowing commands
```
lsusb
``````
aplay -l
```

Thanks for your help!

1)
```
arran@Jay:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c051 Logitech, Inc. G3 (MX518) Optical Mouse
Bus 005 Device 002: ID 413c:8103 Dell Computer Corp. Wireless 350 Bluetooth
Bus 005 Device 003: ID 0e41:4151 Line6, Inc. 

```2)
```

arran@Jay:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: PODStudioUX2 [POD Studio UX2], device 0: POD Studio UX2 [POD Studio UX2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

---

### Post by sgx on 2011-10-24
> **aza484 said:**
> Hi All,

I'm new round these parts and would really appreciate your expert opinions/guidance.

I've managed to get an old laptop into working condition again and installed ubuntu studio 11.10. My problem is that I have a Line6 UX2 USB interface and while I can record using the guitar and/or instrument inputs, neither of the mic xlr in's or the stereo line in's at the back work at all. 

Has anyone managed to get these working?

Thanks a lot!
Look for a new or used Fender Mustang1 usb amp. ($40 to $99)
Works plug-and-play in linux,
a linux editor called 'Plug' exists for the 12 built in classic Fender amp models, and you have 24 presets to save your creations in, and flip thru with a knob, while sending them to rakarrack, guitarix, calf/lv2 plugins yada yada. (it comes with a nice mac/pc software editor)
It also includes IK Amplitube Fender LE, (Twin Reverb, SuperSonic, and Metalhead 500 amps) which runs nicely in wine,
and also integrates nicely with the free version of Amplitube 3.7.
Which also works in wine.
Cheers

---

### Post by aza484 on 2011-10-24
> **sgx said:**
> Look for a new or used Fender Mustang1 usb amp. ($40 to $99)
Works plug-and-play in linux,
a linux editor called 'Plug' exists for the 12 built in classic Fender amp models, and you have 24 presets to save your creations in, and flip thru with a knob, while sending them to rakarrack, guitarix, calf/lv2 plugins yada yada. (it comes with a nice mac/pc software editor)
It also includes IK Amplitube Fender LE, (Twin Reverb, SuperSonic, and Metalhead 500 amps) which runs nicely in wine,
and also integrates nicely with the free version of Amplitube 3.7.
Which also works in wine.
Cheers

Thanks for your thought but I went for Linux because 1) it makes best use of my old system's resources and 2) its largely freeware based. If I need to pay money I could just buy a new copy of windows 7 for similar money and my UX2 would work fine.

Also, having already invested in the UX2 I'd rather avoid buying something else for the same purpose.

Finally, my issue is not that it doesnt record guitar (which it does), but that the mic inputs and stereo line inputs don't work.

Thanks anyway though.

Can anyone help me get the UX2 working fully?

---

### Post by jejeman on 2011-10-24
Give us output from 
```
arecord -l
```
So you have
2 front inputs, and 3 back inputs. Does this device suport 5 simultanius inputs? How is this managed on the device?
How many inputs do you expect/suppose to have on software side?

---

### Post by aza484 on 2011-10-25
> **jejeman said:**
> Give us output from 
```
arecord -l
```
So you have
2 front inputs, and 3 back inputs. Does this device suport 5 simultanius inputs? How is this managed on the device?
How many inputs do you expect/suppose to have on software side?
 
Will do when I get home this evening.
 
The interface has 2 XLR mic in's (with pre-amps) a mono guitar in and a mono pad in on the front, then a stereo line in and a stereo monitor in on the back. These can all be used simultaneously (I successfully did this on windows). It also has 2 analogue meters on the front to show recording levels, which don't work for me on linux yet.
 
Full spec here:
[http://line6.com/podstudioux2/specifications.html](http://line6.com/podstudioux2/specifications.html)
 
Thanks! :)

---

### Post by sgx on 2011-10-25
It looks like some internal routing is performed using Podfarm software, to send mic signals over usb, and this means experimenting in wine. Either running the podfarm installer, or copying files from a windows install to the same paths inside a .wine folder. The device itself should allow button routing the mics to the analog outs, which then can cable to your soundcard line-in.

Someone using Tango Studio has a youtube of Pocket Pod using
system software, perhaps it is Gearbox?

[http://www.youtube.com/watch?v=NVL1XMfCnmw](http://www.youtube.com/watch?v=NVL1XMfCnmw)

and Puppy Studio may have the line6 firmware pre-configured.

[http://www.murga-linux.com/puppy/viewtopic.php?t=72402](http://www.murga-linux.com/puppy/viewtopic.php?t=72402)

The line6 firmware may still be out there somewhere, to compile in a
ubuntu setup if needed.

Cheers

---

### Post by aza484 on 2011-10-25
> **sgx said:**
> It looks like some internal routing is performed using Podfarm software, to send mic signals over usb, and this means experimenting in wine. Either running the podfarm installer, or copying files from a windows install to the same paths inside a .wine folder. The device itself should allow button routing the mics to the analog outs, which then can cable to your soundcard line-in.
 
Someone using Tango Studio has a youtube of Pocket Pod using
system software, perhaps it is Gearbox?
 
[http://www.youtube.com/watch?v=NVL1XMfCnmw](http://www.youtube.com/watch?v=NVL1XMfCnmw)
 
and Puppy Studio may have the line6 firmware pre-configured.
 
[http://www.murga-linux.com/puppy/viewtopic.php?t=72402](http://www.murga-linux.com/puppy/viewtopic.php?t=72402)
 
The line6 firmware may still be out there somewhere, to compile in a
ubuntu setup if needed.
 
Cheers
 
Thanks very much for your input. So as a total linux noob (but not a tech one - just so you know what competence level to pitch to :P ) what should my next steps be? How would I go about using wine in tandem with JACK and Ardour? Regarding the line out to my soundcard, my soundcard is rubbish which is why I bought the UX2 interface so that's not really an option... 
 
Thanks again for your help.

---

### Post by aza484 on 2011-10-25
> **jejeman said:**
> Give us output from 
```
arecord -l
```So you have
2 front inputs, and 3 back inputs. Does this device suport 5 simultanius inputs? How is this managed on the device?
How many inputs do you expect/suppose to have on software side?

right, as promised,

```

arran@Jay:~$ arecord -l
**** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: PODStudioUX2 [POD Studio UX2], device 0: POD Studio UX2 [POD Studio UX2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

---

### Post by sgx on 2011-10-25
> **aza484 said:**
> Thanks very much for your input. So as a total linux noob (but not a tech one - just so you know what competence level to pitch to :P ) what should my next steps be? How would I go about using wine in tandem with JACK and Ardour? Regarding the line out to my soundcard, my soundcard is rubbish which is why I bought the UX2 interface so that's not really an option... 
 
Thanks again for your help.
Hi. Wine builds a mini windows setup for you, in

/home/username/.wine

and has an asio driver
called wineasio, which works great with Reaper. Install wineasio by
synaptic package manager, or download a .deb wineasio package, and install manually with

sudo dpkg -i name-of-wineasio.deb

Then issue the command   regsvr32 wineasio.dll

the winecfg command opens a panel to configure wine, choose
alsa in the audio tab, not jackd.

Linux support of windows vsts in ardour/qtractor/fst/dssi-vst
is spotty, the good news is you can use Reaper to host vst plugins, and many standalone apps will run, choose wineasio from their various preferences setups. The wineasio connection shows up in the
audio tab of qjackctl, usually auto-connected, and the midi items in will be in the alsa tab, usually needing manual connection, so select
an item on both the left and right panes, and press the connect button, a line showing success is drawn. Patchage does the same
connections, with free-floating widgets, and bezier cables, like
those in energyXT2.5, (the windows version of eXT 2.5 also works very well for vsts in wine!)

Run the podfarm or gearbox installer, 

wine name-of-installer.exe

and hope it works. You can
also find where windows installs the podfarm apps and .dll, and copy manually, hoping a registration key does not have special registry weirdness. Guitar Rig, Amplitube, and a host of freeware ampsims work great, and both Reaper and standalone app output can be routed in qjackctl to linux fx like rakarrack or Calf-plugins, for further processing and recording. Timemachine is great for testing recording.

ilok, pace, macromedia, donglware, and a handfull of
synthmaker/synthedit vsts won't work, almost all the 
all others will. Gazillions of 'em.

The harsh reality may be that a sale/trade of the nice UX2, or
buying another soundcard may be
your best option. mAudio pci cards are rock solid in linux,
simple to set up, and easy to come by used, if needed. Linux is what it be, unsupported hardware is a gold duck, shiny, pricy, but can't fly. :(

Cheers
(.wine can be renamed, and new/different wine versions can be installed,
then copy good parts of the old .wine to the new one, like a
Steinberg/VstPlugins folder, which I backup to dvd for good luck and time savings)

---

