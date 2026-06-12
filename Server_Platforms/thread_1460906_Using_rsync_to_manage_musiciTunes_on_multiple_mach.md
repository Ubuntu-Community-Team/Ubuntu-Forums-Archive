---
title: "Using rsync to manage music/iTunes on multiple machines?"
date: 2010-04-23
forum: Server Platforms
---

### Post by flatline on 2010-04-23
I have a **lot** of music.  After ripping nearly 1,000 CDs, my collection is well over 80GB.  All of this lives on my Macbook Pro in iTunes.  I'd like to keep a separate copy of it on my home server, which can be shared to the other computers in the house (HTPC and gaming rig, both running Win7 x64 Ultimate), but be able to sync the two libraries up as needed, so I don't have to rip every new CD twice.  

I thought that rsync might work, although I'm not sure how I would trigger it - probably from the laptop, since it's not always 'on' the network?  I'm assuming that any new CD will be ripped to the MBP and need to be synced to the server, but of course it would be optimal if the system could sync in either direction.  Anyone running a similar setup have suggestions?

---

### Post by 1serveyou on 2010-04-23
> **flatline said:**
> I have a **lot** of music.  After ripping nearly 1,000 CDs, my collection is well over 80GB.  All of this lives on my Macbook Pro in iTunes.  I'd like to keep a separate copy of it on my home server, which can be shared to the other computers in the house (HTPC and gaming rig, both running Win7 x64 Ultimate), but be able to sync the two libraries up as needed, so I don't have to rip every new CD twice.  

I thought that rsync might work, although I'm not sure how I would trigger it - probably from the laptop, since it's not always 'on' the network?  I'm assuming that any new CD will be ripped to the MBP and need to be synced to the server, but of course it would be optimal if the system could sync in either direction.  Anyone running a similar setup have suggestions?


I'm in the same boat(about half the amount of music though), and would love to hear an answer to this. I have mac and pc computers too.

---

### Post by arrrghhh on 2010-04-23
I was trying to think of all these solutions, I can't come up with something that doesn't recopy the songs except rsync.

It sounds like you don't mind kicking the script off manually, or perhaps you could do it as a startup script on the Mac - but yea, just setup an rsync script to copy all your music folder over to the server.

---

### Post by tgalati4 on 2010-04-23
I'm pretty sure that the iTunes database is coded to the copy of iTunes that created it.  So simply copying it to another machine running iTunes would probably not work.  That is also why when you connect an iPod to a foreign machine, the iTunes on that machine doesn't recognize it.

I would install Rhythmbox on the Mac and enable music-sharing in the plug-ins.  This will start up a DAAP music share that you can see on iTunes with the other machines.

iTunes will also share tunes to other iTunes players, so you could try that as well.  But it is encrypted and non-iTunes players can't see the shares.

Your case illustrates the hazard of putting all of your music into an "encumbered" iTunes format.  You can't easily share it the way you want to.

I would take an iPod and install floola.  ([http://floola.com](http://floola.com)) Then you can drag and drop files from the iPod to the other machines.  Once they are out of the iTunes database, you can use just about any other music player to index and share the music across your local network.

---

### Post by arrrghhh on 2010-04-23
Well, tgalati4 is kinda right... but I think the user just wants to copy the MUSIC - not necessiarly the LIBRARY.  Am I correct, OP?

If that's the case, you can copy the music without issue, assuming it's DRM-free - which if you ripped it, should be the case.

DAAP is a good solution, but is just for streaming the music to another machine - you won't get copies of the music on both machines, just the ability to play the music on both machines.  Which may be sufficient for you.

---

### Post by HermanAB on 2010-04-23
Rsync is your friend.

---

### Post by dfreer on 2010-04-25
> **flatline said:**
> I have a **lot** of music.  After ripping nearly 1,000 CDs, my collection is well over 80GB.  All of this lives on my Macbook Pro in iTunes.  I'd like to keep a separate copy of it on my home server, which can be shared to the other computers in the house (HTPC and gaming rig, both running Win7 x64 Ultimate), but be able to sync the two libraries up as needed, so I don't have to rip every new CD twice.  

I thought that rsync might work, although I'm not sure how I would trigger it - probably from the laptop, since it's not always 'on' the network?  I'm assuming that any new CD will be ripped to the MBP and need to be synced to the server, but of course it would be optimal if the system could sync in either direction.  Anyone running a similar setup have suggestions?

I ended up having just one copy of my music library on my server (backed up manually of course), and just sharing it to my laptop. Using windows I would just map the share to a local network drive, and if I was away from the home network I'd use SSH/port tunneling to access the music share across the internet.

This of course isn't much of a solution if you like to listen to your music on your laptop when you have no internet connection, but maybe this would be acceptable to the OP.

---

