---
title: "GUI (XFCE) + VNC on Ubuntu Server"
date: 2008-08-23
forum: Server Platforms
---

### Post by cyrus_the_virus on 2008-08-23
Hi,

I need to have GUI with VNC server running on Ubuntu 8.04 Server. Preferable a light gui like XFCE. The VNC server should share the desktop of a single user account. Also the vnc session should be resumable. It will be an account that everyone in my network can use to download torrent files with azureus.

I searched around but I still have some questions:
- Can I install XFCE by just doing *sudo apt-get install xubuntu-desktop*?

- I also found this tutorial on how to install a VNC server:
[http://ubuntuforums.org/showthread.php?t=795036]("http://ubuntuforums.org/showthread.php?t=795036") Will this work with XFCE? The tutorial is for gnome and gdm. I'm not sure if XFCE uses gdm?

I do not want to install the desktop version, because this pc also hosts http, email, ftp and samba.

Marty

---

### Post by windependence on 2008-08-23
Why not use rtorrent? No X necessary and members here swear by it. It's an ncurses app which means it's a kind of semi GUI in a terminal window. Detachable too.

[http://libtorrent.rakshasa.no/](http://libtorrent.rakshasa.no/)

-Tim

---

### Post by cyrus_the_virus on 2008-08-23
Thanks! Will sure try that. Do you know if there excists this kind of program for usenet/binaries downloading? (like grabit on windows)

I would rather not install a GUI on my server, but the users in my home network are very basic pc users. I'm not sure if they will understand ssh with screen etc...

Before ubuntu I used opensuse on my server with which I could run gnome & vnc and still have a quite fast server. The idea was to save costs on power bills (one PC as both server and download machine, instead of 2 machines for each purpose). 

Marty

---

### Post by windependence on 2008-08-23
I'm not sure about the usenet stuff but we have so many people here that use rtorrent (I actually don't, I just use azureus on my Mac) that I think someone here surely will see this post and know the answer. Since this is an ncurses app, I think they might be able to use it even with little tech knowledge.

-Tim

---

### Post by salvador24 on 2009-02-16
I personally use SABnzbd+ for usenet/binary downloading on my headless Ubuntu 8.04 server.  It runs via a web interface, can have a watch directory for nzb files and can also integrate with newzbin if you have an acct there.  It also automatically pars and rars.  It is fantastic, and there is no need for X either.  I torrent with rtorrent as well BTW.  Good luck!

---

### Post by songshu on 2009-02-16
i noticed that a newer version of transmission has a web interface and it looks pretty smooth.

you can run it as a daemon i think so you don't need a desktop installed.

---

