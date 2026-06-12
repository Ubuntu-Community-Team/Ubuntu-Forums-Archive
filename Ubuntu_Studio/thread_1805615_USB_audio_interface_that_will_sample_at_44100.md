---
title: "USB audio interface that will sample at 44100?"
date: 2011-07-16
forum: Ubuntu Studio
---

### Post by keithpeter on 2011-07-16
Hello All

I've discovered that the internal sound card in this PC will only work at 48000Hz sampling rate with jack, see

[http://ubuntuforums.org/showthread.php?t=1805563](http://ubuntuforums.org/showthread.php?t=1805563)

Does anyone have a recommendation for a usb audio interface that they *know from use* will support hardware sampling at a rate of 44100Hz and a 16bit resolution?

Stereo in and stereo out is fine. Its for editing voice type material, not multitracking or anything sophisticated. Think radio rather than music studio. Not outrageously expensive!

Cheers

---

### Post by Pablo_F on 2011-07-16
The M-audio fast track pro suits your needs. Zoom H4 too. 

Take a look at [http://wiki.linuxmusicians.com/doku.php?id=hardware](http://wiki.linuxmusicians.com/doku.php?id=hardware)
(it is not complete but there is useful info there)

---

### Post by keithpeter on 2011-07-17
> **Pablo_F said:**
> The M-audio fast track pro suits your needs. Zoom H4 too. 

Take a look at [http://wiki.linuxmusicians.com/doku.php?id=hardware](http://wiki.linuxmusicians.com/doku.php?id=hardware)
(it is not complete but there is useful info there)

Thanks for the list, Pablo_F. I've worked out that many usb sound interfaces including the cheap and cheerful ones support 44100Hz sampling, and I've dug an old Griffin iMic that I used years ago with an iBook. 

It works fine and allows 44100 or 48000 sampling and responds to the setup dialog in Jack.

---

### Post by Jordii on 2011-07-22
Do bear in mind that the M-Audio fast-track pro is an USB 1.1 interface. Therefore, it is slower than 2.0 devices. (More latency, which could be a pain with recording.)
Edit: Oops, I see you've got one already. My bad.

---

### Post by keithpeter on 2011-07-22
> **Jordii said:**
> Do bear in mind that the M-Audio fast-track pro is an USB 1.1 interface. Therefore, it is slower than 2.0 devices. (More latency, which could be a pain with recording.)
Edit: Oops, I see you've got one already. My bad.

No worries Jordii

Also, I'm not multi-tracking as such. I'm doing speech and location recording using a sound recorder then editing in ardour. My guess is that latency won't be such an issue.

---

