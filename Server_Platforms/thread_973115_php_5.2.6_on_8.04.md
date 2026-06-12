---
title: "php 5.2.6 on 8.04?"
date: 2008-11-06
forum: Server Platforms
---

### Post by maple03 on 2008-11-06
My corporate security scanners keep saying that my Ubuntu servers have vulnerability in php 5.2.4. And after months of waiting there is still no progress on updating to php 5.2.6. I've tried to google and searching forums but no solution except adding dotdeb.org repository and compiling from the source code. 

Since 8.04 is an LTS release, I do not want to upgrade to Interpid. So what I need to do to make my php be up-to-date?

---

### Post by CP1256 on 2008-11-06
[DotDeb.org]("http://www.dotdeb.org/") is probably the only way.

You can also add the repositories of Ubuntu 8.10, then you'll also get Apache 2.2.9.

Otherwise I see no other way then building it from source.

---

### Post by maple03 on 2008-11-06
What are the disadvantages of adding 8.10 repos and building php from the source?

---

### Post by CP1256 on 2008-11-06
I use one Ubuntu 8.10 repo for my 8.04 server, one disadvantage is that they won't add new releases from PHP, so I probably have to use DotDeb in the future. 

Building PHP from scratch could be hard, but I've never done it so I can't say anything about it.

---

### Post by maple03 on 2008-11-06
And can php be built using deb-src? I am not quite sure how to compile applications in Ubuntu. Though it was very easy in FreeBSD - make install clean, and that's all ;)

---

### Post by CP1256 on 2008-11-07
Compiling from source in Ubuntu is done like this:

Extract source, ./configure, make and sudo make install. 

The problem is that you need to install all dependencies yourself, which is done automaticly when using apt.

> And can php be built using deb-src?
That's something I don't know.

---

### Post by tomchuk on 2008-11-07
First, ./configure; make; make install is probably not what you want to be doing. It leads to issues in dpkg when you're attempting to install a package that depends on php and generally makes things harder to upgrade later on.

Second, The php 5.2.4 in 8.04 has all security fixes from later versions applied. In Ubuntu, it is very rare that package versions will be updated in the release, rather essential changes are backported to the existing version. If you look at the [CHANGELOG](http://changelogs.ubuntu.com/changelogs/pool/main/p/php5/php5_5.2.4-2ubuntu5.3/changelog) for php5 in 8.04, you can see that the latest changes (from July 18) are the backporting of the security-related fixes from 5.2.6. As long as you have the security repository enabled (you should unless you specifically disabled it) and are updating your system regularly, you should be in good shape. The security scanner is just a bit dumb, only looking for php version returned in the headers of the web server. If you edit your /etc/php5/*/php.ini and change expose_php to "Off" it will remove the php signature from the server headers and fool the scanner into thinking that everything is OK.

Third, If you really want to upgrade to 5.2.6, you should add the following lines to your /etc/apt/sources.list:

```

deb-src http://archive.ubuntu.com/ubuntu/ intrepid main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu intrepid-security main restricted universe multiverse
```

Then run:
```

sudo apt-get update
sudo apt-get build-dep php5
apt-get --build source php5

```

Assuming there have been no drastic dependency changes, you'll be left with a bunch of php*.deb packages that you can install with dpkg -i. Please note though, that updating your system with apt will not upgrade your php packages. You will be responsible for tracking changes in the source php5 package from Intrepid, and re-building php whenever they change to stay on top of security fixes.

Generally, I'd advise to just stick with the Hardy packages, after all, that's the whole point of an LTS release.

---

### Post by maple03 on 2008-11-11
Thank you very much for your reply. I see now that using 8.04 LTS is the best option.

---

