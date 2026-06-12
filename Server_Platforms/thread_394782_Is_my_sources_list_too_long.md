---
title: "Is my sources list too long"
date: 2007-03-27
forum: Server Platforms
---

### Post by davidshere on 2007-03-27
This is my sources list.  I've read here that having one that includes "too many" sources can be a security risk.  I know I've added/enabled a few of these in the past to get things working (mostly for upgrading from 6.06 to 6.10) and I'm not sure which ones are ok to remove, or what is available from each.

```
admin@raptor:~$ sudo apt-get update
Ign cdrom://Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025) edgy/main Translation-en_US
Ign cdrom://Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025) edgy/restricted Translation-en_US
Get:1 http://us.archive.ubuntu.com edgy Release.gpg [191B]                                       
Ign http://us.archive.ubuntu.com edgy/main Translation-en_US                 
Get:2 http://security.ubuntu.com edgy-security Release.gpg [191B]
Ign http://security.ubuntu.com edgy-security/main Translation-en_US
Ign http://security.ubuntu.com edgy-security/restricted Translation-en_US
Ign http://us.archive.ubuntu.com edgy/restricted Translation-en_US
Ign http://us.archive.ubuntu.com edgy/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com edgy/universe Translation-en_US
Get:3 http://us.archive.ubuntu.com edgy-updates Release.gpg [191B]
Ign http://us.archive.ubuntu.com edgy-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com edgy-updates/restricted Translation-en_US
Ign http://security.ubuntu.com edgy-security/multiverse Translation-en_US
Ign http://security.ubuntu.com edgy-security/universe Translation-en_US
Hit http://security.ubuntu.com edgy-security Release
Ign http://us.archive.ubuntu.com edgy-updates/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com edgy-updates/universe Translation-en_US
Hit http://us.archive.ubuntu.com edgy Release
Hit http://us.archive.ubuntu.com edgy-updates Release               
Hit http://security.ubuntu.com edgy-security/main Packages          
Hit http://us.archive.ubuntu.com edgy/main Packages
Hit http://us.archive.ubuntu.com edgy/restricted Packages
Hit http://us.archive.ubuntu.com edgy/main Sources
Hit http://security.ubuntu.com edgy-security/restricted Packages
Hit http://security.ubuntu.com edgy-security/main Sources
Hit http://us.archive.ubuntu.com edgy/restricted Sources
Hit http://us.archive.ubuntu.com edgy/multiverse Packages
Hit http://us.archive.ubuntu.com edgy/universe Packages
Hit http://us.archive.ubuntu.com edgy-updates/main Packages
Hit http://us.archive.ubuntu.com edgy-updates/restricted Packages
Hit http://us.archive.ubuntu.com edgy-updates/main Sources
Hit http://us.archive.ubuntu.com edgy-updates/restricted Sources
Hit http://us.archive.ubuntu.com edgy-updates/multiverse Packages
Hit http://us.archive.ubuntu.com edgy-updates/universe Packages
Hit http://security.ubuntu.com edgy-security/restricted Sources
Hit http://security.ubuntu.com edgy-security/multiverse Packages
Hit http://security.ubuntu.com edgy-security/universe Packages
Fetched 3B in 1s (2B/s)  
Reading package lists... Done
admin@raptor:~$ 
```

---

### Post by Aircooledmadness on 2007-03-27
That sources.list isnt too long at all.

I wouldn't worry about security either,  as they are all stock Ubuntu sources.  If you had some crazy 3rd party repos listed...then you might question security.

---

