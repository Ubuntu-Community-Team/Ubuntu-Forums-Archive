---
title: "Trying hard to get a repository setup in Ubuntu"
date: 2008-10-06
forum: Repositories &amp; Backports
---

### Post by niccholaspage on 2008-10-06
I am trying to make a repository that has some extras for Ubuntu and Ultimate OS. I added the source to /etc/apt/sources.list. When I do sudo apt-get update, I get these warnings:
```

W: Failed to fetch ftp://niccholaspage@sephizor.com/archive/ubuntu/dists/intrepid/Release.gpg  Could not resolve 'niccholaspage@sephizor.com'

W: Failed to fetch ftp://niccholaspage@sephizor.com/archive/ubuntu/dists/intrepid/main/i18n/Translation-en_US.bz2  Could not resolve 'niccholaspage@sephizor.com'

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems

```
The repository did not work at all.(Repo is at [ftp://niccholaspage@sephizor.com/archive/ubuntu](ftp://niccholaspage@sephizor.com/archive/ubuntu) intrepid main)
The file structure is this:
archive/ubuntu/intrepid/main/
I have have gwho deb and a Packages.gz.

---

### Post by InfinityCircuit on 2008-10-07
man 5 apt.conf

Search for ftp.  You have to specify the password for password-protected ftp servers in /etc/apt/sources.list in the form  [ftp://[](ftp://[)[user][:pass]@]host[:port]/ in ftp::Proxy.

---

### Post by niccholaspage on 2008-10-07
If I set it up like that,Wouldn't it be easy for someone to see my FTP password?

---

### Post by InfinityCircuit on 2008-10-07
Yes. But you can chmod 600 it.  Normally, there is no reason to worry about password-protecting a Debian repository--this is free software, after all.

---

