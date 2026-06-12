---
title: "anyone owning a terratec dmx 6fire usb?... help..."
date: 2013-12-14
forum: Ubuntu Studio
---

### Post by jivatmadas on 2013-12-14
hello all.

this is my first post here. newcomer to ubuntu... plain newb in other words (maybe i should have post somewhere else...).
don't want to be a(nother) bore but... i have a problem with my dmx 6fire usb.

3rd day searching the forums in every language i know to solve the problem, but now i'm about to quit.
if i don't get this sound card to work, that's it i'm out, back to the microsoft hell...
really don't want though. really willing to make everything possible to stick with linux. so if any good soul could give me a hand, i would apreciate.

so here's the situation: fresh install of ubuntu studio 12.04, i installed the "fwinst.sh" and" sixfireusb-0.6.1" as posted here [http://sixfireusb.sourceforge.net/](http://sixfireusb.sourceforge.net/)
and now i don't know how all that helped me. i'm stuck with no sound, no card recognized by any mixer (though the system is seeing it and the install were correct imo), and a jack which won't start (don't know if it's related). the rest is waaaayy behond my little skills...

eh eh... hmm... what now? 8-[

thanks in advance.
jd

---

### Post by jejeman on 2013-12-14
I don't know where did you get "fwinst.sh" file. On the sourceforge page there is only tar file with the source code.
In INSTALL file in source code it says
> Since Kernel 2.6.39 (and alsa 1.0.24) the module is integrated.Ubuntu 12.04 has the newer kernel then that and ALSA 1.0.25. So, you should not need to compile the driver.
Plug in the card and give output from
```
lsusb
aplay -l
lsmod | grep -i snd
```Device, card and module (snd-usb-6fire.ko) should be listed.

However, if you want you can update the driver by compiling the source code from sourceforge page.

---

### Post by jivatmadas on 2013-12-14
hi.
thanks for the quick answer.

in fact, my version is 12.04.3

here's my alsa version:
Advanced Linux Sound Architecture Driver Version 1.0.24

kernel version:
Linux mathb 3.2.0-57-lowlatency #59-Ubuntu SMP PREEMPT Thu Nov 21 00:00:21 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux


lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 046d:c31d Logitech, Inc. 
Bus 001 Device 004: ID 0939:0b16 Lumberg, Inc. 
Bus 002 Device 003: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 002 Device 004: ID 0ccd:0080 TerraTec Electronic GmbH 
Bus 002 Device 005: ID 046d:c52b Logitech, Inc. Unifying Receiver

aplay -l
aplay: device_list:252: aucune carte son n'a été trouvée... (= no sound card was found)

lsmod | grep -i sndsnd_usb_6fire          29455  0 
snd_pcm                97275  1 snd_usb_6fire
snd_seq_midi           13324  0 
snd_rawmidi            30748  2 snd_usb_6fire,snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61929  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    78957  6 snd_usb_6fire,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15091  1 snd
snd_page_alloc         18529  1 snd_pcm

---

### Post by jivatmadas on 2013-12-14
dmesg gives me:

[    8.783291] 6fire: invalid fimware version in device: 03 01 17 00. please reconnect to power. if this failure still happens, check your firmware installation.
[    8.783297] snd-usb-6fire: probe of 2-1.6:1.0 failed with error -22
[    8.783310] usbcore: registered new interface driver snd-usb-6fire

---

### Post by jejeman on 2013-12-14
Device is recognized
 Bus 002 Device 004: ID 0ccd:0080 TerraTec Electronic GmbH 
Module is loaded
snd_usb_6fire 29455 0 
but it has no users.
Here 
snd_rawmidi 30748 2 snd_usb_6fire,snd_seq_midi
it looks like it has MIDI input.
Give 
```
amidi -l
```

Still, where did you get "fwinst.sh"?

I see that you gave the dmesg output.
In README file it says
> Remarks
--------
Concerning firmware uploading: I removed the check that made firmware uploading
possible only for a specific device version. I don't known if firmware loading
will be successful on all devices. Reports from other users indicate that it
should work. If the device behaves strangely after a firmware upload has been
performed (every time the device has been reconnected to power), please report
this issue with a short description.Repower the device. If problem persist, try the latest kernel module or contact the modul developer.

---

### Post by jivatmadas on 2013-12-14
i found it in the "install" file of the sixfireusb-6.0.1 package that reads as follows:

Prerequisites
--------------

- kernel headers for current kernel
- internet connection


Building the kernel module
---------------------------

Usually you should be able to simple type:
  $ make


Installing windows firmware
----------------------------

[B][COLOR=#b22222]You also need the firmware for the card. To install it, visit
  [http://sourceforge.net/projects/sixfireusb/files/tools](http://sourceforge.net/projects/sixfireusb/files/tools)

Download both files and follow the instructions in fwinst.txt[/COLOR][/B]


Using this module with kernel >= 2.6.39 and alsa >= 1.0.24
-----------------------------------------------------------
Since Kernel 2.6.39 (and alsa 1.0.24) the module is integrated. Changes (either from user requests or bug fixed) will first be available on the
sourceforge page. Until these changes are integrated into the kernel/alsa, it will last a while. To use the sourceforge module with the new kernel/alsa,
all modules that are installed from the kernel/alsa named "snd-usb-6fire.ko" need to be removed from the kernel module directory. To accomplish that, you can type:
  $ sudo make kremove

Afterwards a new make install is required.


Installing the kernel module
-----------------------------

To install the module in the kernel, type:
  $ sudo make install

The module will then be loaded automatically on startup or if the device is inserted.

---

### Post by jejeman on 2013-12-14
I understand. You just installed the firmware, the new one. Try the old one, because we don't know the kernel module version which is included in ALSA 1.0.24. New firmware works with >0.5.4 version of the kernel module.
So, either try old firmware or compile the new version of the kernel module.

---

### Post by jivatmadas on 2013-12-14
thanks, i'll try that tomorrow morning. i'll get back on that.

---

