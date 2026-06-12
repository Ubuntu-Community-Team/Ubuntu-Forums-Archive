---
title: "Windows restore CD advice"
date: 2007-03-08
forum: The Cafe
---

### Post by joker on 2007-03-08
Ok, yes I realize this is the wrong forum... heck, the wrong website for this question, but please indulge me.

I am sick and tired of reinstalling windows for people, I have half converted a few but most still insist on (and sometimes actually need) windows.  Since I am a nice guy, I do it, but I am looking for a better way.

I want to start making restore CDs (like the ones they used to give out with new computers) for the systems I work on.  I figure that way the reinstall process could be cut down from 3 hours to maby 1/2 an hour, or better still, user friendly enough for them to do it themselves.  Just a nice clean system image with a good portion of the updates, drivers, and important software already installed.

Now, this is easy enough to do with a 'nix system, but how can I do it with a windows system?  Can be done with 'nix?  

Please help me.

---

### Post by dyous87 on 2007-03-08
or rather...create an ubuntu image on a dvd and make it with a vista theme installed. then tell them you just installed the new version of windows for them and that xp is being obsolete. haha :lolflag:  jkjk...actually i'm not 100% sure but i think there is a norton program called ghost that this can be done with?

---

### Post by blueturtl on 2007-03-08
I think what you are looking for is Norton Ghost.

---

### Post by joker on 2007-03-08
Ok, I should mention I am cheap too, while the Norton product does look like it would work, it is about $70, and I only get paid $0 per install, so recouping my investment would take longer than I am comfortable with.  

I know I can do most of the operations necessary with 'nix, the only stumbling point is reformatting the drive with NTFS.  Does mkntfs work well?  I know NTFS-3G is fairly stable, but is is stable enough for this useage?

As I see it I have three options:
1.  Reformat drive with windows CD, then restore files with a live CD of some sort.  While I wouldn't put this process in the hands of most of the people I have helped, it would still be easier for me.

2.  Use a stripped down 'nix live cd with NTFS-3G tools installed and do a little scripting for an easy boot time restore.

3.  Create a small partition on the HD with a stripped down OS (most likely 'nix) and the restore image, and do some scripting for easy boot time restore.  It would be easy enough to create a live CD which would handle setting that up with minimal effort on my part.  But again I would be reliant on the mkntfs tool.

I guess I was just wondering if something similar to one of the has already been done, or if I need to get off my lazy butt and do something productive.

---

