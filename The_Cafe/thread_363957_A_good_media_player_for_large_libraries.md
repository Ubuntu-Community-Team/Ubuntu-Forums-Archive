---
title: "A good media player for large libraries?"
date: 2007-02-17
forum: The Cafe
---

### Post by muguwmp67 on 2007-02-17
I've been trying out different media players, but they all seem to have a problem with my music collection.  I have almost 20,000 music files, and the only media player I've used so far that even comes close to working is amarok, but its a kde app and really runs poorly in gnome for me.  I've crashed rhythmbox and exaile each time I've tried to load my library into them.

I like amarok a lot, but it takes forever to load, and sometimes doesn't load correctly.  Are there options in gnome that I haven't considered yet?  

Is it worth moving to kde just to use amarok?

---

### Post by Tuna-Fish on 2007-02-17
One word: Exaile!

---

### Post by spockrock on 2007-02-17
amarok handles my 20K+ of music better then anything else, except for foobar2000....but thats windows.

---

### Post by muguwmp67 on 2007-02-17
> **spockrock said:**
> amarok handles my 20K+ of music better then anything else, except for foobar2000....but thats windows.
Are you using it in KDE or Gnome?  If so, have you plugged it into an alternate SQL engine, or are you using the default?

---

### Post by pmj on 2007-02-17
MPD is by far the most efficient music manager.... thingy I've used. MPD together with GMPC as a frontend has no problems with my 56k songs.

---

### Post by IYY on 2007-02-17
I've never had a collection this large, so I don't know which players would have trouble with it. Have you tried Banshee?

---

### Post by tbroderick on 2007-02-17
+1 for mpd. I also really like cmus.

---

### Post by Mateo on 2007-02-17
Does GMPC minimize to the tray?

---

### Post by pmj on 2007-02-17
> **Mateo said:**
> Does GMPC minimize to the tray?

Yes, it does.

---

### Post by Mateo on 2007-02-17
oh sweet I might give it a try then.

---

### Post by slimdog360 on 2007-02-17
> **muguwmp67 said:**
> Is it worth moving to kde just to use amarok?

its worth moving to kde just because its kde. nuff said.

---

### Post by Mateo on 2007-02-17
a couple more things.  First, will it export playlists (m3u)?  that's kind of a big deal for me and I don't want another application for doing just that.  Also, does mpd and gmpc run seperately?

---

### Post by FrankVdb on 2007-02-17
If you want Amarok to be fast with large collections, open your settings and make sure you select MySql instead of the Lite thing that comes standard. SQL Lite causes a terrible lag with large collections.

---

### Post by pmj on 2007-02-17
> **Mateo said:**
> a couple more things.  First, will it export playlists (m3u)?  that's kind of a big deal for me and I don't want another application for doing just that.  Also, does mpd and gmpc run seperately?

It can create playlists, but the songs in them will have full paths, so they may not be useful to you. And yes, MPD and GMPC does run separately. MPD is a server and GMPC is one of several clients that let you control MPD. It can take a while to set it up, but it's well worth it.

---

### Post by maniacmusician on 2007-02-17
As others have said, Amarok with an SQL backend is the best for large collections. 

Directions for setting up mysql are at the amarok wiki: [http://amarok.kde.org/wiki/MySQL_HowTo](http://amarok.kde.org/wiki/MySQL_HowTo)

you can ignore the first bit they have about compiling it with the --enable-mysql option, because the Ubuntu version comes with it already enabled. You just have to install mysql and configure it as they tell you on that page.


a little off-topic; with a collection that large, what file format do you store your music in? how much disk space does it occupy?

---

### Post by pmj on 2007-02-17
> **maniacmusician said:**
> a little off-topic; with a collection that large, what file format do you store your music in? how much disk space does it occupy?
If you're asking me, my collection is 56338 songs and 372.3GB, unless I forgot to count something. And nearly all of it is MP3.

---

### Post by muguwmp67 on 2007-02-17
I'm at 24484, 111.1 GB.  I loved emusic when it was 'all you can eat', and ripped most of my CD collection (250 cd's or so) a few years ago.  In the event of an emergency, I can listen to 10 weeks 3 days worth of music without repeats.

---

