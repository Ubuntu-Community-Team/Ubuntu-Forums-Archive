---
title: "Lightweight cli torrent client"
date: 2014-04-13
forum: Server Platforms
---

### Post by sandyd on 2014-04-13
As release date is coming up, I want to use a few servers that I have to help seed the ISOs. These particular servers are used for other purposes normally, so I want to be able to cleanly remove the torrent client after seeding ISOs.

I normally use rutorrent on my personal server to seed Ubuntu, but there are too many dependencies

Any reccomendations?

---

### Post by dudumomo on 2014-04-14
If rtorrent is not good for you, I suggest to use aria2. It's my favorite download manager type in command line and can also do torrent with seed feature.

Or may be you could use the old ctorrent too.
At least, transmission-cli should not be too big neither and easy to use.

Hope it helps

---

### Post by Lars Noodén on 2014-04-14
[btpd](https://github.com/btpd/btpd/wiki) is very lightweight and with few dependencies.  It is in the repositories.  It takes a little reading to set up, but then once set up needs no changes.

---

### Post by SeijiSensei on 2014-04-14
I like [ctorrent](http://www.rahul.net/dholmes/ctorrent/) for a simple command-line client.  It's pretty simple to set up.  You can install ctorrent from the repositories ("sudo apt-get install ctorrent").

---

### Post by sandyd on 2014-04-15
> **SeijiSensei said:**
> I like [ctorrent](http://www.rahul.net/dholmes/ctorrent/) for a simple command-line client.  It's pretty simple to set up.  You can install ctorrent from the repositories ("sudo apt-get install ctorrent").

exactly what I was looking for - no additional deps installed and an easy-to-use command line.


Thanks.

---

