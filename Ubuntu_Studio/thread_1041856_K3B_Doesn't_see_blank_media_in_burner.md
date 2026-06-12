---
title: "K3B Doesn't see blank media in burner"
date: 2009-01-17
forum: Ubuntu Studio
---

### Post by madsteer on 2009-01-17
I recently upgraded from Gutsy to Hardy.  Today I tried to burn a data DVD for the first time in Hardy, and the "Burn Medium" just says "Please insert an empty or appendable DVD+-R(W) medium..."

It's been a while since I needed to burn a DVD, but it worked fine the last time I did (in Gutsy).

In case it matters, I'm trying to burn on a box behind my TV running MythTV, so I'm ssh-ing into the box from another box and running k3b from the command window via ssh tunneled X11.  This, again, is how I've always done it.

the device file is "brw-rw----+ 1 root cdrom 11, 1 .... /dev/scd1" and I'm in the "cdrom" group.  Is there another permisisons problem I need to check?

Thanks,

---

### Post by dannysauer on 2009-01-18
My Ubuntu machine with a burner is upstairs and shutd down but as I recall there's a /dev/dvdrw symlink dynamically created on my machine when it recognizes a dvd burner, and there's a menu in K3B which shows the media types that the burner supports (I think it's called "devices" under the preferences dialog?).  Does your K3B know that your burner's capable of burning DVDs?  I seems to recall having issues like that a few years ago with a new DVD burner, and resolving the issue by installing a newer version which knew about the burner...

If nothing else, checking that info out may get you pointed in the right direction... :)

---

### Post by madsteer on 2009-01-19
Thanks for the help!

I do have a /dev/dvdrw1 (no /dev/dvdrw0 but /dev/dvd is not a burner drive).  It's a symlink to the correct device.

Also, I see the device in the K3B settings.  Everything is set to "yes" except +/-R Double layer.  That's correct as it's not a dual layer burner.

I'm starting to think my media is going bad.  I've heard that unused R/W media has a shelf life.  Not sure if that's true, but I bought a 100 pack several years ago.  I've got ~ 15 left.  I say this because I had K3B create an image, which I copied to a MacBook Pro running Leopard.  It ate one of my blank discs and I had to perform a special procedure to get it to spit it out.  Then again, it worked OK with two others, so who knows.  One of the discs that worked in my MBP didn't work in my Myth box.

Thanks,

---

### Post by Ruazinn on 2010-11-22
Even though it's been quite a while since the previous posts, I had the same problem after a new install of Meerkat, so I'll post a fix.  

The first time I opened k3b, I burned a CD, no problem.  Then I started listening to the CD with rhythmbox without shutting down k3b.  I then loaded a blank CD-R into a second drive and tried to burn another CD with k3b while rhythmbox was still running.  K3b registered the blank CD-R in the tree view on the left, but the burn dialog demanded that I insert a blank CD.  

Inserting a CD wouldn't work.  Shutting down rhythmbox and inserting a CD in the other drive wouldn't work.  Restarting the computer with a blank CD in both drives wouldn't get k3b's burn dialog to register either CD.  I finally just clicked "Burn Image Only".  This created wav files, but no iso...

I opened nautilus, found the directory ~/.k3b/share/apps/k3b and deleted it.  Then when I restarted k3b, I could once again burn cds.  Evidently, once the file in that directory gets screwed, you must nuke it.

---

