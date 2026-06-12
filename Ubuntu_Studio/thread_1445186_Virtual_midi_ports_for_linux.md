---
title: "Virtual midi ports for linux?"
date: 2010-04-02
forum: Ubuntu Studio
---

### Post by rockdude on 2010-04-02
Hi!

I'm searching for good alternatives to Midi Yoke and Loopbe1 virtual midi ports. I can't get them to work on wine so I wonder if there's a native linux alternative to use instead. Anyone?

Cheers

---

### Post by AutoStatic on 2010-04-02
The **amidi -p virtual -d** command in a terminal creates a virtual MIDI port.

---

### Post by DerickX on 2010-04-02
sudo modprobe snd-virmidi

edit: BTW you should work the other way around. FIRST you try an Linux native possibility and then, if you need it, an Second option via Wine (imho)

---

### Post by rockdude on 2010-04-05
Thanks guys. Worked like a charm.

---

### Post by aphixnet on 2011-09-11
Yeah, it sounds like charm :-)

But what do I have to do if i wanted to map my joypad as a controller for, say, lmms?
Is this the way I have to go?

---

