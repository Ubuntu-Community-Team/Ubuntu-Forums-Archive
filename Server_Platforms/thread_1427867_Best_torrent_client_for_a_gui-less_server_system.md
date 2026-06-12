---
title: "Best torrent client for a gui-less server system?"
date: 2010-03-12
forum: Server Platforms
---

### Post by espressobeanie on 2010-03-12
Can someone tell me what the best gui-less torrent client is for an Ubuntu server? I heard rtorrent was decent. Is that the only one?

---

### Post by amrypma on 2010-03-12
I use rtorrent. in a screen session.

---

### Post by smeerbartje on 2010-03-12
There are many options; like amrypma mentioned, rtorrent works fine. I prefer transmission, just a matter of taste I think :).

---

### Post by BobVila on 2010-03-12
> **smeerbartje said:**
> There are many options; like amrypma mentioned, rtorrent works fine. I prefer transmission, just a matter of taste I think :).

You may want to look into a combination of rtorrent and wtorrent. I've been using it and like having the webUI available. The learning curve is certainly a bit lower than std CLI rtorrent, but it wouldn't hurt to learn it while you're at it.

---

### Post by jfmanamtr on 2010-03-12
I use torrentflux on my server. It is a webbased GUI, that way I can accesses it from any PC & download what I need.
 
~John

---

### Post by Dayofswords on 2010-03-12
i hear rtorrent is good

deluge can be used without a gui

---

### Post by phillips321 on 2010-03-13
torrentflux or torrentflux-b4rt,

was using torrentflux for years but switched over to torrentflux-b4rt about 6 months ago.

torrentflux is as simple as:

sudo apt-get install torrentflux

then browse to your server: [http://192.168.1.100/torrentflux](http://192.168.1.100/torrentflux)


SIMPLES!

---

### Post by bartos on 2010-03-13
> **phillips321 said:**
> torrentflux or torrentflux-b4rt,

was using torrentflux for years but switched over to torrentflux-b4rt about 6 months ago.

torrentflux is as simple as:

sudo apt-get install torrentflux

then browse to your server: [http://192.168.1.100/torrentflux](http://192.168.1.100/torrentflux)


SIMPLES!

+1

Torrentflux also has a directory listing of your torrents that you can download.great program.

---

### Post by The Real Dave on 2010-03-14
rTorrent :) I love it :) You can also get WebUIs for it now, Avalanche is one I believe.

---

### Post by Cas07 on 2010-03-14
After trying several several torrents clients the latest version of [Deluge]("http://dev.deluge-torrent.org/wiki/About") 1.2.1 is perfect for a headless server with a superb webui and remote GTK client!

---

