---
title: "Can Ubuntu mount a hard drive pulled out of an iMac?"
date: 2008-04-20
forum: The Cafe
---

### Post by diablo75 on 2008-04-20
A friend of mine has a iMac that won't power on anymore.  He wants my help to salvage his data.  I wanted to check and see if there would be anything in the way of preventing me from mounting and reading the drive from Ubuntu?

---

### Post by NiklasV on 2008-04-20
Yes you should be able to mount an HFS+ filesystem.

---

### Post by popch on 2008-04-20
Taht's what I did yesterday. I took the HD out of an iBook, put it into a USB enclosure and plugged that into my notebook. It mounted the volume instantly and without any fuss at all.

---

### Post by ssam on 2008-04-20
you may have trouble though if the HFS+ partiton has not been cleanly unmounted, or is corrupt at all. also if the HFS+ partition has journalling enabled you will only be able to mount it read-only.

---

### Post by Tundro Walker on 2008-04-20
> **popch said:**
> Taht's what I did yesterday. I took the HD out of an iBook, put it into a USB enclosure and plugged that into my notebook. It mounted the volume instantly and without any fuss at all.

...and then yelled maniacally ...

> It's alive!  IT'S ALIVE!

---

### Post by popch on 2008-04-20
> **Tundro Walker said:**
> ...and then yelled maniacally ...

nearly so.

There's a little story behind it.

My wife's iBook worked all right but started to make some very strange noises after a while. I brought it to the apple shop, and they sent back a note that the motherboard and the hard disk had to be replaced, and whether I wanted the iBook repaired or discarded or whether I was going to fetch it. I mailed that I was going to fetch it, and after a few days I went there to do that. 

The guy in the repair shop brought a box containing the fully disassembled iBook and started to stow it into a carrier bag. He even pointed out the hard disk to me and said that this was the only component with moving parts and that it therefore had to be responsible for the noises.

Needless to say, both the hard disk and the motherboard work just fine.

---

