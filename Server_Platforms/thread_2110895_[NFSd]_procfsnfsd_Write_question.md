---
title: "[NFSd] /proc/fs/nfsd/* Write question"
date: 2013-01-31
forum: Server Platforms
---

### Post by Quivalen on 2013-01-31
I'm in the need of tweak some parameters of nfsd.

In particular i need to change the values of nfsv4gracetime and nfsv4leasetime.

Looking on google i've discovered that these parameters are stored inside /proc/fs/nfsd/*

Unfortunatly everytime i try something like
echo 10 > /proc/fs/nfsd/nfsv4gracetime

i encounter some kind of error.

Basically it's impossible to reproduce the steps showed there: [http://ubuntuforums.org/showpost.php?p=10931290&postcount=7](http://ubuntuforums.org/showpost.php?p=10931290&postcount=7)

Because i'm not allowed to write on the file (if the nfs service is started) or the file simply doesn't exist (if the nfs service is stopped, therefore the /proc/fs/nfsd filesystem isn't mounted)

Any idea ?

---

