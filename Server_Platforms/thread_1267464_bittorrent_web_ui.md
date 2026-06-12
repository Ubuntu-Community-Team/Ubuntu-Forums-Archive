---
title: "bittorrent web ui"
date: 2009-09-15
forum: Server Platforms
---

### Post by Entity` on 2009-09-15
I'm looking to build a small server to act as my bittorrent pc.  I also want to be able to manage it with some sort of slick (java or flash) web ui since it is meant to be headless and used only for bittorrent.  I already have the hard drives (4x 1TB) and appropriate SATA controller (the mobo doesn't have any SATA ports) and so on and so forth.

I'm trying to build a web interface for my server so I can manage it wherever I go.  Is it possible to build a web ui that acts like a normal (somewhat) desktop, or would it be better just to ssh login and use the text based gui?  And if it's do-able, what bittorrent client would be compatible to such a UI?  Should I just give up and use Vuse (I don't really like it because it seems too bloated), or hunt down an old version of Azureus?  Thanks for any help.

---

### Post by volkswagner on 2009-09-15
Check out [TorrentFlux]("http://www.torrentflux.com/") for a web based torrent server/client.  Check out [Webmin]("http://www.webmin.com/") for everything else.

---

### Post by enriqueaf on 2009-09-15
I have done that at my home, I have used [transmission]("http://www.transmissionbt.com") it has a native web client, which in my opinion is better than TorrentFlux, which I have also used. And if you can is better to not left the web client opened directly to the world if not use an ssh tunnel.

---

### Post by Entity` on 2009-09-15
Thanks very much for your help volkswagner, those links will help me out a lot.

enriqueaf, perhaps that would be a good idea (i may do that since I'm the only one who would have any reason to access it), but I'm doing this (partly) for a college class as a way to get hands on experience.

---

### Post by grantemsley on 2009-09-16
On my home server I use Vuze (you can turn off the Vuze interface and go back to the old azureus one) inside VNC.

On my other server, I use ruTorrent, which is a frontend to rtorrent, a cli based torrent client.

[http://code.google.com/p/rutorrent/](http://code.google.com/p/rutorrent/)

It works wonderfully.

---

### Post by Udayakiran on 2009-09-18
Try using rTorrent and some web UI plugin if the server will not have any GUI.

Else, try using transmission. I heard it works very well. I think you can also use uTorrent+wine+webUI plugin, though i'm not sure the webUI plugin will work on wine. Maybe some other user can confirm it?

---

### Post by MJWitter on 2009-09-18
From those I have used, Deluge has been the best mix of ease of use and features.

---

