---
title: "If it's so dang hard to accurately read audio CD's...what about data CD's?"
date: 2009-10-07
forum: The Cafe
---

### Post by UnrealMiniMe on 2009-10-07
So, I'm sitting here ripping one of my brand new audio cd's in RubyRipper.  The first song has 73 chunks of 1000 bytes that did not match up after 2 reads, and after a whopping 71 reads (and counting), I STILL have 2 chunks that I can't get to match up 3 times.  Basically, after reading these two chunks 71 times, I haven't gotten the same answer on any 3 of the attempts, and possibly not even any 2.

Of course, people who rip a lot of audio CD's expect minor read errors like this, and that's why secure ripping software exists in the first place, like RubyRipper, EAC, dbPowerAmp, etc.

Still, a really sobering thought just occurred to me:
If it's SO HARD to guarantee an accurate CD read for audio, what does this imply about data CD's and DVD's where bit-for-bit integrity is not just "nice to have" but totally essential?  For instance, most Windows software is actually printed onto discs and sold on store shelves.  The same applies to all console games.  If I cannot accurately read a brand spanking new audio CD in 71 tries (it's up to 75 now with no improvement), how the heck do computers and consoles cope with trying to quickly read EXECUTABLES from similar discs in one try?  I mean, a single error in an executable can spell disaster, mayhem, and doom, right?

Am I missing something, or are the executables floating around on CD's/DVD's being constantly read in with random errors where they'll occasionally execute the wrong instruction, read to or write from the wrong register, etc.?  Obviously checksums can provide verification, but I doubt they're checked on every read...and if they don't match, they must be going ignored, considering how many read errors I'm getting on brand new audio CD's.

:eek:

---

### Post by PurposeOfReason on 2009-10-07
Ripping depends on your drive more than you think. I've never had that much of a problem getting  a 100% log rip.

---

### Post by UnrealMiniMe on 2009-10-07
While that's true, the odds of my drive being especially low on the normal distribution are...well, I suppose those odds are equally low on the normal distribution, by definition. ;)  It's possible of course, but it seems more likely that most people have computers and consoles with drives just as faulty as mine. :eek:

---

### Post by lswb on 2009-10-07
On a data CD there is a certain amount of error correction built in to the recorded data. I forget the exact amount, but I beleive it is something like 2350 bytes per block or sector, of which 2048 bytes is the actual data and the other bytes are used for error detection and correction.

---

### Post by UnrealMiniMe on 2009-10-07
> **lswb said:**
> On a data CD there is a certain amount of error correction built in to the recorded data. I forget the exact amount, but I beleive it is something like 2350 bytes per block or sector, of which 2048 bytes is the actual data and the other bytes are used for error detection and correction.

Thanks!  I was Googling, but I wasn't Googling for the right search term.  After throwing in the term "error correction," it turns out the answer is right in the Wikipedia article on CD-ROM's, and you're right:  There are 2048 bytes of data out of 2352 bytes total, and the error correction data uses the Reed-Solomon algorithm.  This makes a LOT more sense now.

---

