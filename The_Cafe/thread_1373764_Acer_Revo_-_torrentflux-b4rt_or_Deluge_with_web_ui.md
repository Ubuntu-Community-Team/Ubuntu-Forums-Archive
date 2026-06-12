---
title: "Acer Revo - torrentflux-b4rt or Deluge with web ui?"
date: 2010-01-06
forum: The Cafe
---

### Post by melat0nin on 2010-01-06
Hi all

I've bought an Acer Aspire Revo nettop, which I intend to use as an HTPC to replace my aging (and loud and power hungry) Shuttle.

I intend to install Karmic 9.10 on it, along with XBMC 9.11 (Camelot). I'm wondering which torrent client to install.

At present I use torrentflux-b4rt, but something tells me it's a bit overkill for the amount of torrenting I do (I could be wrong). Having to have a web server + sqllite etc installed, just for that one app, seems to be a bit resource-heavy when it doesn't do anything else webserver-related.

So I was thinking instead of moving to Deluge, along with its web UI. The Ajax-ified skin is beautiful, and I think it has most of the features of b4rt (except user accounts). It also means no overhead of apache/lighttpd and a database server.

Does this make sense do you think? I intend to leave the machine running 24/7, and AFAIK the Deluge daemon can be run on startup, along with the web UI, which can be accessed easily enough from the outside world via dynamic DNS.

Any thoughts would be appreciated, not to mention people's experiences torrenting on the Revo.

---

### Post by melat0nin on 2010-01-07
Any thoughts? I'm guessing the deluge daemon with web ui uses less resources, but I could be wrong. Bearing in mind the specs of the Revo (Atom 1.6GHz, 1gb ram) this might be a consideration. Lean and mean is the aim of the game.

---

### Post by 23meg on 2010-01-07
It's a good setup and you're unlikely to have problems.

The Deluge daemon's resource usage will be negligible with such a *powerful* processor as an Atom, and *so much* ram as 1GB.

---

### Post by markp1989 on 2010-01-07
i used to use torrentflux (not the b4rt version) and changed to deluge web ui, i prefer deluge becuase i can set global download limits , when stock torrentflux could only set per torrent limits ( i dont know if b4rt version can do this or not) 

my recomendation goed to deluge.

the revo is plenty powerfull enough to run many torrents , my first torrent slave was a slow slot based pentium with 256mb of ram lol, my sis has a revo and its a good little machine, not good for number crunching or gaming , but will handle most other tasks with ease

---

### Post by melat0nin on 2010-01-07
I think I'll go with Deluge, starting the daemon with the web UI at startup. Seems sensible because it's self-contained and doesn't require a full-blown (even if lightweight) HTTP server, plus database server, which is total overkill for that one job.

On another note, I tried the Revo with a 1080p mkv and it runs like a dream with XBMC and VDPAU :)

---

### Post by drawkcab on 2010-01-07
I have a revo too.  My only complaint is that it does not have enough snort to power through flash video in Linux--no surprises there I guess.  Everything else runs really really well.

---

### Post by PurposeOfReason on 2010-01-07
rtorrent + rutorrent is by far better.

---

### Post by melat0nin on 2010-01-08
> **PurposeOfReason said:**
> rtorrent + rutorrent is by far better.

Care to say why?

---

### Post by PurposeOfReason on 2010-01-08
> **melat0nin said:**
> Care to say why?
Overall control you have over the torrents, least resources, best UI.

---

### Post by markp1989 on 2010-01-09
> **PurposeOfReason said:**
> rtorrent + rutorrent is by far better.

that does look decent, are there any up to date how tos for running rutorrent  in 9.10? i wana give it a go.

---

### Post by PurposeOfReason on 2010-01-09
> **markp1989 said:**
> that does look decent, are there any up to date how tos for running rutorrent  in 9.10? i wana give it a go.
[http://ubuntuforums.org/showpost.php?p=7843014&postcount=7](http://ubuntuforums.org/showpost.php?p=7843014&postcount=7)

The numbers for size won't be right over a certain size unless you compile xmlrpc >= 1.11 but it doesn't break anything so I never bothered.

SS of what I mean.

---

### Post by melat0nin on 2010-01-11
> **PurposeOfReason said:**
> Overall control you have over the torrents, least resources, best UI.

I can't comment on the resources or control, but the deluge 1.2.0 web UI is beautiful and has all the power of a fully-fledged desktop application.

I just spend ages getting it working though, so I'm not gonna go through that again :) if i find myself in this position again, e.g. after a reformat, i'll consider rtorrent + rutorrent :D

---

