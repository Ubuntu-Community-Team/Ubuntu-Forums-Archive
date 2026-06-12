---
title: "Ubuntu Windows question/idea (idk. just a thought)"
date: 2009-03-22
forum: Ubuntu Brainstorm
---

### Post by houseonfire on 2009-03-22
I was thinking a while ago when installing virtual box. Why can't there be like an "on/off" switch type thing. Where you pop a windows disk into the computer, install windows files into a part of your hard drive (partition possibly). You flip the switch on when you want to use windows apps, such as games, apps, etc. Then when your finished you turn it off so you don't get viruses or whatever. 
I don't know. I just hate the idea of needing to go and install windows just so I can use my new video card on my games. 
Just an idea... Not sure about the possibility of this. Or the legality. Just a thought.

---

### Post by smartboyathome on 2009-03-23
Wouldn't wine basically be the same thing as this?

---

### Post by houseonfire on 2009-03-23
I don't know. Would it? Just wine doesn't work with many games. This  way would let games run on the original files created for the purpose of the games.

---

### Post by Chemical Imbalance on 2009-03-23
I guess when virtualization gets more advanced in the future you might be able to do this--but right now 3D acceleration isn't up to snuff with virtualization.

---

### Post by houseonfire on 2009-03-23
Ya. That would be nice. This isn't a full on suggestion/ fully thought out idea. Just a thought that should be discussed for possible implementation in the future.

---

### Post by cardinals_fan on 2009-03-23
You can't run Windows apps without something resembling Windows.  WINE tries to recreate the Windows API on Linux, while virtualization actually runs Windows on virtual hardware.  Either way, you need to have the infrastructure there.

---

### Post by soltanis on 2009-04-09
Cut Wine some slack. Remember that it has to emulate a code base that has become very messy and is not always well documented, not to mention a terrible and constantly changing design philosophy, and an operating system that ignores things like standards that everyone else conforms to.

---

### Post by Merk42 on 2009-04-09
> **soltanis said:**
> ...and an operating system that ignores things like standards that everyone else conforms to.

What operating system standards do everyone else conform to that Microsoft doesn't?  Moreover, what operating system standards are there at all?

I know their web standards in IE has always been behind the others, but that's not what you're talking about.

---

### Post by soltanis on 2009-04-09
I remember an old tale of the NT TCP/IP stack. Have you heard of the TCP "urgent flag"? It used to be set to indicate priority traffic, giving preference to those packets.

Of course, Microsoft decided to simply set the flag all the time, so that it would look like their machines were faster over networks. Now just about no one really pays attention to that bit anymore.

---

