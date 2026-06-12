---
title: "Install SQLite from source"
date: 2015-11-08
forum: Tutorials
---

### Post by brucehohl on 2015-11-08
The quick steps follow.
For more detailed notes, installing in /opt and useful links see attachment.

[LIST=1]
[*]Download
$ wget [http://sqlite.org/2015/sqlite-autoconf-3090200.tar.gz](http://sqlite.org/2015/sqlite-autoconf-3090200.tar.gz) 
[but check sqlite.org for most current version]
.
[*]Move file to /usr/local/src/
.
[*]Extract: 
$ sudo tar -xvf sqlite-autoconf-3090200.tar.gz
.
[*]Install packages needed for compile-make-install:
$ sudo aptitude install build-essential
.
[*]Install packages needed for readline integration:
$ sudo aptitude install libreadline-dev libreadline6-dev libreadline6-dbg
.
[*]Configure-Make-Install
$ cd sqlite-autoconf-3090200
$ CFLAGS="-Os" ./configure --enable-readline 
$ make 
$ sudo make install
[/LIST]

---

