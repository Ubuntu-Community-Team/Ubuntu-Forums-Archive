---
title: "[SOLVED] Is it normal to have so many 'Ign' lines when updating?"
date: 2007-10-26
forum: Repositories &amp; Backports
---

### Post by DasCrushinator on 2007-10-26
I keep getting a bunch of Ign errors when running sudo apt-get update
```
Get:1 http://security.ubuntu.com gutsy-security Release.gpg [191B]
Ign http://security.ubuntu.com gutsy-security/main Translation-en_US
Get:2 http://archive.ubuntu.com gutsy Release.gpg [191B]
Get:3 http://us.archive.ubuntu.com gutsy Release.gpg [191B]
Ign http://us.archive.ubuntu.com gutsy/main Translation-en_US
Ign http://security.ubuntu.com gutsy-security/restricted Translation-en_US
Ign http://security.ubuntu.com gutsy-security/universe Translation-en_US
Ign http://security.ubuntu.com gutsy-security/multiverse Translation-en_US
Hit http://archive.ubuntu.com gutsy Release
Ign http://us.archive.ubuntu.com gutsy/restricted Translation-en_US
Ign http://us.archive.ubuntu.com gutsy/universe Translation-en_US
Ign http://us.archive.ubuntu.com gutsy/multiverse Translation-en_US
Get:4 http://us.archive.ubuntu.com gutsy-updates Release.gpg [191B]
Ign http://us.archive.ubuntu.com gutsy-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com gutsy-updates/restricted Translation-en_US
Hit http://security.ubuntu.com gutsy-security Release
Ign http://us.archive.ubuntu.com gutsy-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com gutsy-updates/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com gutsy Release
Hit http://archive.ubuntu.com gutsy/main Sources
Hit http://us.archive.ubuntu.com gutsy-updates Release
Hit http://security.ubuntu.com gutsy-security/main Packages
Hit http://archive.ubuntu.com gutsy/restricted Sources
Hit http://us.archive.ubuntu.com gutsy/main Packages
Hit http://us.archive.ubuntu.com gutsy/restricted Packages
Hit http://us.archive.ubuntu.com gutsy/restricted Sources
Hit http://security.ubuntu.com gutsy-security/restricted Packages
Hit http://security.ubuntu.com gutsy-security/restricted Sources
Hit http://security.ubuntu.com gutsy-security/main Sources
Hit http://us.archive.ubuntu.com gutsy/main Sources
Hit http://us.archive.ubuntu.com gutsy/multiverse Sources
Hit http://us.archive.ubuntu.com gutsy/universe Sources
Hit http://us.archive.ubuntu.com gutsy/universe Packages
Hit http://us.archive.ubuntu.com gutsy/multiverse Packages
Hit http://security.ubuntu.com gutsy-security/multiverse Sources
Hit http://security.ubuntu.com gutsy-security/universe Sources
Hit http://security.ubuntu.com gutsy-security/universe Packages
Hit http://security.ubuntu.com gutsy-security/multiverse Packages
Hit http://us.archive.ubuntu.com gutsy-updates/main Packages
Hit http://us.archive.ubuntu.com gutsy-updates/restricted Packages
Hit http://us.archive.ubuntu.com gutsy-updates/restricted Sources
Hit http://us.archive.ubuntu.com gutsy-updates/main Sources
Hit http://us.archive.ubuntu.com gutsy-updates/multiverse Sources
Hit http://us.archive.ubuntu.com gutsy-updates/universe Sources
Hit http://us.archive.ubuntu.com gutsy-updates/universe Packages
Hit http://us.archive.ubuntu.com gutsy-updates/multiverse Packages
Get:5 http://packages.medibuntu.org gutsy Release.gpg [189B]
Ign http://packages.medibuntu.org gutsy/free Translation-en_US
Ign http://packages.medibuntu.org gutsy/non-free Translation-en_US
Hit http://packages.medibuntu.org gutsy Release
Ign http://packages.medibuntu.org gutsy/free Packages
Ign http://packages.medibuntu.org gutsy/non-free Packages
Hit http://packages.medibuntu.org gutsy/free Packages
Hit http://packages.medibuntu.org gutsy/non-free Packages
Fetched 5B in 7s (1B/s)
Reading package lists...
```

Looked at the other threads about this issue, but non of them seem to offer a solution.

---

### Post by 67GTA on 2007-10-30
That just means that it is ignoring the repo because nothing has changed, or been updated since the last "apt-get update". It doesn't have to re-download it again.

---

### Post by kostkon on 2007-10-30
I want just to confirm that *67GTA* is right. So, don't worry about these ignore messages.

---

### Post by DasCrushinator on 2007-10-30
> **kostkon said:**
> I want just to confirm that *67GTA* is right. So, don't worry about these ignore messages.

Really?  I hope you are right, but I thought that was what 'Hit' meant.  I thought 'Hit' meant nothing has changed, 'Get' meant something had changed and it was able to download, and I'm not sure what to think of ignore.

SO what does 'Hit' mean if 'Ign' means nothing has changed?

---

### Post by kostkon on 2007-10-30
> **DasCrushinator said:**
> Really?  I hope you are right, but I thought that was what 'Hit' meant.  I thought 'Hit' meant nothing has changed, 'Get' meant something had changed and it was able to download, and I'm not sure what to think of ignore.

SO what does 'Hit' mean if 'Ign' means nothing has changed?

NO! It's not like that. 

*Hit* means that something has changed to a repository so a new version of its list of packages must be downloaded.

*Ign* means that nothing has changed so not need to download something.

 If you had a problem you would get messages with *Err* in the *apt-get update* output.

---

