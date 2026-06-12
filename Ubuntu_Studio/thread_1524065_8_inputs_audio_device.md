---
title: "8 inputs audio device"
date: 2010-07-04
forum: Ubuntu Studio
---

### Post by decibel83 on 2010-07-04
Hi.

I'm looking for a 8 inputs audio 19" rack device (USB or firewire) which works on Linux.

Could you help me to find something supported?

Thank you very much!
Bye.

---

### Post by Pablo_F on 2010-07-04
If firewire, look at ffado support list ([http://www.ffado.org/?q=devicesupport/list](http://www.ffado.org/?q=devicesupport/list)) and choose from the ones with full support. Or ask there.

Based on what Paul Davies comments here ([http://ardour.org/realfaq](http://ardour.org/realfaq)) (worth reading anyway) I wouldn't think of a USB device if you want eight inputs. In any case, you can ask the alsa users list.

Cheers! Pablo

---

### Post by JC Cheloven on 2010-07-04
I recently bought this one. [http://ubuntuforums.org/showthread.php?t=1505953](http://ubuntuforums.org/showthread.php?t=1505953)
Very satisfied.

You'll be probably pointed to the presonus firepod, edirol fa66 (&fa101), echo audiofire 8, and some others. All of them good ones, I guess, but didn't try them out personally.

It's not usual, but some usb2.0 devices are reported to work with the alsa driver. I heard a report of the Edirol M-16DX working (ok for recording, although some issue for monitoring). EDIT: here the source: [http://traverso-daw.org/forum/index.php/topic,243.0.html](http://traverso-daw.org/forum/index.php/topic,243.0.html)

---

### Post by AutoStatic on 2010-07-05
decibel83, then you need a Firewire device. Most supported USB devices are USB1.1 devices, so they simply won't allow for more than two channels to be used at once. Like Paul Davis states in the Ardour FAQ there are practically no supported USB2 devices (USB2 could allow for more than two channels to be used simultanuously).
So I would focus on a Firewire device. I'd like to add Focusrite, they have some nice stuff also. I'm expecting a Saffire Pro 24 one of these days.

---

### Post by JC Cheloven on 2010-07-05
> **AutoStatic said:**
>  (...) there are practically no supported USB2 devices (USB2 could allow for more than two channels to be used simultanuously).True, but (admittedly to my surprise) some of them are reported to work. I was considering one of those because many laptops lack a fw port nowadays.

> So I would focus on a Firewire device. I'd like to add Focusrite, they have some nice stuff also. I'm expecting a Saffire Pro 24 one of these days. +1  people at focusrite cares about linux, which we should acknowledge. 
But the fact is that I've been watching the status of the saffires (24 & 40) in ffado for longer than a year, and it never changed from 'experimental'. So I ended up with the Phonic Helix board...
I look forward to see some report from you about the saffire 24 :rolleyes:

JC

---

### Post by bluesscream on 2010-07-05
there is the edirol ua101 as a usb2 device since 2005. But all I read about it's use in linux does not convince me. I'm pretty satisfied with it's fw version edirol fw101

---

### Post by trulan on 2010-07-06
As was said, you'll get pointed to the Presonus Firepod / FP10.  I have two of them and they are great IMHO.  Of course they are discontinued, so you'd have to go somewhere like ebay to get one (My first one was bought new, second one used off ebay).  Presonus has newer (better?) gear but I can't speak for how well it is supported.

---

