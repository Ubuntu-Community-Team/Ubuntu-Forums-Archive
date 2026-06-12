---
title: "libapache2-mod-security in feisty"
date: 2007-07-30
forum: Server Platforms
---

### Post by rockdon on 2007-07-30
I went to install mod_security in apache2 last night, and found that for apache2.2, feisty does not have a libapache2-mod-security package in apt.

Anyone know what happened to this package or why its not in feisty?

FYI: I have tried opening repos to universe and multiverse as well.

---

### Post by punx45 on 2007-07-30
I was looking for this the other day too.

---

### Post by AnRa on 2007-07-30
You should try [libapache2-mod-ifier](http://packages.ubuntu.com/feisty/web/libapache2-mod-ifier), it is intended to be an extremely lightweight replacement for mod_security.

---

### Post by rockdon on 2007-07-30
I just read through the intro on that package, while that seems like a nice package, i'm not looking for a "non-feature-rich" version of mod_security, i want mod_security. 

I don't mind installing it by hand that much, but I seek to understand why it was taken OUT of the repos for feisty.

---

### Post by punx45 on 2007-07-31
according to the description for mod-ifier, mod-security wont be included in debain etch.   is that why it also is not appearing in the feisty repos?  or no one got around to building it yet maybe?

---

### Post by lionelp on 2007-08-01
libapache2-mod-security was removed from Debian for licence issues. When a package is removed from Debian, Ubuntu usually removed it also (removing a package is for a good reason).
That's what happen to libapache2-mod-security.

---

### Post by fmouse on 2008-01-28
I corresponded today with Alberto Gonzalez Iniesta, the package maintainer for the former Debian libapache2-mod-security package and it seems that he maintains his own archive of up-to-date mod-security packages at [http://etc.inittab.org/~agi/debian/libapache-mod-security2/]("http://etc.inittab.org/~agi/debian/libapache-mod-security2/").  This is good news for Debianistas but not really so useful for Ubuntu users since Ubuntu Dapper Drake (LTS server) which my client is using has incompatible (older) versions of both libc6 and apache and Alberto's mod-security package won't install.

I was wondering if anyone on this forum knows of a similar project for maintaining and making available apache mod-security packages which are compatible with various Ubuntu server distribution versions.

Alberto confirmed the licensing issue as far as Debian is concerned, and I'm not surprised that Ubuntu will follow suit.  mod-security 1.8.7 is so old that Breach Security no longer distributes it or supports it, and the current core rules set won't work with it.  It might as well be dropped from Ubuntu server distrubitions altogether if it's not going to be kept up.

---

