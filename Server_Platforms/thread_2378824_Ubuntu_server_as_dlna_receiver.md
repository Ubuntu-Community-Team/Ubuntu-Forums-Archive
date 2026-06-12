---
title: "Ubuntu server as dlna receiver?"
date: 2017-11-27
forum: Server Platforms
---

### Post by micindev on 2017-11-27
Hi everyone!

I'm new to Linux so bare with me please. 

I'm trying to build a dlna flac playback device from Intel d2700dc I've just found in basement. I would like to connect it to my DAC (only spdif and coax input) and send music (music only, flac, ogg, ape, mp3) stored on my synology NAS over dlna. I've tried xpenology, but it won't use optical output.

I've done a little research, but I'm still a bit confused and not sure if minidlna or rygel will work on headless Ubuntu, nor how to configure them. Or maybe there is other way?

---

### Post by SeijiSensei on 2017-11-28
minidlna is a DLNA server, not a client.  Don't know about rygel.

Apparently Amarok can work as a DLNA client: [https://userbase.kde.org/Amarok/Manual/Organization/Collection/RemoteCollections/UPnP]("https://userbase.kde.org/Amarok/Manual/Organization/Collection/RemoteCollections/UPnP").  So can VLC: [https://codeyarns.com/2015/01/25/how-to-use-vlc-as-dlna-client/]("https://codeyarns.com/2015/01/25/how-to-use-vlc-as-dlna-client/").

---

### Post by micindev on 2017-12-04
thanks,

sorry for late response, i was trying different distros but without luck...

so, theoretically, is it possible to turn on audio drivers, install amarok or rygel and let them wait for dlna? honestly, even if that is possible, i dont even know where to start or where to search...

---

### Post by Habitual on 2017-12-04
Plex.
The setup I utilized (Mac-server+Plex client = 2 packages)
It found all my AVI/MP4/mkv with barely any effort.
I followed a search_engine with this query:
```
dlna site:https://www.plex.tv
```

And it turned out to be simpler than Kodi (the other solution I attempted).

Naturally, you can extend this server-client solution on the desktop to a Roku as I managed.
Sign up for a free plex.tv account, add your dlna-server on their site, Add Plex app to Roku and you're golden.

Good Luck and have fun!

My plex setup allows me to play my iTunes Music. w00t

---

### Post by micindev on 2017-12-04
thanks for reply, but im not sure if this is a solution Im looking for... Im looking for solution to use ubuntu server as a dlna renderer with audio output via toslink. I dont really want to store any data on ubuntu server

---

### Post by micindev on 2017-12-05
please consider this thread as solved, I've found snakeoil os which works just as I imagined.
thanks

---

### Post by slickymaster on 2017-12-05
*Thread moved to **Server Platforms**.*

---

### Post by slickymaster on 2017-12-05
> **micindev said:**
> please consider this thread as solved, I've found snakeoil os which works just as I imagined.
thanks
How to mark your thread as [SOLVED]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")

---

