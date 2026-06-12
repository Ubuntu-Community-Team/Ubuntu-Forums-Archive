---
title: "Media Organizer (TV, Movies, Music) on headless?"
date: 2011-07-20
forum: Server Platforms
---

### Post by GriFF3n on 2011-07-20
I have an Ubuntu server and use it to stream videos and music to my remote XBMC computer connected to my TV via Samba. The computer connected to my TV has Windows 7 and is used mostly for just XBMC. Everything works great with this setup, but I would like to organize all my videos through the server. Is there any software out there that does this headless? Or with a Web GUI? Any info would be great on this subject. Thanks fellas,

GriFF

---

### Post by arrrghhh on 2011-07-20
I just use samba, or forward X over ssh & use dolphin "on" the server...  It's pretty slow the latter way, the former works really well for me.

There's been some discussion on a webUI for this, but I haven't seen anything come to fruition.

---

### Post by cariboo on 2011-07-20
I use XBMC on top of Natty, and auto connect via /etc/fstab and nfs to the server. My music collection isn't organized at all, I just dump up to 2000 files in a directory, currently I have 7 music directories. 

My video collection is organized by series name/season/show name/episode number for TV shows, and series name/title for ripped dvds, if they have any sequels, and just by dvd name for the others.

My DVD collection only consists of 125 DVDs, so it easy to keep track of them, but the tv series collection consists of over 1800 separate files, so I've made a bit more of an effort to keep them organized.

---

### Post by JackandJohn on 2012-08-12
In case anyone runs across this, or the original posters are still monitoring:

plexmediaserver (apt-get install plexmediaserver) runs headless, has a webGUI for organization, and will not only serve content locally through the Plex client, but will also transcode to iOS, android, ps3, xbox, DNLA devices, Roku, etc, etc, etc.

It's best thought of as a properly done server-client version of XBMC.

[http://www.plexapp.com/getplex/index.php](http://www.plexapp.com/getplex/index.php)

---

