---
title: "which Bittorrent client fot Bit-colo"
date: 2010-05-26
forum: Server Platforms
---

### Post by exssrerion on 2010-05-26
I've a plan to make Bittorrent Colocation.
 
It like web hosting, the different is customer are rent space for download bittorrent.
Because internet bandwidth in my country is very slow.
So it have multi-user on this server
 
What bittorrent client I use?
 
thankyou

---

### Post by sylvester_0 on 2010-05-26
Transmission has a nice and simple interface. I guess you could set up a different copy for each client and run them on different ports...

---

### Post by cadriel on 2010-05-26
There's also the rTorrent / ruTorrent combination. ruTorrent now supports multi-user mode against one instance of rTorrent, or you can run it for seperate instances of rTorrent.

The best thing about this combination is that ruTorrent has built-in broadcatching support too. rTorrent is also really effecient and has a low memory footprint.

The only gotcha i've found is that in order to have blocklist support and xmlrpc support - you need to apply a patch and compile yourself. It's also worthwhile self compiling a more recent version of xmlrpc-c as ubuntu's version is really old.

---

### Post by dudumomo on 2010-05-27
I really like using Deluge-torrent, and not really transmission.
But for what you want to do, I strongly recommend you to go for **rtorrent** !

This will entirely suit your needs.

---

### Post by exssrerion on 2010-05-27
thank you very much

---

### Post by volkswagner on 2010-05-27
[TorrentFlux]("http://www.torrentflux.com/") is an option also.  You can have multi-Users login also.  I have not spent much time with it, but I did have one unresolved issue with displaying search results for some servers.  Just make sure you test thoroughly before putting into service.

---

