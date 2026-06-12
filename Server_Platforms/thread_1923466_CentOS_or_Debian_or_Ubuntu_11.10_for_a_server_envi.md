---
title: "CentOS or Debian or Ubuntu 11.10 for a server environment"
date: 2012-02-10
forum: Server Platforms
---

### Post by Rukiri on 2012-02-10
Before anything get's technical here's what I plan on using.

node.js 0.6.10
Ruby on Rails
PHPMyadmin (just use to it)
MySQL
PostgreSQL
Lighttpd

I originally had gentoo installed but because it has constant updates and they do take for ever to compile and the recent update broke etc-update for updating config files..  Arch is in the same position and it's an OS you can update pacman(since there's no go gui to gather data and only one terminal window is counted..)

Of course I know how to easily fix those issues in a running box but I don't recommend gentoo or arch for production boxes.

Now brings me to the actual question, what do you guys thing would be better for a server environment?  CentOS 6, Debian 6, Ubuntu 11.10.

I have experience with all of them, but never ran any of them in a server environment.

---

### Post by Habitual on 2012-02-10
Hands down CentOS

---

### Post by Mia1990 on 2012-02-11
My vote is for Ubuntu server 11.10 is working great for me but i think I would wait till April for 12.04 to come out it will be a LTS release and will be much more stable.

---

### Post by spynappels on 2012-02-11
If you go for Ubuntu, go for a LTS release like MIA said, 10.04 is running great on my production Ubuntu boxes, but I won't use 12.04 until the end of 2012 at the earliest.

Whether CentOS or Debian or Ubuntu, only you can decide, based on your needs and experience. Here is what I've found:

Debian - rock stable, older packages some some compiling from source required for more up to date packages.

Ubuntu - I'm used to it, reasonably up to date packages.

CentOS - Rock solid, good if you are used to RHEL. Slightly different file structure etc.

You decide what features and stability you need and make your choice accordingly.

Hope that was a little helpful.

---

### Post by savanna on 2012-02-11
What do you want out of your server? Bleeding edge tools and libraries, or stability? Ubuntu for the former and Debian for the latter.

Are you planning on working it IT? If so, CentOS, as you'll learn how to work with RHEL (RHEL is used commercially by a lot of companies as it gives "commercial support").

Personally I prefer either Ubuntu or Debian, as I find the package management is better than any of the rpm based distros (CentOS, RHEL, etc).

---

