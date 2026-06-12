---
title: "Need assistance installing focusrite saffire pro 24 dsp to ubuntu studio 12.04"
date: 2012-10-15
forum: Ubuntu Studio
---

### Post by Fatihaci on 2012-10-15
Hi ppl! I tried everything i found but  FW(firewire) led is still off. Mixer is not  recognizing my  sound card also. 
I have a clean installation at the moment before i screw everything, any advice?!

---

### Post by jejeman on 2012-10-15
Plug it in and give us output
```
dmesg | grep fw
ls /dev/ | grep fw
lsmod | grep fire
```

---

### Post by Fatihaci on 2012-10-15
hi man! I'm new around  here  if you  asking terminal result here you go

fatih@Fatih:~$ dmesg | grep fw
fatih@Fatih:~$ ls /dev/ | grep fw
fw0
fw1
fatih@Fatih:~$ lsmod | grep fire
firewire_ohci          40168  0 
firewire_core          56593  1 firewire_ohci
crc_itu_t              12347  1 firewire_core
fatih@Fatih:~$

---

### Post by sgx on 2012-10-16
[http://www.ffado.org/?q=node/1204](http://www.ffado.org/?q=node/1204)

scroll down for success stories with your device.
Similar Focusright device configs are on the previous page:

[http://www.ffado.org/?q=devicesupport/list&page=1](http://www.ffado.org/?q=devicesupport/list&page=1)

In qjackctl setup page

Input Device >
Output Device >

click the  >  and look for the fw:  devices.
The Periods/Buffer setting in qjackctl should be 3

The motherboard or card-based firewire chipset, is very
important, what works with jackd1 may not on jackd2.
One setup may use the older firewire 1394 stack, another the
ffado stack, probably time for a sharpie and notebook :wink:
 
Cheers

---

### Post by Fatihaci on 2012-10-16
Hi sgx and  thx for your advice! But its even hard to understand these stuff. i just met with ubuntu 5-6 days ago. and with  studio 3-4 days  ago. but  i'd try hardly . and i found out that firmwire problem. i guess... cause when i start to mixer saying:
**This device has firmware 0x10008 while we only know about version 0x10004**.
like that. 
and ppl telling there they changed :
''
I edited the saffire_pro24.cpp to modify the condition so it accepts the 0x10008 firmware, and it seems to work!
 I changed « if (tmp[0] != 0x00010004 ) » to « if (tmp[0] != 0x00010008 ) ».''
But i don't know how can i do that.
Btw this post is an old post belongs to 2010.(Found where did you link to me.)

---

### Post by sgx on 2012-10-16
> **Fatihaci said:**
> Hi sgx and  i just met with ubuntu 5-6 days ago. and with  studio 3-4 days  ago. 
There are a lot of details, but one at a time,
they can be mastered. Sometimes I just wait a few days,
when overwhelmed, and choose a time with energy, to explore
something new that is over my head.

The flow of audio in computers, mimics the cables, cords
buttons and knobs of old stereos, in/out/on/off/volume/selector
except its done with software. Ther are many ubuntu youtube videos,
that may help remove some of the mysteries.
Cheers

---

### Post by Fatihaci on 2012-10-16
Hi again ppl! Still i don't have led on. I'm getting this warring when i try to run mixer:

FFADO Control DBUS service
Part of the FFADO project -- [www.ffado.org](www.ffado.org)
Version: 2.999.0-
(C) 2008, Pieter Palmers
This program comes with ABSOLUTELY NO WARRANTY.
-----------------------------------------------

 Discovering devices...
00221541079: Warning (ieee1394service.cpp)[ 375] initialize: Could not set SPLIT_TIMEOUT to min requested (1000000)
00221541101: Warning (ieee1394service.cpp)[ 379] initialize: Set SPLIT_TIMEOUT to min requested (1000000) did not succeed
00221812256: Warning (dice_eap.cpp)[1398] read: No routes found. Base 0x7, offset 0x4000
00221839123: Warning (dice_eap.cpp)[ 881] updateNameCache: What is this function about?
00221841118: Error (saffire_pro24.cpp)[ 114] discover: This is a Focusrite Saffire Pro24 but not the right firmware. Better stop here before something goes wrong.
00221841141: Error (saffire_pro24.cpp)[ 115] discover: This device has firmware 0x10008 while we only know about version 0x10004.
00221841157: Error (devicemanager.cpp)[ 632] discover: could not discover device
DBUS service running
press ctrl-c to stop it & exit

Any idea?

---

