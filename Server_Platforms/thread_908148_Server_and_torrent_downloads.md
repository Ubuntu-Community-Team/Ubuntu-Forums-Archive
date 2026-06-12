---
title: "Server and torrent downloads"
date: 2008-09-02
forum: Server Platforms
---

### Post by griz on 2008-09-02
I have a desktop setup with a standard Hardy install that is operating as a basic file and print server.  I would like to change it to a server install with limited if any graphics.  The problem that I have is that I download a lot of torrents (legal open source movies).  I currently use Ktorrent because of its schedule function (download torrents during off-peak download period).  Is there any way to set up a server system with no graphics that can download torrent files?  I think I have my head around setting up a LAMP server, which is something that I really want working 100%.

---

### Post by mihaiv on 2008-09-02
bittorent has a command line version.
```
sudo apt-get install bittorrent
```

---

### Post by Archmage on 2008-09-02
May I suggest rtorrent?

---

### Post by griz on 2008-09-02
Thanks for that, do those have the scheduling function as well though?

---

### Post by Archmage on 2008-09-04
> **griz said:**
> Thanks for that, do those have the scheduling function as well though?

Oh yes. You can configure it via a configure-file.

---

### Post by windependence on 2008-09-04
rtorrent seems to be what everyone likes around here.

OpenSource movies??????  Hehe.

-Tim

---

### Post by europa on 2008-09-04
I use torrentflux for my server.  It has a web gui and lets me add and start downloading torrents from anywhere.  It will also allow you to zip up the files and download them from the interface. Very handy to have around!

Check it out
[http://www.torrentflux.com/](http://www.torrentflux.com/)

sudo apt-get install torrentflux

---

