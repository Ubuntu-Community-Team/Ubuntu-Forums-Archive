---
title: "Could not download all repository indexes?"
date: 2006-11-18
forum: Repositories &amp; Backports
---

### Post by Candace90 on 2006-11-18
I attempted to update my machine using Synaptic and got this error:

"Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences."

Here's what the error box below showed:

```
http://us.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg: Connection failed [IP: 146.137.96.7 80]
http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg: Connection failed [IP: 146.137.96.7 80]
http://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg: Connection failed [IP: 195.248.90.38 80]
http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/Release.gpg: Connection failed [IP: 146.137.96.7 80]
http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg: Connection failed
http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-i386/Packages.gz: Connection failed
http://us.archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.gz: Connection failed [IP: 146.137.96.7 80]
http://archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages.gz: Connection failed [IP: 195.248.90.38 80]
http://us.archive.ubuntu.com/ubuntu/dists/dapper/restricted/source/Sources.gz: Connection failed [IP: 146.137.96.7 80]
http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/binary-i386/Packages.gz: Connection failed
http://us.archive.ubuntu.com/ubuntu/dists/dapper/universe/source/Sources.gz: Connection failed [IP: 146.137.96.7 80]
http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz: Connection failed [IP: 146.137.96.7 80]
http://archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz: Connection failed [IP: 195.248.90.38 80]
http://security.ubuntu.com/ubuntu/dists/dapper-security/main/source/Sources.gz: Connection failed
http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-i386/Packages.gz: Connection failed [IP: 146.137.96.7 80]
http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz: Connection failed [IP: 146.137.96.7 80]
http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz: Connection failed [IP: 195.248.90.38 80]
http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/source/Sources.gz: Connection failed
http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/source/Sources.gz: Connection failed [IP: 146.137.96.7 80]
http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/main/binary-i386/Packages.gz: Connection failed [IP: 146.137.96.7 80]
http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/binary-i386/Packages.gz: Connection failed [IP: 195.248.90.38 80]
http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/binary-i386/Packages.gz: Connection failed [IP: 146.137.96.7 80]
http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/binary-i386/Packages.gz: Connection failed [IP: 146.137.96.7 80]
http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/binary-i386/Packages.gz: Connection failed [IP: 146.137.96.7 80]
http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/main/source/Sources.gz: Connection failed [IP: 146.137.96.7 80]
http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/source/Sources.gz: Connection failed [IP: 146.137.96.7 80]
http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/source/Sources.gz: Connection failed [IP: 146.137.96.7 80]
http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/source/Sources.gz: Connection failed [IP: 146.137.96.7 80]
```

I attempted to fix my repository, but now I seem to have 2 different sources.list files, one backup, and one that ends in .save. I saw this: [http://www.linuxforums.org/forum/installation/66311-cant-download-all-repository-indexes.html](http://www.linuxforums.org/forum/installation/66311-cant-download-all-repository-indexes.html) and it says the bug was fixed, but I have a copy of Dapper that was shipped several months ago. ](*,) 

Any help would be greatly appreciated.

---

### Post by slimdog360 on 2006-11-19
Try replacing your sources list with the one from the psychocats page
[http://psychocats.net/ubuntu/sources]("http://psychocats.net/ubuntu/sources")

Make sure you replace it with the right one. It has source lists for edgy, dapper and breezy.

---

