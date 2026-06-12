---
title: "rTorrent, mktorrent and own tracker"
date: 2010-09-15
forum: Server Platforms
---

### Post by Domen91 on 2010-09-15
Hi!

I successfully install rtorrent with wtorrent for web (it's working :D ).

Question: How to make torrent with own tracker for my server?
How to make a torrent and seed it to a tracker (rtorrent)??

I hope, you understand me :D

Similar as in uTorrent: make torrent and seeding to other [COLOR=#000000]neighbours (with own tracker address - [http://ip:port/announce](http://ip:port/announce)) - [http://www.utorrent.com/documentation/make-a-torrent](http://www.utorrent.com/documentation/make-a-torrent) (The tracker)

best regards, domen

Edit:

When I make torrent witk mktorrent-1.0 and upload to rtorrent, it says **"**[/COLOR]**Tracker: [Could not parse bencoded data]     **[COLOR=#000000]**"**The port is set correct.

Edit 2: Major question is which IP I mus write under the Trackers???? I test with my IP and port but is not work (in uTorrent you write [http://myIP:port/announce](http://myIP:port/announce) and is working - how is this in rtorrent??).

Please, help.
[/COLOR]

---

### Post by Bytesunfish on 2010-09-16
Similar problem. Subscribed.

Mayor Bytesunfish

---

### Post by Domen91 on 2010-09-17
Solved! :p

Download Bittorrent tracker here: [http://download.bittorrent.com/dl/BitTorrent-4.0.0-GPL.tar.gz](http://download.bittorrent.com/dl/BitTorrent-4.0.0-GPL.tar.gz)

And follow the instruction here: [http://vorg.ca/1480-How-to-set-up-a-BitTorrent-tracker-on-Linux](http://vorg.ca/1480-How-to-set-up-a-BitTorrent-tracker-on-Linux)

I used this only for tracker; for client I used rTorrent.

---

