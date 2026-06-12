---
title: "Sync music to a device running Rockbox"
date: 2007-04-24
forum: The Cafe
---

### Post by Noah0504 on 2007-04-24
When I decided to run Linux, I decided to use all of the benefits open source has to offer.  My music collection is now entirely in Ogg Vorbis.  I made the mistake (well, that's what the folks over at the Linux Action Show! call it) of buying an iPod.  Don't get me wrong, it's a great device -- even more so now that I run Rockbox on it.

Anyway, I was wondering how any of the Rockbox users here sync music to their devices.  If nothing exists, I may have to brush up on my programming and create something myself.

---

### Post by ProteinPappa on 2008-01-08
*bump* 

Is there any such software? I can stand to manually copy the albums I want over, but it would be nice with a program that transfers over new podcasts automatically.

---

### Post by science4sail on 2008-01-08
try exaile and amarok, some people say that they're ipod compatible, but i haven't tested them myself...

---

### Post by SolusNunquam on 2008-01-08
I can sync my Ipod using Amarok or Rhythmbox, but i prefer Rhythmbox...

---

### Post by DPic on 2008-07-27
Ipod compatible means they'll work with normal ipods... It's ironic that although they can do that, they don't work with rockbox. I have the same trouble with rockbox. Does anybody know a solution or a workaround? 

I suppose that instead of treating rockbox like a portable music device, you could treat it as a portable storage device like a USB drive. Don't suppose you can sync your music library like that though, huh?

---

### Post by fluteflute on 2008-07-27
I use a program called 'Unison'. It's in the repos - I belive you want the 'unision-gtk' package.

Its rather slow at finding changes but it does the job well.

Edit: Its not automatic (as in you still have to run the program). If you know whats changed its far faster doing so yourself!

---

### Post by amar on 2008-07-27
I just set up an rsync script to run each time I connected the device. It involved a bit of fiddling but works for me. Unfortunatly I am on a placement at the moment so I can't get to the computer to show you the script for another month.

It might be worth suggesting that it could be a feature added to rbutil

Good luck though

---

### Post by DPic on 2008-07-31
I filed this bug [https://bugs.edge.launchpad.net/ubuntu/+bug/253785](https://bugs.edge.launchpad.net/ubuntu/+bug/253785)

---

### Post by vheisssu on 2008-09-14
Bump. I have the same problem. I'm fine with running a script to sync but do not have the linux background to do this myself. It would be nice to be able to redefine a device in Rhythmbox so that it treats it as a USB drive and lets you decide the file structure. This seems like it would be simple to do and would very easily solve this problem.

Does anyone have a script to sync?

---

### Post by jamesisin on 2009-12-07
I too am looking for a convenient way to auto-sync music to a Rockbox device (iPod 60GB 5th Gen).

It seems easy enough for Rb to treat the music as raw data and load copies of that onto the mounted device (which is what I do manually anyway).  Would be nice if there were a plugin to manage, say, playlist sync'ing (my entire collection won't likely fit on a portable player for a long time yet).

Did anyone ever come up with a nice sync script?  Utility?  Plugin?

---

### Post by caribo on 2010-10-04
Banshee 1.8 seems to do the trick for me, syncing music,audiobooks and podcasts...

---

### Post by jamesisin on 2010-10-04
> **caribo said:**
> Banshee 1.8 seems to do the trick for me, syncing music,audiobooks and podcasts...

And you are synquing to a RockBox device?

---

### Post by Austin25 on 2010-10-04
I wish I could put Rockbox on [this]("http://www.bhphotovideo.com/c/product/718685-REG/Sony_NWZE354BLK_8GB_E_Series_Walkman.html"). :(

---

### Post by sideaway on 2010-10-05
You can, you jsut have to figure it out yourself :)

I had a rockboxed Sansa Fuze and a Toshiba Gigabeat, but I sold the fuze once I got an android phone and the toshiba's USB terminal broke... would still be kind of usefull to have a fuze though, for the gym etc. Gotta get the toshiba fixed.

I even designed a theme for the gigabeat.

I used rsync for music syncing.

---

