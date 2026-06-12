---
title: "Nautilus uses too much memory..."
date: 2008-11-14
forum: The Cafe
---

### Post by Giant Speck on 2008-11-14
I've noticed that Nautilus has been using over 200.00 MB of memory whenever it runs, and I cannot figure out why.

Is there anyway to configure it to use less memory?  Or do I have to look for a lighter alternative.  If the latter is the answer, what is a good file browser that has a GUI similar to Nautilus?  (And don't tell me Konqueror, please.)

---

### Post by chris4585 on 2008-11-14
for a lighter alternative, there's thunar and pcmanfm

---

### Post by Wolki on 2008-11-14
> **Giant Speck said:**
> I've noticed that Nautilus has been using over 200.00 MB of memory whenever it runs, and I cannot figure out why.

Has happened to me once in a while after I was in a directory with a large number of images (thousands), and even then it should take quite some time. If it happens, just kill it and it should be back to regular memory usage.

Also make sure that you measure memory usage correctly. Don't look at "virtual memory" - that number is by far too large.

---

### Post by Polygon on 2008-11-14
mine does not use that much whenever i check it...maybe around 40 or 50?

---

### Post by Giant Speck on 2008-11-14
> **Wolki said:**
> Has happened to me once in a while after I was in a directory with a large number of images (thousands), and even then it should take quite some time. If it happens, just kill it and it should be back to regular memory usage.

Also make sure that you measure memory usage correctly. Don't look at "virtual memory" - that number is by far too large.

Well, I get that number from System Monitor:

---

### Post by speedwell68 on 2008-11-14
It seems to only be using 27mb for me, no matter what I do.

---

### Post by Wolki on 2008-11-14
> **Giant Speck said:**
> Well, I get that number from System Monitor:

OK, the memory column should be relatively accurate (it's quite difficult to determine the real memory use). If you kill nautilus, how much memory does it use? Monitor it for a while and see when the memory consumption starts to rise.

---

### Post by Grant A. on 2008-11-14
The filer with the lowest footprint I have seen is the rox-filer. It is in the *buntu repositories, I believe.

---

### Post by Giant Speck on 2008-11-14
> **Wolki said:**
> OK, the memory column should be relatively accurate (it's quite difficult to determine the real memory use). If you kill nautilus, how much memory does it use? Monitor it for a while and see when the memory consumption starts to rise.

The memory consumption starts to rise immediately and quite rapidly.  In under a minute after restarting, it went from 17 MB to 108 MB of memory usage.  After two minutes, it was up to 175 MB.  It finally settled back to above 200 MB again after three minutes.

---

### Post by Giant Speck on 2008-11-14
Okay... I *think* I might have fixed it.

I set it to never show thumbnails, never preview sounds, and never show text in icons.  Then I killed and restarted the process.  It's only taking up around 32 MB now with no sudden skyrocket in memory usage.

I'll keep monitoring it and if that is finally what fixed it, I'll mark the thread as solved.

---

### Post by dizee on 2008-11-14
> **Grant A. said:**
> The filer with the lowest footprint I have seen is the rox-filer. It is in the *buntu repositories, I believe.
rox is good but takes a bit of getting used to.

almost certainly the lightest gui file browser, though if you go cli there are even lighter ones.

pcmanfm might be worth a look for a more familiar-feeling but still light file browser.
> **Giant Speck said:**
> Okay... I *think* I might have fixed it.

I set it to never show thumbnails, never preview sounds, and never show text in icons.  Then I killed and restarted the process.  It's only taking up around 32 MB now with no sudden skyrocket in memory usage.

I'll keep monitoring it and if that is finally what fixed it, I'll mark the thread as solved.
strange, that suggests there's a memory leak in there somewhere. those features shouldn't be *that* memory hungry, should they?

but then i'm not a developer so i wouldn't be sure. nautilus is known for being a bit bloated (does all the desktop wallpaper stuff etc).

---

### Post by chris4585 on 2008-11-14
rox is one of my favorites

but I thought xfe was one of the lightest GUI file browsers? :)

---

### Post by Wolki on 2008-11-15
> **Giant Speck said:**
> I set it to never show thumbnails, never preview sounds, and never show text in icons.  Then I killed and restarted the process.  It's only taking up around 32 MB now with no sudden skyrocket in memory usage.

I'll keep monitoring it and if that is finally what fixed it, I'll mark the thread as solved.

Probably the thumbnails, if there are a lot of them visible they can take some ram. Still, it shouldn't be this much. Do you have very large amounts of thumbnailed things on your desktop?

You could also try cleaning your thumbnail cache (~/.thumbnails).

---

### Post by chucky chuckaluck on 2008-11-15
thunar is a good alternative and i think aysiu has a script to make it the default file manager for gnome on his psychocats (redundant title, if you ask me. they're all nuts by default) site. mc is fantastic, once you get used to it (just like swimming in maine).

does pcman still do that weird thing where it deletes the directory you're in?

---

### Post by ssam on 2008-11-15
do you have a large number of files on your desktop?

do you have a large desktop wallpaper?

---

### Post by mentallaxative on 2008-11-15
> **chucky chuckaluck said:**
> thunar is a good alternative and i think aysiu has a script to make it the default file manager for gnome on his psychocats (redundant title, if you ask me. they're all nuts by default) site. mc is fantastic, once you get used to it (just like swimming in maine).

does pcman still do that weird thing where it deletes the directory you're in?

I haven't had that problem with Pcmanfm before. It is a good file manager, because it looks similar to Thunar and Nautilus which newbies may find more comforting than, say, Rox-filer or Emelfm2. No proper trashcan in Pcmanfm though--delete means delete. It's fine for me but others might be less careful.

As for replacing Nautilus with Thunar... I'm sure it works, but it feels like you're scooping the heart out of Gnome and replacing it with Xfce, in which case I would run Xfce anyway.

---

### Post by chucky chuckaluck on 2008-11-15
> **mentallaxative said:**
> As for replacing Nautilus with Thunar... I'm sure it works, but it feels like you're scooping the heart out of Gnome and replacing it with Xfce, in which case I would run Xfce anyway.

oh, i don't know, there's still the joys of the gconf-editor and no right-click menu to worry about.

---

### Post by madhi19 on 2009-05-22
I think I figured the leak out. I had the same problem and used the same solution but I started turning feature off one by one to see who messing things up and it preview sound file. I was going to report the bug but it already well documented.

---

### Post by Tibuda on 2009-05-22
> **Giant Speck said:**
> Okay... I *think* I might have fixed it.

I set it to never show thumbnails, never preview sounds, and never show text in icons.  Then I killed and restarted the process.  It's only taking up around 32 MB now with no sudden skyrocket in memory usage.

I'll keep monitoring it and if that is finally what fixed it, I'll mark the thread as solved.

Thumbnails uses much memory for me too. It uses 40MB, but when I open a photo folder, it goes to 100MB or more. It's ok for me, but I have to kill nautilus after I'm done browsing that folder.

---

### Post by Giant Speck on 2009-05-22
Holy crap.

I forgot I even made this thread.

---

### Post by CJ Master on 2009-05-22
> **Giant Speck said:**
> Holy crap.

I forgot I even made this thread.

There's been a very large wave of nercomancing lately. I mean its fine if you have something constructive to say, but he just repeated the same thing said a few post before! ARG! >.<

[/rant]

---

### Post by ed bear on 2011-06-17
My recent experiences may lend some light on this problem... I've dug through all manner of threads on Nautilus Memory Leaks in the last six hours, and this is the only one active in the last few years that mentions a solution! ALAS - it fails to work for me.  I turned off sound preview, killed and restarted Nautilus, and the problem persists.

Let me give the relevant details: In particular, this problem only happened to me very recently, and I can now produce it with a single directory opening.  And my results may rule out some of the other ideas out there.

BEARBUN6 is a fully-updated 8.04 LTS system; I've been running Hardy since mid-2008 but did a fresh install March 7, 2011.  Always had photo preview turned on, never a problem.

I LIKE Nautilus, and run a variant of Crux theme, which uses Metacity.

My install was prompted by a move to a newer hardware platform, which I had been testing 10.04 LTS and 10.04.1 on:

- ASUS motherboard, Intel 2.2 MHz single-thread CPU
  (BEARBUN4 was an AMD Duron 850)
- NVIDEA Gforce 400 AGP video card, an add-in in April
- ViewSonic VG900b monitor
- 1 GB basic DDR RAM
- 1 CD rewriter, one DVD rewriter - both ATA
- 1 internal iOmega ZIP 250 drive
- 1 internal 3.5" floppy drive (couldn't live without it!)
- 1 internal 5.25" floppy drive
  (OK, I'm old, but I got to see all the great bands!)
- 4 motherboard-based USB 2.0 ports
- 4 USB 2.0 ports on a PCI card
- 40GB WD ATA hard drive

Now, some have speculated that the memory leak arises only on certain filesystems or devices, of that it's a hardware problem with certain devices.  BUT...

My hard drive is complex.  The root partition is

ext2: 7.6 GB/5.3 free

My main data and work partition (mounted off root, not media) is

ext3: 19.4 GB/1.3 free

My swap partition is 2GB

I also have four 2GB FAT partitions (also off root) and have used external NTFS, Mac OSX and FAT32 drives and memory dongles in these experiences.  AND I don't know what the gvfs-fuse-daemon is, but it acts like a drive identical to my root partition.

Somewhere in there, I discovered and activated sound preview, so reading your solution excited me.  Alas, turning it off and killing, then rebooting changed nothing.

The system worked perfectly until about May 23, when a friend brought over two USB external NTFS hard drives with large video files on them.  (We are starting to learn a bit of video editing, which I realize will not get very far with this ancient hardware.)

As I sorted and copied files to my machine, I sometimes started getting what we have come to recognize as the Nautilus Memory Leak: system getting uselessly slow but not really crashing, CPU usage pinning near 100% but eventually getting things done if we wait forever - even for menu drops or window selection!  And it happened on external USB hard drives (NTFS), internal ext2 and ext3 partitions, and USB dongles (FAT32).

Mouse tracking remained perfect and the modem never dropped a bit.  Single-core, single-thread CPU, remember?  AND my internal hard drive light flashed about once every 2 seconds rather than running continuously, odd in a memory thrashing situation...

Dropping a kill box icon on any file browser window instantly returned the system to normal function every time, though the kill sometimes took a long time.

In normal running, with Mozilla online so I can talk to you and four tabs open, System Monitor tells me Nautilus is sleeping and taking about 10-25 MB.  I have no idea what "nice" refers to, though many threads refer to it; Nautilus is 0 nice.  CPU usage and memory vary widely, but the system isn't anywhere near half of those resources save for brief bursts when programs load (or if hot-babe is running; she's a bit of a hog).

When the system goes into slo-mo, about half my gig of RAM is occupied, considerable swap (of my 2GB) is in use and CPU load is bouncing off the pin at 97-100% but never staying there.  I sometimes find TWO Nautilus processes running, one asleep and one taking 67% of CPU or so.

WEIRDNESS: Sometimes, System Monitor memory graph shows a steady climb from about 15% to about 80%, followed by a drop and then another climb, very linear - like a saw-tooth ramp wave!

MORE WEIRDNESS: this kept happening in large directories.  But it also happened in small ones!  The key was that they held large video files - some of which showed previews despite my having selected "preview only files under 3 MB" in preferences.

I have triggered the condition - by opening a directory on my ext3 drive - and still see no delay in using Mozilla to compose this message to you!  Only the Nautilus functions seem to suffer at this point, though system menus do - I think they are Nautilus-managed, right?  Remember matacity's in here too.

The directory contains fifteen .AVI files (which preview) and a couple of .MP4 files, which do not preview.  I THINK I've seen it go south even in list view, though I can't reproduce it now - but that makes sense since list view has little previews, too.

I've suspected that the thumbnail manager is having trouble, perhaps creating lots of thumbnails, but under 20 files are enough to cause the problem.  The proportion of free space on the drive does not seem to affect that.

That's my obsessing for today.  Have I helped this along?  Many threads indicate the problem persists in older AND the newest installs using Nautilus.
ED BEAR

---

### Post by Bandit on 2011-06-17
Smells of Necrosis in here...

---

### Post by Elfy on 2011-06-17
Closed.

---

