---
title: "Hanging on access to us.archive.ubuntu.com"
date: 2006-07-22
forum: The Cafe
---

### Post by K.Mandla on 2006-07-22
I'm trying to do an update/upgrade, but us.archive.ubuntu.com (146.137.96.7) seems to be hanging. I can ping it, but apt-get is hanging when it tries to access it. 

Does anyone else have that problem (if you're using the U.S. repositories)?

Is there a site that tracks Ubuntu's repositories and their status?

Sorry if these are dumb questions.

---

### Post by scxtt on 2006-07-22
i'm experiencing that problem too ... we'll probably just have to wait it out - it's never done that before ...

```
:> sudo apt-get update
Get:1 http://security.ubuntu.com dapper-security Release.gpg [189B]
Get:2 http://security.ubuntu.com dapper-security Release [30.9kB]
Get:3 http://xgl.compiz.info dapper Release.gpg [191B]
Get:4 http://xgl.compiz.info dapper Release [2147B]
Ign http://packages.freecontrib.org dapper Release.gpg
Ign http://xgl.compiz.info dapper Release
Ign http://packages.freecontrib.org dapper Release
Ign http://xgl.compiz.info dapper/main Packages
Ign http://packages.freecontrib.org dapper/free Packages
Get:5 http://security.ubuntu.com dapper-security/main Packages [39.4kB]
Get:6 http://xgl.compiz.info dapper/main Packages [12.7kB]
Ign http://packages.freecontrib.org dapper/non-free Packages
Hit http://packages.freecontrib.org dapper/free Packages
Get:7 http://security.ubuntu.com dapper-security/restricted Packages [4275B]
Hit http://packages.freecontrib.org dapper/non-free Packages
Get:8 http://security.ubuntu.com dapper-security/main Sources [9552B]
Get:9 http://security.ubuntu.com dapper-security/restricted Sources [974B]
Get:10 http://security.ubuntu.com dapper-security/universe Packages [6951B]
Get:11 http://security.ubuntu.com dapper-security/universe Sources [902B]
Get:12 http://archive.canonical.com dapper-commercial Release.gpg [191B]
Hit http://archive.canonical.com dapper-commercial Release
Hit http://archive.canonical.com dapper-commercial/main Packages
99% [Connecting to us.archive.ubuntu.com (146.137.96.15)]
```

---

### Post by K.Mandla on 2006-07-22
Okay, at least it's not just me. Thanks; I can wait. ;)

---

### Post by Iandefor on 2006-07-22
I had the same problem when I tried to do a sudo aptitude update this morning.

---

### Post by Johnsie on 2006-07-22
you could just change us to uk in the meantime.

uk.archive.ubuntu.com

---

### Post by NeoChaosX on 2006-07-22
Or just remove the 'us.' and just use the archive.ubuntu.com servers, which get updater sooner than the local mirrors (at least IME).

---

### Post by OneSeventeen on 2006-07-22
After removing all references to us.archive.ubuntu.com I run sudo apt-get update and it hangs on the second to last server... us.archive.ubuntu.com... even though it isn't in sources.list

Any ideas?

```

deb http://archive.ubuntu.com/ubuntu/ dapper main restricted
deb-src http://archive.ubuntu.com/ubuntu/ dapper main restricted
deb http://archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted

```

---

### Post by teet on 2006-07-22
I've had problems with the US servers in the past also.  I just removed the "us." from everything and it seemed to fix the problem.

For example change
```

deb http://us.archive.ubuntu.com/ubuntu dapper main

```
to
```

deb http://archive.ubuntu.com/ubuntu dapper main

```
-teet

---

### Post by K.Mandla on 2006-07-22
Just a note: I'm putting Ubuntu on a machine for a friend at work (dual boot with Win98 on an ancient Cyrix desktop :p ) and got updates by changing the us to uk. Thanks, UKers!

---

### Post by Skia_42 on 2006-07-23
I just noticed that when i was installing some stuff with Automatix, it's odd...hopefully not forever.

---

