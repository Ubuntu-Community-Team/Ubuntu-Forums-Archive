---
title: "transmission-daemon details?"
date: 2008-11-09
forum: Server Platforms
---

### Post by sparrowkc on 2008-11-09
I'm setting up a home server, and I want it to be able to download torrents.  I think transmission-daemon is what I want.  It's part of the transmission-cli package.  It seems to work, I can access the web interface once it's running, but it fails and exits when I try to download a torrent.  Also, the man page does not list any arguments to select listen port, encryption, etc.  Is this supposed to run on top of something else?

---

### Post by sparrowkc on 2008-11-10
I think I understand now.  You can give transmission-daemon a config folder via the command line, and the first time you run it, it populates the folder with a default config file where you can set ports and stuff.

---

