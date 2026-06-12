---
title: "MusE does not record Control Change events"
date: 2009-04-18
forum: Ubuntu Studio
---

### Post by teel on 2009-04-18
Hi,
Finally, I've almost successfully set up the MIDI environment with my Yamaha P-70 piano via Audiotrak MidiMate and started recording with MusE.

However, I've noticed MusE does not record sustain pedal on/off events (Control Change) and with this limitation it is barely usable.

I've checked with KMidiMon and the Control Change events are captured (event value 64 on=127, off=0). I've searched through MusE docs, found nothing. Has anyone had similar problems and solved them?

Regards,
teel

---

### Post by babarosa on 2009-04-18
Hello teel,

I assume you are using the version from the repository (that is v0.8). It is very old and has a lot of bugs.

Recently our group was very very active (the added feature list truly is immense!) and the actual version is v1.0rc1, sadly at the moment you only get it as CVS branch - that means you have to compile it by yourself.

Our group is very helpful, post your message at "http://sourceforge.net/mailarchive/forum.php?forum_name=lmuse-user", we all help you through the compilation process. It differs a bit from ubuntu 8.04/8.10 and 32/64 bit. I am on v8.04 and 32 bit.

Regards, Michael

---

### Post by teel on 2009-04-19
> **babarosa said:**
> I assume you are using the version from the repository (that is v0.8). It is very old and has a lot of bugs.

Michael, v0.8 was exactly the version I've been using at my Ubuntu 8.10. Compiled 1.0rc1 and it seems to be way more mature, many thanks for that! Change control now works fine.

Best regards,
Tomek

---

