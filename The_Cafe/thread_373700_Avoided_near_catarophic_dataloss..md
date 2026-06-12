---
title: "Avoided near catarophic dataloss."
date: 2007-03-01
forum: The Cafe
---

### Post by PrimoTurbo on 2007-03-01
I have no clue what went wrong but for some odd reason Ubuntu 6.10 install froze at 34% for about 1 hour, with no cue from my CD drive or hard drive that anything was working. Then when I tried moving the mouse around and access menus the whole LiveCD froze.

So I'm like, alright whatever. Pop in Windows XP CD enter Recovery Console and type FIXMBR to restore the windows MBR, everything looked fine. However upon reboot, I was getting operating system missing errors. So I figured I needed to delete the messed up partial linux partition and set the NTFS drive active, so I popped in my simplyMephis LiveCD because it has QtParted. However it doesn't want to work for some odd reason, I can't get passed the login screen it just freezes.

At this point I'm thinking that I'm running out of options and a format would mean I would loose my music collection, a ripped DVD of a rare movie I need for a class to write a paper on and the original DVD was already damaged by me recently, some new photos and university paper outline and assignments which I had recently started.

I had to download Ultimate Boot Disk from a different computer and burn it, then I entered the live linux CD on it and opened up QtParted and removed the broken linux partition made by Ubuntu install. However for some odd reason I could set the drive active, I rebooted and I was getting a lot of odd error messages. Again I entered the UB LiveCD and this time for whatever reason I was able to set the NTFS partition active.

Anyways I have no clue what happened, I was thinking drive/cd drive failure but I just checked everything and it all works fine no ERRORS or anything. Even made a backup in Windows on a DVD and checked it with no problems.

I noticed that Ubuntu install can freeze for no reason, even on working hardware. Despite the fact that the CD worked before with no problem and had a Md5Sum check on it before burning. Has anyone else ever avoided any problems with installing Ubuntu?

---

### Post by SunnyRabbiera on 2007-03-01
you could still have a bad burn
and you might also want to use dapper instead of edgy, as edgy is called edgy for a reason (I heard issues on cd installations of edgy)

---

### Post by Nikron on 2007-03-01
I've never avoided it...  I've just simply given up and formatted though.

---

