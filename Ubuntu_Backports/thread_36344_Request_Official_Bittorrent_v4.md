---
title: "Request: Official Bittorrent v4"
date: 2005-05-23
forum: Ubuntu Backports
---

### Post by bored2k on 2005-05-23
[CENTER][http://www.bittorrent.com/](http://www.bittorrent.com/)[/CENTER] 
[center][img]http://img268.echo.cx/img268/2644/bittorrentlogo7rm.gif[/img][/center]
It would be nice to get its upgrades (right now repositories have the old 3.4). Currently it's on stable 4.0.1 and BETA 4.1.0 with trackerless and internationalization support. This is a real needed file for users like me who dislike giving away 3/4 of their RAM to Azureus Java client. Plus, it's very pretty (GTK 2) :D.

---

### Post by pdk001 on 2005-05-23
what's that application?

---

### Post by jdong on 2005-05-23
I've been looking at this for a while now, and it doesn't seem to backportable at the moment. Current patches do NOT work against the new Bittorrent, and the FAQ's method of generating debs creates such CRAP that I will not release them. Heck the deb that they offer on their homepage is BROKEN... (wonder how much testing went into that ;) *cough* alien *cough*)


As soon as I can, I WILL get proper packages for Bittorrent 4.

---

### Post by bored2k on 2005-05-23
[QUOTE=jdong]I've been looking at this for a while now, and it doesn't seem to backportable at the moment. Current patches do NOT work against the new Bittorrent, and the FAQ's method of generating debs creates such CRAP that I will not release them. Heck the deb that they offer on their homepage is BROKEN... (wonder how much testing went into that ;) *cough* alien *cough*)


As soon as I can, I WILL get proper packages for Bittorrent 4.[/QUOTE]
 Thanks. It's quite amazing how the "official" .deb's only use is to screw up your current gnome-bt/bittornado/bittorrent.

---

### Post by JonahRowley on 2005-05-23
[QUOTE=jdong]Heck the deb that they offer on their homepage is BROKEN...[/QUOTE]

I use that deb, it works fine for me..

---

### Post by bored2k on 2005-05-23
[QUOTE=JonahRowley]I use that deb, it works fine for me..[/QUOTE]
 Here I get sprayed a "line not found [yattayattayatta]!".

---

### Post by jdong on 2005-05-24
Yeah, it bombs out for me, too. With or without removing all existing Bittorrent.

---

### Post by Belarios on 2005-05-26
I moved /usr/lib/python2.3/site-packages/Bittorrent to /usr/lib/python2.4/site-packages/Bittorrent and that fixed my errors.

I'd also appreciate this in backports.  Keep up the good work.

---

### Post by jdong on 2005-05-26
Yeah, that's the only change truly necessary, but it still doesn't follow Debian standards (MIME integration, .desktop icon generation, lintian, and so on).

---

### Post by brian g on 2005-10-12
whats the status on this?
torrent sites are banning gnome-bittorrent (which identifys itself as Python-urllib/2.4) The current version of BitTornado in backports (0.3.11) is old. I refuse to use azeurus as that program is a bloated joke.
can we get some kind of decent current bit torrent client in some kind of repository for hoary?

---

### Post by bored2k on 2005-10-12
BitTornado 0.3.13 has been out for a while now. I'm on Breezy and  I don't even think Breezy repositories has it. Solution? Download the .tar.gz package and use that, which is what I'm doing.  I'd really like updated BitTorrent clients, but I guess that's what we have to do ATM.

---

