---
title: "[IDEA] Community Torrent Mirror 'Mesh'"
date: 2007-10-18
forum: Ubuntu Brainstorm
---

### Post by bobbocanfly on 2007-10-18
Summary:
A simple community program that would stop a large amount of the problems caused by server overload on release days. Simply everyone with ~1mb of spare hosting space sets up a small mirror with all the torrents on them. This is linked to from the main Ubuntu downloads page and each mirror links interlink to every other mirror

Scope and Use Cases:
Most people in the Ubuntu Community want the latest patches and goodies that come with every release as soon as possible. This leads to them rampaging onto the servers in search of the downloads. A good chunk of these people will want the torrents. 

Implementation:
People simply email the admin of the project who builds up a list of mirrors. He/she then releases the full list all HTML'd up ready to be pasted onto a web page. Each torrent mirror admin then uplaods it along with the torrents and everything is ready.

Why its useful:
The Ubuntu server is slowed by people directly downloading the ISO's which means the torrenters have a hard time getting to the torrents. This would let them get to the torrent files easier and also make download speed for everyone quicker.

Just a quick idea i came up with after this morning. Any comments/suggestions?

---

### Post by Awalton on 2007-10-18
You mean like Apt-Torrent:
[http://sianka.free.fr/](http://sianka.free.fr/)

---

### Post by Zdravko on 2007-10-18
Yeah - this feature will lighten the servers a bit.

---

### Post by bcherry on 2007-10-18
darn.  I'd just suddenly had an idea:
when downloading the iso on release day, get it from torrents as the servers are bogged down.  But if you're upgrading, the servers are bogged down as well.

my idea was this: "What if you made a package manager and/or modified apt-get with a --distrib option or something that would download the packages from a distributed network i.e. bittorrent.  Normally I'd imagine not too many seeders (no more than the standard mirror list) but on release day when thousands or more (i really have no idea) people are dl'ing the same packages, this would make it much faster."

Looks like apt-torrent already accomplishes this.  I'll look into it more.

---

### Post by Zdravko on 2007-10-19
[bcherry]("http://ubuntuforums.org/member.php?u=120098"), this is an even better idea.

---

