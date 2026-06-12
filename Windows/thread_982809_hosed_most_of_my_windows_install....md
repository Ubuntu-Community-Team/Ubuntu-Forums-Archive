---
title: "hosed most of my windows install..."
date: 2008-11-15
forum: Windows
---

### Post by mfarquhar on 2008-11-15
I've been dual booting Windows and Linux for a while now. after a short spell of being windows only I went back to dual boot last month, everything's been running fine, until tonight at 1 in the morning I had a bright idea that wasn't so bright.

I'm running an old system, so I use Windows ME, since its FAT32 it plays nice with Linux. Only hitch is I have to mount manually via command line. not a problem, only takes a sec and i felt a little better having to do it that way than having it auto mounted.

the only thing was, i mounted it under media/d (folder I made) and after having to open the filesystem and navigate there, while not really all that much work, i thought "hey I'll just make a shortcut on my desktop and skip a step" good in theory, didn't work in practice. i dragged the folder to the desktop and held the button that changed it from copy to move, it was an arrow so before I could think about it I assumed arrow = shortcut.

Fast forward and when i open the new file on my desktop, there's some weird stuff in there I've never seen before, and when i go back through the filesystem to the right spot things are missing. not yet realizing what i had done, i assumed something had gotten messed up during the mounting (hadn't checked it prior to my "shortcut" making) so i manually unmounted and remounted, didn't fix it.

rebooted the system to try to boot windows, grub tells me its an invalid disk, and retry a few times, with the same results. It hits me that maybe i messed up the boot sector or files for windows, so I grab the FreeDOS CD that a friend advised me to get, boot into that, look at the help files and see something that looks promising called bootfix, run the command, get some cryptic text back, and reboot. Windows is still listed as invalid through grub, so I'm back to Linux. Somewhere in here it hits me what I did wrong, so I'm thinking this is an easy fix.

i try to copy the files that got taken from windows back to where i think they belong, and then try to reboot back into windows, no such luck.

back in Linux i try to back up any personal files I can find onto my trusty Linux partition for safe keeping, but most of the contents of the My Documents folder except My Pictures, is missing, the only stuff i can really retrieve is what was sitting on my windows desktop. and of course, like everybody but the people who have been bitten enough, I didn't make backups, It was on my to do list, for the better part of a year...and I've lost all my data before messing around with resizing partitions and through drives giving up the ghost, so I'm really kicking myself right now for not listening to my own advice.

I'm not sure if this is fixable, getting ready to just reinstall windows again, maybe Linux too, tweak all the partitions to just the right sizes (my past experiences with repartitioners led me to just using a small 2nd drive for Linux, gonna change that next time around). and I'm gonna make a couple smaller backup partitions that I keep files I don't want to lose in.

Anyone who read the whole story, let this be a lesson, [COLOR="Red"]**[SIZE="3"]BACK UP YOUR DATA FREQUENTLY[/SIZE]**[/COLOR]

---

### Post by jaqie on 2008-11-15
Yep. and for those of you that use 2000/xp/vista check out the freeware for personal use DIXML utility for backing up. it uses windows' own shadowcopy service, which is honestly the best way to do it.  One little quit pro quo (spelling?): don't use DIXML in conjunction with truecrypt set to encrypt the entire hard drive - upon restore things aren't restored properly >(x.x)<

---

### Post by Izek on 2008-11-15
Or you can keep all your documents in like an 8 GB flash drive (or bigger) so you can install any OS you want to the physical hard drive at any time. No backup utility required if you do that.

Though, you'll lose all application data, etc. if you choose to go my way. Just not documents (Pictures, music, etc.) if you remember to keep them all there at all times. I sometimes don't, but only on rare occasions.

---

### Post by HermanAB on 2008-11-19
Hmm, I have come to the conclusion that click-drag-drop can be very dangerous when the wife's secretary accidentally moved about 10,000 files on a server.  Since Linux is very fast, this kind of schkrew-up happens at the full bandwidth of the disk.  

Some distros by default mount the Windows partitions as read-only in a dual boot system to prevent most finger trouble.

---

### Post by mfarquhar on 2008-11-19
> **HermanAB said:**
> Hmm, I have come to the conclusion that click-drag-drop can be very dangerous when the wife's secretary accidentally moved about 10,000 files on a server.  Since Linux is very fast, this kind of schkrew-up happens at the full bandwidth of the disk.  

Some distros by default mount the Windows partitions as read-only in a dual boot system to prevent most finger trouble.

I had been thinking of altering the command i was using to make it mount read only just in case, but I was lazy (the same reason there were no backups...)

---

