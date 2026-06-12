---
title: "Ignored Repositories"
date: 2007-08-04
forum: Repositories &amp; Backports
---

### Post by synd7 on 2007-08-04
I posted this in the beginners area as i anticipated a simple/obvious answer, but it seems thats not the case.

When i update (using aptitude) my repositories i get a bunch that are ignored. The ones that are ignored change each time i update.

Whats causing this? I'm not even sure that it presents a problem but it bugs me :)

This has happened for a long time (edgy, feisty and now gutsy) but for some reason it didn't bother me back then :)

Heres the output of a **sudo aptitude update**
```
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Alpha i386 (20070718.1) gutsy/main Translation-en_AU
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Alpha i386 (20070718.1) gutsy/restricted Translation-en_AU
Get:1 http://security.ubuntu.com gutsy-security Release.gpg [191B
Ign http://security.ubuntu.com gutsy-security/main Translation-en_AU
Ign http://security.ubuntu.com gutsy-security/restricted Translation-en_AU
Ign http://security.ubuntu.com gutsy-security/universe Translation-en_AU
Ign http://security.ubuntu.com gutsy-security/multiverse Translation-en_AU
Hit http://security.ubuntu.com gutsy-security Release       
Hit http://security.ubuntu.com gutsy-security/main Packages 
Hit http://security.ubuntu.com gutsy-security/restricted Packages
Hit http://security.ubuntu.com gutsy-security/main Sources  
Hit http://security.ubuntu.com gutsy-security/restricted Sources
Hit http://security.ubuntu.com gutsy-security/universe Packages
Hit http://security.ubuntu.com gutsy-security/universe Sources
Hit http://security.ubuntu.com gutsy-security/multiverse Packages
Hit http://security.ubuntu.com gutsy-security/multiverse Sources
Get:2 http://archive.ubuntu.com gutsy Release.gpg [191B]
Ign http://archive.ubuntu.com gutsy/main Translation-en_AU
Ign http://archive.ubuntu.com gutsy/restricted Translation-en_AU
Ign http://archive.ubuntu.com gutsy/universe Translation-en_AU
Ign http://archive.ubuntu.com gutsy/multiverse Translation-en_AU
Get:3 http://archive.ubuntu.com gutsy-updates Release.gpg [191B]
Ign http://archive.ubuntu.com gutsy-updates/restricted Translation-en_AU
Ign http://archive.ubuntu.com gutsy-updates/main Translation-en_AU
Ign http://archive.ubuntu.com gutsy-updates/multiverse Translation-en_AU
Ign http://archive.ubuntu.com gutsy-updates/universe Translation-en_AU
Get:4 http://archive.ubuntu.com gutsy Release [65.9kB]
Hit http://archive.ubuntu.com gutsy-updates Release
Get:5 http://archive.ubuntu.com gutsy/main Packages [1080kB]
Get:6 http://archive.ubuntu.com gutsy/restricted Packages [7243B]
Get:7 http://archive.ubuntu.com gutsy/main Sources [302kB]
Get:8 http://archive.ubuntu.com gutsy/restricted Sources [1996B]
Get:9 http://archive.ubuntu.com gutsy/universe Packages [3987kB]
Get:10 http://archive.ubuntu.com gutsy/universe Sources [1219kB]
Get:11 http://archive.ubuntu.com gutsy/multiverse Packages [157kB]
Get:12 http://archive.ubuntu.com gutsy/multiverse Sources [56.1kB]
Hit http://archive.ubuntu.com gutsy-updates/restricted Packages
Hit http://archive.ubuntu.com gutsy-updates/main Packages
Hit http://archive.ubuntu.com gutsy-updates/multiverse Packages
Hit http://archive.ubuntu.com gutsy-updates/universe Packages
Fetched 6876kB in 1m3s (109kB/s)
Reading package lists... Done

```

---

### Post by ChrisNiemy on 2007-08-05
What seems to get ignored are "only" translations of the package descriptions. I can't tell how it works, but I have the same here with de_DE language packs. Though I have some descriptions in German. I have this error messages also with apt-get/synaptic. It's not because of using aptitude.

So the error message is confusing, but things seem to work correctly.

Anyone got an idea?

---

