---
title: "torrent &amp; server-only install"
date: 2005-11-19
forum: Server Platforms
---

### Post by Zelut on 2005-11-19
I've got a server-only install of Breezy 5.10 running ISPConfig and hosting (currently) two websites.  I would also like to utilize this server to share the Ubuntu .torrent files, but I don't know how to do this without having access to a gui.  We recently installed a fiber-optic (15M/15M) connection so I've got plenty of bandwidth to spare!

Can someone tell me how I can share the .iso/.torrent from my server-only installation?

---

### Post by herrpoon on 2005-11-20
Sorry, I am confused, are you looking for a torrent client to put on your server?

If I've understood you correctly, then something like torrentflux would work well.

---

### Post by Zelut on 2005-11-20
Yeah.  I need a non-gui torrent client.  Currently I use Azureus or bittorrent (gnome), but I need a non-gui...

---

### Post by apjone on 2005-11-20
bittoreent has a command line interface as well 

root@GHOST:~# btdownloadcurses

---

### Post by herrpoon on 2005-11-20
As I said in my previous post torrentflux would work well.  Taken from their website,

" TorrentFlux is a FREE PHP based Torrent client that runs on a web server. Manage all of your Torrent downloads through a convenient web interface from anywhere. "

It's very easy to setup and you can choose either bittornado or bittorrent to use  on it, I use it and it works a treat!

---

