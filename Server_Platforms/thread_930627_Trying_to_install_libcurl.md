---
title: "Trying to install libcurl"
date: 2008-09-26
forum: Server Platforms
---

### Post by dewman0012 on 2008-09-26
I am using apt-get to install libcurl on our ubuntu server. The libcurl installs without an issues, however, when doing the install for php5-curl, I get the following error:

```
Err http://us.archive.ubuntu.com gutsy-updates/main php5-curl 5.2.3-1ubuntu6.4
  Could not resolve 'us.archive.ubuntu.com'
Err http://security.ubuntu.com gutsy-security/main php5-curl 5.2.3-1ubuntu6.4
  Could not resolve 'security.ubuntu.com'
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/p/php5/php5-curl_5.2.3-1ubuntu6.4_i386.deb  Could not resolve 'security.ubuntu.com'
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
```

So I try and update, and I get a huge list of errors:

```
Ign cdrom://Ubuntu-Server 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_US
Ign cdrom://Ubuntu-Server 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_US
Err http://security.ubuntu.com gutsy-security Release.gpg
  Could not resolve 'security.ubuntu.com'
Err http://us.archive.ubuntu.com gutsy Release.gpg
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com gutsy/main Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err http://security.ubuntu.com gutsy-security/main Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err http://us.archive.ubuntu.com gutsy/restricted Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err http://security.ubuntu.com gutsy-security/restricted Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err http://us.archive.ubuntu.com gutsy/universe Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err http://security.ubuntu.com gutsy-security/universe Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err http://us.archive.ubuntu.com gutsy/multiverse Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err http://security.ubuntu.com gutsy-security/multiverse Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err http://us.archive.ubuntu.com gutsy-updates Release.gpg
  Could not resolve 'us.archive.ubuntu.com'
Ign http://security.ubuntu.com gutsy-security Release
Ign http://security.ubuntu.com gutsy-security/main Packages
Err http://us.archive.ubuntu.com gutsy-updates/main Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Ign http://security.ubuntu.com gutsy-security/restricted Packages
Err http://us.archive.ubuntu.com gutsy-updates/restricted Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Ign http://security.ubuntu.com gutsy-security/main Sources
Err http://us.archive.ubuntu.com gutsy-updates/universe Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Ign http://security.ubuntu.com gutsy-security/restricted Sources
Err http://us.archive.ubuntu.com gutsy-updates/multiverse Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Ign http://security.ubuntu.com gutsy-security/universe Packages
Ign http://us.archive.ubuntu.com gutsy Release
Ign http://security.ubuntu.com gutsy-security/universe Sources
Ign http://us.archive.ubuntu.com gutsy-updates Release
Ign http://us.archive.ubuntu.com gutsy/main Packages
Ign http://security.ubuntu.com gutsy-security/multiverse Packages
Ign http://us.archive.ubuntu.com gutsy/restricted Packages
Ign http://security.ubuntu.com gutsy-security/multiverse Sources
Ign http://us.archive.ubuntu.com gutsy/main Sources
Err http://security.ubuntu.com gutsy-security/main Packages
  Could not resolve 'security.ubuntu.com'
Err http://security.ubuntu.com gutsy-security/restricted Packages
  Could not resolve 'security.ubuntu.com'
Ign http://us.archive.ubuntu.com gutsy/restricted Sources
Err http://security.ubuntu.com gutsy-security/main Sources
  Could not resolve 'security.ubuntu.com'
Ign http://us.archive.ubuntu.com gutsy/universe Packages
Err http://security.ubuntu.com gutsy-security/restricted Sources
  Could not resolve 'security.ubuntu.com'
Ign http://us.archive.ubuntu.com gutsy/universe Sources
Err http://security.ubuntu.com gutsy-security/universe Packages
  Could not resolve 'security.ubuntu.com'
Ign http://us.archive.ubuntu.com gutsy/multiverse Packages
Err http://security.ubuntu.com gutsy-security/universe Sources
  Could not resolve 'security.ubuntu.com'
Ign http://us.archive.ubuntu.com gutsy/multiverse Sources
Err http://security.ubuntu.com gutsy-security/multiverse Packages
  Could not resolve 'security.ubuntu.com'
Ign http://us.archive.ubuntu.com gutsy-updates/main Packages
Err http://security.ubuntu.com gutsy-security/multiverse Sources
  Could not resolve 'security.ubuntu.com'
Ign http://us.archive.ubuntu.com gutsy-updates/restricted Packages
Ign http://us.archive.ubuntu.com gutsy-updates/main Sources
Ign http://us.archive.ubuntu.com gutsy-updates/restricted Sources
Ign http://us.archive.ubuntu.com gutsy-updates/universe Packages
Ign http://us.archive.ubuntu.com gutsy-updates/universe Sources
Ign http://us.archive.ubuntu.com gutsy-updates/multiverse Packages
Ign http://us.archive.ubuntu.com gutsy-updates/multiverse Sources
Err http://us.archive.ubuntu.com gutsy/main Packages
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com gutsy/restricted Packages
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com gutsy/main Sources
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com gutsy/restricted Sources
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com gutsy/universe Packages
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com gutsy/universe Sources
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com gutsy/multiverse Packages
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com gutsy/multiverse Sources
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com gutsy-updates/main Packages
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com gutsy-updates/restricted Packages
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com gutsy-updates/main Sources
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com gutsy-updates/restricted Sources
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com gutsy-updates/universe Packages
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com gutsy-updates/universe Sources
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com gutsy-updates/multiverse Packages
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com gutsy-updates/multiverse Sources
  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/gutsy/Release.gpg  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/gutsy/main/i18n/Translation-en_US.bz2  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/gutsy/restricted/i18n/Translation-en_US.bz2  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/gutsy/universe/i18n/Translation-en_US.bz2  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/i18n/Translation-en_US.bz2  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release.gpg  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/i18n/Translation-en_US.bz2  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/i18n/Translation-en_US.bz2  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/i18n/Translation-en_US.bz2  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/i18n/Translation-en_US.bz2  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://security.ubuntu.com/ubuntu/dists/gutsy-security/Release.gpg  Could not resolve 'security.ubuntu.com'
Failed to fetch http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/i18n/Translation-en_US.bz2  Could not resolve 'security.ubuntu.com'
Failed to fetch http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/i18n/Translation-en_US.bz2  Could not resolve 'security.ubuntu.com'
Failed to fetch http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/i18n/Translation-en_US.bz2  Could not resolve 'security.ubuntu.com'
Failed to fetch http://security.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/i18n/Translation-en_US.bz2  Could not resolve 'security.ubuntu.com'
Failed to fetch http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/binary-i386/Packages.gz  Could not resolve 'security.ubuntu.com'
Failed to fetch http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/binary-i386/Packages.gz  Could not resolve 'security.ubuntu.com'
Failed to fetch http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/source/Sources.gz  Could not resolve 'security.ubuntu.com'
Failed to fetch http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/source/Sources.gz  Could not resolve 'security.ubuntu.com'
Failed to fetch http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/binary-i386/Packages.gz  Could not resolve 'security.ubuntu.com'
Failed to fetch http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/source/Sources.gz  Could not resolve 'security.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/gutsy/main/binary-i386/Packages.gz  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://security.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/binary-i386/Packages.gz  Could not resolve 'security.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/gutsy/restricted/binary-i386/Packages.gz  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://security.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/source/Sources.gz  Could not resolve 'security.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/gutsy/main/source/Sources.gz  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/gutsy/restricted/source/Sources.gz  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/gutsy/universe/binary-i386/Packages.gz  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/gutsy/universe/source/Sources.gz  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/binary-i386/Packages.gz  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/source/Sources.gz  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/binary-i386/Packages.gz  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/binary-i386/Packages.gz  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/source/Sources.gz  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/source/Sources.gz  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/binary-i386/Packages.gz  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/source/Sources.gz  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/binary-i386/Packages.gz  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/source/Sources.gz  Could not resolve 'us.archive.ubuntu.com'
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

```


Since I am not the best at linux, all help would be appreciated on how I can fix this problem :)

Thanks in advance!

---

### Post by dewman0012 on 2008-09-29
Bump!!

---

### Post by dewman0012 on 2008-09-29
It appears I am having issues getting out to websites. What is weird though, our site is displaying fine online, so it has access to the internet. Any ideas?

---

