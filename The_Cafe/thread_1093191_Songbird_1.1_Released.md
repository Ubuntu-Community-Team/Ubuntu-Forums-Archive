---
title: "Songbird 1.1 Released"
date: 2009-03-11
forum: The Cafe
---

### Post by gloscherrybomb on 2009-03-11
The newest version of songbird (1.1) has been released.

For all new features (including album art fetching) see here:

[http://blog.songbirdnest.com/2009/03/10/songbird-11-is-here/]("http://blog.songbirdnest.com/2009/03/10/songbird-11-is-here/")

It seems you just extract the folder and run the program bin directly from it, is that correct?

---

### Post by bvanaerde on 2009-03-11
> **Watch Folders**
You can choose to watch a folder hierarchy for changes and the content will auto-magically be imported in your library. If a file is removed from the watched folder, the corresponding track will be deleted from your Library.
I think a lot of people have been waiting for this feature:D

---

### Post by Dragonbite on 2009-03-11
Can it watch a networked folder?  I have my music on the server and I would prefer to not have to import everything into my local drive so I'm managing two locations.

(same idea with pictures, but that's another story)

---

### Post by Spike-X on 2009-03-12
> **bvanaerde said:**
> I think a lot of people have been waiting for this feature:D
I know I certainly have!

---

### Post by kk0sse54 on 2009-03-12
> **gloscherrybomb said:**
> 
It seems you just extract the folder and run the program bin directly from it, is that correct?

Yes, however I prefer to actually install through my package management system.

---

### Post by smartboyathome on 2009-03-12
> **Dragonbite said:**
> Can it watch a networked folder?  I have my music on the server and I would prefer to not have to import everything into my local drive so I'm managing two locations.

(same idea with pictures, but that's another story)

I am guessing it can if you mount it as a local filesystem (ie, using something similar to the mount command for other partitions).

EDIT: I wish they would finally get the ability to restore a closed tab, and the ability to use more than one window. Those are two features I desperately need.

---

### Post by JackieChan on 2009-03-13
I'm still waiting for a visualizer. :neutral:

---

### Post by Sinkingships7 on 2009-03-13
The day Songbird develops a good-working equalizer is the day I leave iTunes forever.

---

### Post by regonzal on 2009-03-13
I have always been interested in this player, I just wish it could better blend into the themes I use with Ubuntu; I know, just being picky here :P

---

### Post by Islington on 2009-03-13
> **smartboyathome said:**
> I am guessing it can if you mount it as a local filesystem (ie, using something similar to the mount command for other partitions).

EDIT: I wish they would finally get the ability to restore a closed tab, and the ability to use more than one window. Those are two features I desperately need.

ctrl+shift+t doesnt work?

---

### Post by binbash on 2009-03-13
debs : [http://www.getdeb.net/app/Songbird](http://www.getdeb.net/app/Songbird)

---

### Post by Johnsie on 2009-03-13
Does it play/rip cd's yet?

---

### Post by legolas_w on 2009-03-13
I was an Amarok user before songbird 1.0. and now I prefer using songbird more than any other media player specially Amark2.
If it had some minimize to tray feature I would call it a feature complete media player for audio based media

---

### Post by CraigPaleo on 2009-03-13
> **binbash said:**
> debs : [http://www.getdeb.net/app/Songbird](http://www.getdeb.net/app/Songbird)

Thanks! You read my mind.

---

### Post by gloscherrybomb on 2009-03-13
> **Sinkingships7 said:**
> The day Songbird develops a good-working equalizer is the day I leave iTunes forever.

The next release (May) will have an equaliser

---

### Post by Audrey Hepburn on Crack on 2009-03-13
> **gloscherrybomb said:**
> The newest version of songbird (1.1) has been released.

For all new features (including album art fetching) see here:

[http://blog.songbirdnest.com/2009/03/10/songbird-11-is-here/](http://blog.songbirdnest.com/2009/03/10/songbird-11-is-here/)

It seems you just extract the folder and run the program bin directly from it, is that correct?

Thanks for the info, but with Pandora I hardly find Songbird relevant.

Technically, you might say Songbird is a little too little and a little too late.

Nice effort by the devs though

:popcorn:

---

### Post by CraigPaleo on 2009-03-13
> **Audrey Hepburn on Crack said:**
> Thanks for the info, but with Pandora I hardly find Songbird relevant.

Technically, you might say Songbird is a little too little and a little too late.

Nice effort by the devs though

:popcorn:

Isn't Pandora just Internet radio? It may be nice if you don't already have your own music stored locally -- or am I missing something?

---

### Post by Sinkingships7 on 2009-03-13
> **gloscherrybomb said:**
> The next release (May) will have an equaliser

Source? If this is true, I'm really excited! :D

---

### Post by Sand &amp; Mercury on 2009-03-13
Have they made any effort to make the program a bit lighter on memory?

---

### Post by Changturkey on 2009-03-13
Is Songbird QT or GTK?

---

### Post by kpkeerthi on 2009-03-13
Great News! I will hold until this [bug]("http://bugzilla.songbirdnest.com/show_bug.cgi?id=12261") is fixed

---

### Post by kk0sse54 on 2009-03-13
> **Sand & Mercury said:**
> Have they made any effort to make the program a bit lighter on memory?

Not really, songbird remains and I think will always be one of the more heavier media players around. It's definitely not for those looking for to set up a system of low ram usage. However that being said for me the ram usage is a conceded point when comparing it to other full fledged media players since I've had fantastic performance with my large library as opposed when I tried Banshee. That was of course before I met MPD + ncmpcpp which equals perfect bliss for me these days.

---

### Post by Dragonbite on 2009-03-13
> **Changturkey said:**
> Is Songbird QT or GTK?

Isn't it the Mozilla tookbox, which isn't Qt or GTK (and not Gecko, that's the browsing engine.. but I can't remember what mozilla calls it)

---

### Post by mehaga on 2009-03-13
XUL. But, why does it matter if it's QT or GTK or...?

---

### Post by Firestem4 on 2009-03-13
I downloaded the update yesterday. THey really did a good job with this update. I have been waiting for folder watching and artwork-fetching. Can't wait for the next round of updates.


> **Sand & Mercury said:**
> Have they made any effort to make the program a bit lighter on memory?

Yes they have. If you read the release notes, the list of major changes include fixing a lot of memory leaks and optimizing parts of their program to use less memory. The biggest change is the 40% cut in CPU usage [for large libraries]. I have a 30 gig music library O.O This is good news for me.

For the person asking about an Equalizer and other features: [http://wiki.songbirdnest.com/Roadmap](http://wiki.songbirdnest.com/Roadmap)

---

### Post by Sinkingships7 on 2009-03-13
> **firestem4 said:**
> 
for the person asking about an equalizer and other features: [http://wiki.songbirdnest.com/roadmap](http://wiki.songbirdnest.com/roadmap)

:d

---

### Post by timjohn7 on 2009-03-13
Although a visualizer would be great, I'd give CD playback and CD Ripping priority.  The devs should look at ripperx and incorporate its simplicity and reliability to move Songbird to a complete suite.

---

### Post by Teabicky on 2009-03-13
I'd love to see MTP device support.  I wouldn't need any other player then.

---

### Post by jaebe2 on 2009-03-14
> **C!oud said:**
> Yes, however I prefer to actually install through my package management system.
How do I do that?
I have downloaded the tar archive. I also heard about getting a deb package. How do I get my system to do it through package management?

---

