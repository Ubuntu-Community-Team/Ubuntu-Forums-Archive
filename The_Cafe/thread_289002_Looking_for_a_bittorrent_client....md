---
title: "Looking for a bittorrent client..."
date: 2006-10-30
forum: The Cafe
---

### Post by joeljkp on 2006-10-30
I'm looking for a bittorrent client that matches the following specifications:

[list]
[*] CLI or curses GUI, or daemon
[*] UPnP
[*] dynamic DNS support (outside IP detection, updating, etc.)
[/list]

Any suggestions?

---

### Post by mahy on 2006-10-30
> **joeljkp said:**
> I'm looking for a bittorrent client that matches the following specifications:

[list]
[*] CLI or curses GUI, or daemon
[*] UPnP
[*] dynamic DNS support (outside IP detection, updating, etc.)
[/list]

Any suggestions?

I thought Azureus does the trick, doesn't it? Even DDNS with some plugins, AFAIK.

---

### Post by kalle314 on 2006-10-30
> **joeljkp said:**
> I'm looking for a bittorrent client that matches the following specifications:

[list]
[*] CLI or curses GUI, or daemon
[*] UPnP
[*] dynamic DNS support (outside IP detection, updating, etc.)
[/list]

Any suggestions?

rTorrent!

It is a great ncurses client!
I don´t know about UPnP or DNS though, as I haven't cared to learn those abbreviations.

---

### Post by puppy on 2006-10-30
azureus can be a terrible resource hog - while other clients burble away in the background azureus seems to grab my entire bandwidth (I can hardly browse, even when its only downloading at 10k or so) - I wanted to try ktorrent but can't get it to work under Gnome (it's not in the repos either...)

---

### Post by Kateikyoushi on 2006-10-30
I second rtorrent, but look for the newest version, the one in the repos is half a year old.

---

### Post by GeneralZod on 2006-10-30
> **puppy said:**
> azureus can be a terrible resource hog - while other clients burble away in the background azureus seems to grab my entire bandwidth (I can hardly browse, even when its only downloading at 10k or so) - I wanted to try ktorrent but can't get it to work under Gnome (it's not in the repos either...)

The very latest release of KTorrent (2.0.3) should be available in the backports repository - I know because I installed mine from there :)

---

### Post by KaroSHi on 2006-10-30
> **GeneralZod said:**
> The very latest release of KTorrent (2.0.3) should be available in the backports repository - I know because I installed mine from there :)

^^ i can second this, ive been using ktorrent for a few months now, very happy with its performance. Its kind of like abc/utorrent.

---

### Post by jdong on 2006-10-31
KTorrent works great from GNOME for me. For some GNOME configurations, you need to first run "kdeinit", then start ktorrent. Do this if the tray icon for KTorrent doesn't show up, or shows up in unexpected places.

---

### Post by Hemmer on 2006-11-17
does anyone know of a lightweight bittorrent client like uTorrent (for windows)?

---

### Post by Choad on 2006-11-17
> **Hemmer said:**
> does anyone know of a lightweight bittorrent client like uTorrent (for windows)?
deluge is trying to be that, but its still under pretty heavy development. backend is libtorrent, written in c++ and very light, front end is trying to stay light but add enough creature comforts. written in python. its developed for the ubuntu project too :D

i use it, and it is not getting the speeds i want. apparently thats because DHT support is not enabled yet. in the next release (a few weeks down the line?) it will be enabled. apparently you will be getting very respectable speeds out of it then

---

### Post by zekt0r on 2006-11-17
You might want to give Transmission a try, it´s really good.
[http://transmission.m0k.org/](http://transmission.m0k.org/)

---

### Post by mazirian on 2006-11-17
Does deluge have a project page anywhere?  Oh, and, yeah, rtorrent is my favorite bt client.

---

### Post by Dirty Ole on 2006-11-17
deluge. Search for it in the forum.

---

### Post by Henry Rayker on 2006-11-17
rTorrent is VERY lightweight. text only, but once you get the hang of it, it is incredibly sweet.

---

### Post by zachtib on 2006-11-17
> **Choad said:**
> deluge is trying to be that, but its still under pretty heavy development. backend is libtorrent, written in c++ and very light, front end is trying to stay light but add enough creature comforts. written in python. its developed for the ubuntu project too :D

i use it, and it is not getting the speeds i want. apparently thats because DHT support is not enabled yet. in the next release (a few weeks down the line?) it will be enabled. apparently you will be getting very respectable speeds out of it then

Actually, 0.4 (with DHT support) is slated to be out next week.  There are debs on the project page of 0.4rc1.  It got pushed out a little earlier than we had originally planned because a couple of goals got deffered until the next release because they required massive code rewrites.

> **mazirian said:**
> Does deluge have a project page anywhere?  Oh, and, yeah, rtorrent is my favorite bt client.

Deluge's project page is [http://deluge-torrent.org](http://deluge-torrent.org), and we have a support forum here at ubuntuforums.org, check my sig for a link.

That said, Deluge doesn't currently have all the features that the OP asked for, in particular the ncurses interface.  However, it's my primary goal for the 0.5 development cycle to daemonize the backend so that it can run independent of the user interface, at which point it should fulfill your needs nicely.

---

