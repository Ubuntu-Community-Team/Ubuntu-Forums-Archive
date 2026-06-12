---
title: "setting up a local apt repository/mirror?"
date: 2008-10-29
forum: Security
---

### Post by AntEater on 2008-10-29
I run a couple of computer labs with the workstations running Ubuntu 8.04.  I would like to set up an apt repository on a local server that mirrors the official and unofficial repositories.  I could then point my client machines at the local server for their upgrades.  I'm trying to avoid having dozens of machines going out across the internet to hit the official servers for their updates concurrently.  Seems like a waste of our bandwidth and Ubuntu's to do things this way.  I've searched the forums a bit but haven't found any information on setting something like this up.  Perhaps I missed something.  I've created a similar setup with other distributions but never with a Debian based Linux.  Anyways, I was hoping that someone could point me in the right direction with this.

---

### Post by forger on 2008-10-29
Key-command:
```
apt-cache search apt.*mirror
```

take your pick :)
[apt-proxy]("apt://apt-proxy")
> Description: Debian archive proxy and partial mirror builder
 apt-proxy automatically builds a Debian HTTP mirror based
 on requests which pass through the proxy.  It's great for
 multiple Debian machines on the same network with a slower
 internet link.
 .
 The archive is automatically kept up to date using http,
 ftp or rsync.  Cache cleaning of unused and old versions
 is configurable.  You can also import the contents of
 your apt cache into the archive using apt-proxy-import.
 .
 For more information, see the apt-proxy homepage at
 [http://apt-proxy.sourceforge.net](http://apt-proxy.sourceforge.net)
 .
 The suggested packages are needed for the following
 features: rsync for rsyncd backends, and
 dpkg-dev for apt-proxy-import.

[apt-mirror]("apt://apt-mirror")
> Description: APT sources mirroring tool
 A small and efficient tool that lets you mirror a part of or
 the whole Debian GNU/Linux distribution or any other apt sources.
 .
 Main features:
  * It uses a config similar to apts <sources.list>
  * It's fully pool comply
  * It supports multithreaded downloading
  * It supports multiple architectures at the same time
  * It can automatically remove unneeded files
  * It works well on overloaded channel to internet
  * It never produces an inconsistent mirror including while mirroring
  * It works on all POSIX complied systems with perl and wget
 .
  Homepage: [http://apt-mirror.sourceforge.net/](http://apt-mirror.sourceforge.net/)


there is a wealth of "how to" guides for them if you [search at Google]("http://www.google.com/search?hl=en&q="how+to"+apt-mirror") or Ubuntuforums :)

---

