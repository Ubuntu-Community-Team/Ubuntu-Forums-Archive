---
title: "If fans have magnets in them, how dont they break your HDD?"
date: 2007-08-02
forum: The Cafe
---

### Post by jgrabham on 2007-08-02
Have just thought of this.  I know how an an electric motor works, but shouldn't it corupt you hard drive?

---

### Post by ErusGuleilmus on 2007-08-02
I would imagine that the feilds given of by the fans are so weak it doesnt effect your hdd.

---

### Post by Motoxrdude on 2007-08-02
Fans have pretty small magnetic fields. It takes large magnets to screw with your hdd. I'm not talking refrigerator magnets, more like earth magnets.

---

### Post by burt_57 on 2007-08-02
> **Motoxrdude said:**
> Fans have pretty small magnetic fields. It takes large magnets to screw with your hdd. I'm not talking refrigerator magnets, more like earth magnets.
Lmao......  anyway the right answer can be so easy to fine..
Do a google search .
Never put a magnet in frot or a CRT ... well if you do look at the nice picture or distortion it does .:popcorn:

---

### Post by ~LoKe on 2007-08-02
There are magnets in your hard drive.  It takes some serious power to damage an HD.

A floppy disk, on the other hand..

---

### Post by burt_57 on 2007-08-02
I read once that the NSA standard for erasing old hard drives called for fairly stern hardware measures.

One of the steps involved sand-blasting the magnetic medium off of the surface.

Issac Newton, not Einstein. Newton's First Law of Thermodynamics (AKA the law of conservation of energy) states that energy can neither be created nor destroyed, but only converted from one form to another



I read somewhere that a person had standardized on a certain powered rifle to shoot the hard disk and ensure that data is not retrieved later on.

I think that would be a cheap, quick and certain process to ensure data privacy.



Way back we used to melt the hard drive aluminum platters into a brick - it made for a very nice, if bulky, paperweight.

There are several issues with permanently deleting files off of a hard drive:

As you pointed out the file system delete function merely "un-links" the directory entry from the file contents which continue to exist on the drive as "unused" sectors until a new file is written over them. That's why investigators can find so-called deleted files quite easily.

Un-erase programs (such as PGP-Wipe) overwrite the sectors with alternating patterns of 1's and 0's to "premanently" erase the remains. This is generally acceptable if you want to protect the file contents from easily obtainable discovery with standard forensic tools (you left out Guidance Software's EnCase - the premier forensic tool - not free).

However, the underlying magnetic particles are not all entirely re-aligned even with a good un-erase product. Think of the magnetic media as having millions of compass needles for each bit - for a digital 1, for example, they are all lined up with the North Pole of the magnet pointing up and for a digital 0 with the North Pole pointing down. When you overwrite the bits not all of the needles follow - enough change so the sector can be successfully read but enough remain in the former position that with very sensitive instruments one can obtain the old file data. There is even some traces of the old data in the aluminum substrate itself. Hence the need to melt the media into a block. Or strongly encrypt in the first place.


**Scientists have discovered one of the major causes of hard disk failure.**

According to researchers working at the University of California and Hitachi Global Storage Technologies, understanding certain types of disk drive failures, called magnetic avalanches, could help disk drive manufacturers produce more reliable storage.

Magnetic avalanches occur when a magnetic head hovers over a patch of disk drive causing the polarity of that part of the drive to change its alignment or spin. The patch's polarity in many magnetic materials changes in a haphazard series of large and small jumps that physicists liken to an avalanche - though the scientist's research showed it often behaves more like an explosion or runaway fire. These avalanches can cause sections of hard drive to lose data.

Research was carried by Joshua Deutsch, professor of physics at the University of California, Santa Cruz, and Andreas Berger, who did the research while at Hitachi Global Storage Technologies.

Deutsch said that the research paper, published in 13 July edition of Physical Review Letters, that the findings advanced knowledge of magnetic spin in drives.

"The big advance in this paper is that in previous models of avalanches, the spin just flips from up to down as soon as they apply a magnetic field, and they're done. But that's not the way spin behaves in the real world," Deutsch said.

The scientists said that previous models overlooked an effect called "spin precession", which each magnetic field exerts on its neighbours. The scientists likened each individual bit of information on a platter to a "tiny pincushion bristling with individual magnetic fields."

As the head of the drive nears, each pin wobbles in a widening circle - pointing neither up or down but somewhere in between - before it settles on its new polarity. They called that wobbling "precession" and said it resembled the way a spinning top draws out circles as it rotates.

"It takes around a few nanoseconds for a precession to die down," said Deutsch. "That's not that fast compared to computers today. It's not as fast as the timescale you get for a transistor to switch." During that brief time, each magnetic field contributes forces that affect the precession of neighbouring fields. Each of these spins

Combining all those wobbles adds up to a lot of energy that changes the polarity of neighbouring bits and spreads across the surface, causing sections of disk drive to be wiped out.

The researchers suggested that the reason these avalanches die out is that the magnetic material can dampen the wobbles. They said that materials that good damping abilities would make candidates for use in hard drives.

"Obviously, disk drive makers have already learned by an enormous amount of ingenuity and trial and error what materials make good disks," Deutsch said. "But now we understand a lot better one of the reasons why - because the materials are good at damping, and we can quantify how damping will stop runaway avalanches. We still can't calculate their damping, but at least we can measure it."

---

### Post by Turboaaa2001 on 2007-08-02
When I worked as a PC Tech at Circuit City we had to use those magnetic keys for high value items to destroy the drive.

Even then we had to place it on the drive, and run a search for about 30 minutes. 

The other thing is that the electricity moving around inside creates more of a field than anything else. Plus the screws that hold the hard drive in place can become more magnetic than the ones in the fans.

---

### Post by Motoxrdude on 2007-08-02
> **burt_57 said:**
> Lmao......  anyway the right answer can be so easy to fine..
Do a google search .
Never put a magnet in frot or a CRT ... well if you do look at the nice picture or distortion it does .:popcorn:

Yes, a crt monitor is much more sensative to magnets then a hdd. Do a google search next time ;)

---

### Post by the_darkside_986 on 2007-08-03
I was reading the post about methods of destroying data, and I am wondering, is it true that the ext3 file system "zeroes out" the data--permanently deleting it instead of just un-linking it? I've read that somewhere, and I'm just wondering. I am a Computer Science major and in assembly language class we learned about the fat16 file system and how it doesn't delete files completely.

---

### Post by cmat on 2007-08-03
The PC speaker itself can do quite a bit of damage to floppy drives. To be safe I install all drives away from them.

---

