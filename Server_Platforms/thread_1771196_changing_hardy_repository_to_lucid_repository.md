---
title: "changing hardy repository to lucid repository"
date: 2011-05-30
forum: Server Platforms
---

### Post by Naqib on 2011-05-30
I am newbie in Linux,
I have got ubuntu repository: [http://tamtam.pischiello.echosolution.it/echolinux/](http://tamtam.pischiello.echosolution.it/echolinux/) which is for hardy box. It has got non-free part which are some personal packets(web application,php code, javascript etc). Now I want to convert it to lucid with the same non-free packages where the lucid boxes can get there update from. To achieve this goal I have gone through following methods:

First: 
---------------------------------------------------------------------------------------------------------------
1. I downloaded the source of the similar packages and rebuild it as(under lucid source.list):
   -apt-get source packagename 
   -apt-get build-dep packagename
   -debuild -us -uc
2. I generated the repository using reprepro
3. I added the link to the source.list of box and on apt-get update I got error:

var/cache/apt/archive/libgtk2.0-dev_2.20.10ubuntu.deb
var/cache/apt/archive/libhtml-parser-perl_3.64.deb
---------------------------------------------------------------------------------------------------------------

Second:
---------------------------------------------------------------------------------------------------------------
1. I copied the pool/main from lucid and integrated my non-free package.
2. Generated the Packages.gz and Sources.gz:

    -dpkg-scanpackages
    -dpkg-scansources.

I got this error:
Hash Sum mismatch.
---------------------------------------------------------------------------------------------------------------

I would be so thankful if one tell me how to change my repository to lucid. Because, I have been working in this since last 2 months. please help me because, I think I started linux first time from difficult part, because, I have been trying all means to solve my problem(Internet search, forums and etc)


Thanks a lot:)

---

### Post by Lars Noodén on 2011-05-30
> **Naqib said:**
> 

I would be so thankful if one tell me how to change my repository to lucid.

Typically, the contents of the /etc/apt/sources.list looks like this:

```

deb http://us.archive.ubuntu.com/ubuntu/ lucid main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid main restricted

deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates main restricted

```

Of course change it from us.archive.ubuntu.com to the mirror closest you.

Then update and load the new system:
```

sudo apt-get update
sudo apt-get dist-upgrade

```

---

