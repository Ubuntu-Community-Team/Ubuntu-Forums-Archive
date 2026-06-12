---
title: "Backports Repository Doesn't Work"
date: 2006-07-31
forum: Ubuntu Backports
---

### Post by graphic23 on 2006-07-31
Hi All, 
           I have the following in my sources.list:

```


deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse


```

Then, I've run apt-get update several times. But there is beagle-0.2.7 in backports and i never get an option to upgrade to it. I've tried:

```

apt-get -t dapper-backports beagle

```

I've tried messing with /etc/apt/preferences

but nothing works. 

Any help on how to get this to work ? Thanks!

---

### Post by mmcmonster on 2006-07-31
This is what I have in my /etc/apt/sources.list:
```

deb http://archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

```


That being said, I don't think there is anything in Dapper backports yet.  The [Ubuntu packages site]("http://packages.ubuntu.com/") doesn't even mention Dapper backports yet, which is a bad sign. ;-(

---

### Post by graphic23 on 2006-07-31
> **mmcmonster said:**
> This is what I have in my /etc/apt/sources.list:
```

deb http://archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

```


That being said, I don't think there is anything in Dapper backports yet.  The [Ubuntu packages site]("http://packages.ubuntu.com/") doesn't even mention Dapper backports yet, which is a bad sign. ;-(


Ah ok. Because I checked in the dapper-backports/pool/ and there were many things there -so I was a bit surprised by why i was not getting anything.

---

### Post by Metacarpal on 2006-07-31
> **mmcmonster said:**
> That being said, I don't think there is anything in Dapper backports yet.  The [Ubuntu packages site]("http://packages.ubuntu.com/") doesn't even mention Dapper backports yet, which is a bad sign. ;-(

That's largely because of the amount of changes to library dependancies for the new packages.  Backporting from Edgy development is a bit of a sticky problem, because so many of the base packages and lib-whatever files have changed to new versions.  Trying to upgrade the new versions, when most of Dapper is expecting the ones you already have, could seriously b0rk your installation.

To avoid changes in dependancies causing a complete failure of your desktop, backports are being held.  So if you want the new version of a package, you'll either have to compile from source, or wait for Ubuntu 6.10 to be released.

---

### Post by mmcmonster on 2006-08-01
> **Metacarpal said:**
> That's largely because of the amount of changes to library dependancies for the new packages.  Backporting from Edgy development is a bit of a sticky problem, because so many of the base packages and lib-whatever files have changed to new versions.  Trying to upgrade the new versions, when most of Dapper is expecting the ones you already have, could seriously b0rk your installation.

To avoid changes in dependancies causing a complete failure of your desktop, backports are being held.  So if you want the new version of a package, you'll either have to compile from source, or wait for Ubuntu 6.10 to be released.

This confuses me a bit.  For something to get into backports, do they just take the .deb from the edgy repository and copy it to dapper-backports?  I was under the impression that a custom .deb was built from the source.  If so, anything that an individual can build on dapper should be capable of being in dapper-backports, right?

---

### Post by MadMan2k on 2006-08-01
> **mmcmonster said:**
> This confuses me a bit.  For something to get into backports, do they just take the .deb from the edgy repository and copy it to dapper-backports?  I was under the impression that a custom .deb was built from the source.  If so, anything that an individual can build on dapper should be capable of being in dapper-backports, right?
they take the edgy deb and reabuild it on dapper so it uses the older libraries.
so you are basically right; everything which you can compile on dapper can also be compiled using the edgy deb source.

---

### Post by infoseeker on 2006-08-01
I'm in South Africa and also having normal update problems.  Updating today gave me 33 errors.

Example (3 of 33 errors)> Err [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) dapper-updates/universe librss1 4:3.5.2-0ubuntu6.1
  404 Not Found
Err [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) dapper-updates/universe dcoprss 4:3.5.2-0ubuntu6.1
  404 Not Found
Err [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) dapper-updates/main libgnomeui-0 2.14.1-0ubuntu3
  404 Not Found

Is it my sources list settings or is there something I don't know of ?

Some of my entries have somehow been disabled (hashed).

>     deb [http://za.archive.ubuntu.com/ubuntu](http://za.archive.ubuntu.com/ubuntu) dapper main restricted universe
# multiverse (removed from above)

deb-src [http://za.archive.ubuntu.com/ubuntu](http://za.archive.ubuntu.com/ubuntu) dapper main restricted universe
# multiverse (removed from above)

    deb [http://za.archive.ubuntu.com/ubuntu](http://za.archive.ubuntu.com/ubuntu) dapper-updates main restricted universe
deb-src [http://za.archive.ubuntu.com/ubuntu](http://za.archive.ubuntu.com/ubuntu) dapper-updates main restricted universe


# deb [http://za.archive.ubuntu.com/ubuntu](http://za.archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse


Thanks

---

### Post by skymt on 2006-08-02
Your sources.list looks fine. I would guess the packages haven't all been copied to your server yet. You could get them from another server, like the main archive.ubuntu.com, or you could wait a couple hours.

---

### Post by skymt on 2006-08-02
Your sources.list looks fine. I would guess the packages haven't all been copied to your server yet. You could get them from another server, like the main archive.ubuntu.com, or you could just wait a couple hours.

---

