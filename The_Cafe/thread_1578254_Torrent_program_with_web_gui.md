---
title: "Torrent program with web gui"
date: 2010-09-20
forum: The Cafe
---

### Post by Spindles on 2010-09-20
Hey Everyone,

Does anyone know of a decent torrent program with a web gui that allows you to select the destination folder for individual torrents?

I've tried torrentflux, but that doesn't allow you to choose download location, neither does the Transmission web interface.

I've got a netbook remix of Lucid which I use for XBMC. It has a 1TB external USB drive attached to it and I would like to be able to download stuff to the directory structure on the external drive over a web interface.

Cheers in advance,

Spindles

---

### Post by roddie on 2010-09-20
There is a Linux uTorrent alpha which might support it. I've not tried it myself because the media server I have runs Windows 7 and (obviously) I've no issues accessing the webUI from Ubuntu. Might be worth a look though.

[http://forum.utorrent.com/viewtopic.php?id=83506](http://forum.utorrent.com/viewtopic.php?id=83506)

---

### Post by MJWitter on 2010-09-20
Deluge allows selecting the destination from the web interface, although I'm not sure if that feature is present in the Lucid version or if you need the deluge ppa, which is the version I have installed.

---

### Post by ugm6hr on 2010-09-20
> **roddie said:**
> There is a Linux uTorrent alpha 

The WebUI works fine with uTorrent + Wine - although I no longer use it - but if it allows choice of folders, I don't see why it shouldn't work.

---

### Post by NCLI on 2010-09-20
I'd recommend Deluge, [it can also sync with a remote GUI]("http://dev.deluge-torrent.org/wiki/Faq#Daemon").

---

### Post by markp1989 on 2010-09-20
Id say try deluge, torrentflux  , and rtorrent

deluge and torrentflux are easy to set up the web ui torrentflux is webui only, rtorrent is abit more complicated to get a web front end going.

---

### Post by Spindles on 2010-09-20
Cheers for the suggestions everyone.

I'll give Deluge a try, and if that doesn't work I'll go for the uTorrent alpha or the Wine option.

---

### Post by undecim on 2010-09-20
I have deluge from the PPA running on my server. I have to start deluged and deluge-web manually via SSH when the server gets reset, but it works fine.

---

