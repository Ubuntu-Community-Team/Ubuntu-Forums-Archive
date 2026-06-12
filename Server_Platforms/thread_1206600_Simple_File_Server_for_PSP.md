---
title: "Simple File Server for PSP"
date: 2009-07-07
forum: Server Platforms
---

### Post by Tactical Fart on 2009-07-07
I'm just looking for a simple web-based file server. Something like [this]("http://www.rejetto.com/hfs/"). I don't need to used a web interface to upload, nor do I plan on doing so. I only need a server that will allow me to browse my files and download them. (PSP does not like mediatomb. I've already tried.)I also mostly administrate this machine through ssh and ftp with some x forwarding (It's not headless though). Any ideas?

---

### Post by damis648 on 2009-07-07
You could just use apache and have it display the index of a folder?

---

### Post by Tactical Fart on 2009-07-11
Ever since the last post, I've been playing with apache2. I keep getting 403 Forbidden when I try to change stuff. I'm trying to serve a folder on another partition. I managed to get it to show the files in a directory once (forgot how) but got 403 when I tried to download something or go to another directory. Any Ideas?

Also how do I make apache demand a password when I go to it with my browser? I'm sure I don't want any "letters" if you know what I mean.

---

