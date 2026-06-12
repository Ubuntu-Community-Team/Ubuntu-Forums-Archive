---
title: "Battery Blues"
date: 2009-09-29
forum: System76 Support
---

### Post by Carl Hamlin on 2009-09-29
Heya, folks.

This evening, I noticed that the battery on my Starling netbook isn't charging unless I turn the machine off entirely. If the power is off, the battery will charge from AC, but otherwise, Gnome Power Manager is acting like it doesn't even see the battery.

I took the advice offered on another thread and removed the battery for about fifteen minutes, checked the contacts, and put it back in, but to no avail. After that, I marked the Gnome Power Manager for re-installation via Synaptic, but that didn't resolve the issue either.

Anybody know what's up?

---

### Post by thomasaaron on 2009-09-30
Try removing the battery *and* the ac adapter. Let everything cool down to room temp. Give it 30 minutes. Then plug it back in. If that doesn't fix it, contact me via email (support...at...system76...dot...com).

---

### Post by Carl Hamlin on 2009-09-30
> **thomasaaron said:**
> Try removing the battery *and* the ac adapter. Let everything cool down to room temp. Give it 30 minutes. Then plug it back in. If that doesn't fix it, contact me via email (support...at...system76...dot...com).

Will do. I'll keep you posted. Thanks for your help with this.

---

### Post by RoaringOasis on 2009-10-13
Any luck on this? 

I have the same exact problem. Gut feel is that it started happing around the last kernel update. The battery will charge when the system is powered off, but merely maintains charge when powered on w/ AC. 

Suspend has also gotten a little bit weird recently, randomly waking up in my backpack or simply refusing to sleep. And finally, my wireless card (RTL8187) goes USB address hopping every so often. All of this has occurred within the two most recent kernel updates.

I'm going to run back to .12 in grub later this afternoon and see if the problems resolve... if you've heard anything, let me know! :-)

TIA,
RO

---

### Post by Carl Hamlin on 2009-10-13
> **RoaringOasis said:**
> Any luck on this?

Yep. I live in Denver, so Tom had me drive out to their admin office and swpa my battery out for his. His battery works like a charm, so he's letting me borrow it while the warranty replacement is in shipping. 

> **RoaringOasis said:**
> I have the same exact problem. Gut feel is that it started happing around the last kernel update. The battery will charge when the system is powered off, but merely maintains charge when powered on w/ AC.

Hmm. In my case, it was almost certainly the hardware, as swapping it out with Tom's battery appears to have resolved the problem neatly.

> **RoaringOasis said:**
> Suspend has also gotten a little bit weird recently, randomly waking up in my backpack or simply refusing to sleep.

I had problems with suspend under Intrepid, with my Acer Extensa, but they went away when I upgraded to Jaunty. It's possible that they've broken suspend for certain models again with a recent kernel update - my wife uses my old Extensa now, and never updates anything, ever.

> **RoaringOasis said:**
> And finally, my wireless card (RTL8187) goes USB address hopping every so often. All of this has occurred within the two most recent kernel updates.

Huh. I'd try rolling back to an earlier version of the kernel and see if that goes away.

> **RoaringOasis said:**
> I'm going to run back to .12 in grub later this afternoon and see if the problems resolve... if you've heard anything, let me know! :-)

Consider yourself up to date on the battery issue - Tom's going to let me know when the new battery comes in, and I'll drive back down there and swap him back to him for the new one.

Good luck to you.

---

### Post by RoaringOasis on 2009-10-16
Thanks :-)

Rolling back the kernel doesn't seem to fix anything. Wireless issues have become less frequent seemingly of their own volition. My standby is still weird, but I'm not worried about it right now.

I'll email support to see what they can tell me about the battery.

-RO

---

