---
title: "A Pseudotester's Rushed Review of Windows Vista Beta 2"
date: 2006-06-10
forum: The Cafe
---

### Post by linbetwin on 2006-06-10
**Download.** Huge! 3200 MB for the 32-bit version, 4100 MB for the 64-bit version. I know that it's the "Ultimate" edition, but come on, it's not like they bundled Encarta with it! They do have some "example content" though: scenes from Apollo 13 and some underwater images from the Carribean.

**Installation.** First two attempts ended with BSOD's. I'm not kidding, I saw the dreaded thing right at the start of the installation process! Third try: no BSOD, but "CD/DVD drive device driver missing". Who ever heard of that? And it didn't give me an option to skip it or abort installation. The only solution was a hard reboot. After a few more attempts that ended with the same driver showstopper, I decided to try and install from XP. Yes, you can install it from within XP, but only to a partition seen by XP, not to unpartitioned space on the HD.

So I started the installer in XP and reached the same driver roadblock. Only this time it informed me it was the Nero Virtual Drive. So I disabled it and Vista didn't complain anymore.

The installer is graphical from start to finish, but it gives you almost no options, you either take it, or leave it. It copied files from the DVD to the NTFS partition for almost an hour. The DVD was spinning so furiously, I thought it was going to take off! Then the installer "expanded" the copied files. I guess "decompress" is too arcane a term for such an installer for dummies. Maybe they should have said "making the files really big". The expanding took another 30 minutes or so. At 27%, it rebooted my PC and continued.

3) Booting. I have an ATHLON64 3000+ (939, Venice), 1 GB of RAM, and an NVIDIA 6600 GT (128 VRAM). The Vista rating tool says my PC scores 3 (out of 10, I presume). I admit it's not a dream machine, but XP, Dapper, SUSE 10.1 and other distros fly on it. Not Vista! It takes more than 3 minutes to boot to the desktop. Before installing what drivers I could find (from NVIDIA, Windows Updates, the driver directory in XP) I had problems rebooting or shuting down.

On a funny note, the Vista bootloader listed Vista as "Microsoft Windows" and XP as "Earlier version of Windows". Come on, Softies! Evern Linux recognises an XP when it sees one! For a moment there I thought Vista replaced XP with 3.11. Or worse, ME!

**Look & Feel.** Aero Glass looks nice and works smoothly, but this baby was born to be screenshot, not used on a daily basis. It's like working in an office where everything (including furniture) is made of glass. So much for "Bringing clarity to you life", or whatever their slogan is.

If you had trouble switching from the Win98 interface to the 2000/XP one, Vista will leave you scratching your head (or banging it against the wall). IE 7 is unrecognisable, Office 2007 is a wholly different beast, the Media Center is a worthless piece of bloat. It's the kind of software that keeps getting more complicated and more "blingy" in order to justify its existence.

I haven't tried the desktop search. I'm not that old yet. The sidebar is as beautiful as it is useless. Just another piece of blingware.

**Performance.** My CPU and graphics card seem to be reasonably capable of handling the job, but the RAM... oh, the RAM! **Vista, thy name is Glutton!** It swallows ~700 MB of RAM, with no programs running other than the PC-cillin Internet Security for Vista. Before installing the AV, it was arount 500 MB, so Trend Micro is one of the main culprits here. The Task Manager displays more than 16,000 handles right after booting. If I open IE and WMP, memory usage soars to a hallucinating ~940 MB! And turning off Aero doesn't seem to help one byte! I read somewhere that this is because beta builds are compiled in debug mode, whatever that is. I wonder if this is really the problem.

I think there's also something wrong with the HD usage. I tried to defragment my partitions, the Defragmenter said i don't need to, but I insisted. (By the way, I know that Windows treats its users as if they were completely computer-illiterate, but not showing them the fragmentation analysis details, the drive performance map and the defragmentation progress is really offending. It only says that "defragmentation could take minutes or hours".) So I defragmented, but when I rebooted into XP, Diskeeper revealed that the Vista partition had 28% fragmentation!

**Conclusion.** I'll bet you dollars to downloads that Vista won't be released in January. There is still a lot of bug-fixing, tuning and twaking to be done. What Vista needs right now is... [developers, developers, developers, developers!]("http://video.google.com/videoplay?docid=8913084255008000794&q=ballmer+developers")

It looks nice and shiny from a distance, but it's all for your friends' and relatives' drooling pleasure, not for daily work. At least not without some serious getting used to.

---

### Post by Seaman on 2006-06-10
Bah, why can't they make an operating system based on *BSD? Sure, there wouldn't be any backward combatibility, but there would be less bugs and more security.

---

### Post by vseehua on 2006-06-10
hmm..hv been testing for one day...

it's eye candies are nice, no doubt about that... but the preformance is horrible...imagine taking more than 5 mins to start an application after i click on it... i guess i'll stick to ubuntu dapper and xp...

but seriously... with dapper getting even faster the older version, using vista is a step back frm xp...

---

### Post by Eggplant on 2006-06-10
I think the main reason why Windows Vista Beta 2 might be slow is because it might be compiled in Debug-Mode - and thus runs slower than it would be without debug flags. This would perfectly make sense for a beta that is aimed at providing feedback on bugs. The same does apply to Linux, too - that's the reason why debug-flags are not on by default if you go and compile a program yourself ;)

But I do not know if this really does apply to Windows Vista, as I have neither tried it myself, nor saw any justification of my debug-claim (of course, I didn't research into this).

---

### Post by Alienist on 2006-06-10
After successfully managing to triple boot Dapper/XP/Vista (which was kind of a headache, but i got it working) I've had some time to play around with Vista and so far my reaction is "meh." It's not that it is *bad* per se, it just isn't very exciting. A year ago I was pretty enthusiastic about Longhorn, but the actual product is anticlimatic to say the least. 

First of all, it is an *absolute* resource hog. 1 gig of RAM is the bare minimum to run this thing. The desktop compositing effects are kind of cool and min/maxing windows is snappy. Live folder previews are also cool. But somehow the whole user experience comes off as ponderous and cumbersome. It's difficult to explain; maybe it's that a lot of things about the UI just aren't that intuitive. The unfortunate bottom line for Microsoft, I guess, is that one way or another you can get 90% of Vista's features in XP, so why upgrade? 

I'm writing this from Vista but I really can't wait to boot back into Dapper.

---

