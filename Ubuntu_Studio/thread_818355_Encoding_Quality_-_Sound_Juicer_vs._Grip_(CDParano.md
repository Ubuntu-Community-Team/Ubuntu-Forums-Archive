---
title: "Encoding Quality - Sound Juicer vs. Grip (CDParanoia)"
date: 2008-06-04
forum: Ubuntu Studio
---

### Post by BassKozz on 2008-06-04
This question started from a thread I posted in the Community Cafe Here: [MultiThreaded CD Ripper?]("http://ubuntuforums.org/showthread.php?t=817801")

I started ripping my CD collection using [Sound Juicer]("http://live.gnome.org/SoundJuicer"), and I noticed that it wasn't multi-threaded, so I asked if there were any CD ripper/encoders that were, and I learned about Grip... Thinking I would get faster Rip/Encodes using [Grip]("http://nostatic.org/grip/") because of it's Multi-Threading capabilities (and my Quad Core Q6600 OC'ed to 3.3ghz) I gave Grip a try, only to find out that it is actually **MUCH** slower then Sound Juicer :confused:
I learned that the reason it is slower is due to the fact that it has a "[CDParanoia]("http://en.wikipedia.org/wiki/Cdparanoia")" feature that supposedly compensates for faulty disks and/or CD Drive Hardware, that should create a flawless rip (again, **Supposedly**). I am using Brand New CD's and a Brand New CD Drive, so I don't know if my CD's or Hardware could be faulty...

My Question is are there any applications available that can verify these claims? 
What I'd like to do is use an application to compare (side-by-side) the two encodes (one with Sound Juicer and one with Grip), and see a comparison of Rip/Encode Quality, to see if the Quality Justifies the SLOW speed of Grip... Are there any applications that can do this, or has there ever been any research done on this topic?

Thanks in advance for any/all feedback.
-BassKozz

---

### Post by BassKozz on 2008-06-06
:bump:

---

### Post by Stochastic on 2008-06-06
> **BassKozz said:**
> a "[CDParanoia]("http://en.wikipedia.org/wiki/Cdparanoia")" feature that supposedly compensates for faulty disks and/or CD Drive Hardware, that should create a flawless rip (again, **Supposedly**). I am using Brand New CD's and a Brand New CD Drive, so I don't know if my CD's or Hardware could be faulty...

Well, quite often the errors come from age or poor parts in the CDROM, or issues with the CD itself (most often a scratch, but could even exist on poorly mastered brand new CDs).  If you follow digital audio copying orange book standards (what the professional mastering studios go by) then these errors are VERY serious and are worth the time to check for (pros will then throw out any errored CDs and start over), but to the average person, most of these can be safely ignored.  Only when CDs are heavily scratched will the average person care about CD Paranoia (though this is generalization).

> My Question is are there any applications available that can verify these claims? 
What I'd like to do is use an application to compare (side-by-side) the two encodes (one with Sound Juicer and one with Grip), and see a comparison of Rip/Encode Quality, to see if the Quality Justifies the SLOW speed of Grip... Are there any applications that can do this, or has there ever been any research done on this topic?

Well, you could look at the songs in a wave editor that will show you every single sample (such as rezound or audacity), and manually check for irregularities.  You could also use the most important tool of all: your ears.  In the end, if you're ripping to any lossy compressed format (mp3 or ogg for example), then any errors kinda don't matter unless they're audible.

Here's the answer from CDParanoia's website > How can I tell if my drive would be OK with regular cdda2wav?
Easy. Run cdparanoia; if the progress meter never shows any characters but the little arrow going across the screen, the CDROM drive is probably one of the (currently) few drives that can read a pristine stream of data off an audio disc regardless of circumstances. This drive will work quite well with cdda2wav (or cdparanoia using the '-Z' option)

A drive that results in a bargraph of all hyphens would *likely* work OK with cdda2wav, but it's less certain.

Any other characters in the bargraph (colons, semicolons, pluses, Xs, etc..) indicate that a fixups had to be performed at that point during the read; that read would have failed or 'popped' using cdda2wav.

---

### Post by logos34 on 2008-06-06
You want it done fast or you want it done right?  If the latter, resign yourself to slow rips.  Good things take time.  Catch up on some reading.

Cdparanoia is actually the third best way to rip.  If you want highest quality/secure rip, use Exact Audio Copy or dBpoweramp cd grab (on Wine), which use AccurateRip feature (compares checksums against online database).  RubyRipper is the next best (native linux app too), which rips twice and compares "chunks" against an md5sum.

Then there's cdparanoia, which works amazingly well all things considered.  I use it with abcde a lot, unless the cd is visibly worn, in which case I use EAC (i.e. I did until it stopped working on me).  If I start getting error symbols during rip I run the tracks through a secure ripper.

Loads of useful info over at Hydrogenaudio forums

---

### Post by darsu on 2008-06-06
Grip doesn't rip or encode anything! It's only a frontend, and makes you choose which rip and encoding systems to use.

---

### Post by Stochastic on 2008-06-06
This really should be in the Multimedia & Video section of the forums.

---

