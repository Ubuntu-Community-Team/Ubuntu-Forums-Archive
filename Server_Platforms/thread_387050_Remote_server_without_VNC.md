---
title: "Remote server without VNC?"
date: 2007-03-17
forum: Server Platforms
---

### Post by bt86bt on 2007-03-17
Hi

I am new to setting up ubuntu-server and just have a quick question.

I have an old computer for seeding torrents and FTP. I want to be able to access it and VNC would be fine but it just that I thought it might take some CPU-load off if I disabled gnome (the gui for ubuntu) and just ran the terminal.

How do I set up so that ubuntu does not load gnome at startup and what clients should I use to set up a way to remotly controlll the terminal? I want to controll Ubuntu from a Windows-machine.

(and if you know any torrent-clients that automaticly downloads new torrents from a site that would be nice also)

Help will be greatly appreciated!

---

### Post by solar george on 2007-03-17
You can use ssh - install the openssh server and use [cygwin]("http://www.cygwin.com/") from windows to access it.

---

### Post by Nikron on 2007-03-17
[OpenSSH for a secure remote connection...]("https://help.ubuntu.com/community/SSHHowto")

Also, for your torrents you might want to look at

[www.torrentflux.com](www.torrentflux.com)

---

### Post by pjbgravely on 2007-03-18
To disable the Ubuntu GUI at boot:

sudo apt-get install rcconf
sudo rcconf
 uncheck gdm

rtorrent is a good command line torrent client. I run it in screen. I have a folder set up with nfs, that I drop .torrents into and then copy the completed files when they are done.

Paul

---

### Post by bt86bt on 2007-03-18
Thanks for all of your help!

---

