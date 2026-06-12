---
title: "backport repositories not working"
date: 2006-09-13
forum: Repositories &amp; Backports
---

### Post by wpshooter on 2006-09-13
I get this when trying to update:

[B]Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.[/B]

Should I just **uncheck** these two **backport repositories** or should I **delete** them from the listing ???

Thanks.

---

### Post by Architeuthis on 2006-09-13
Hello, I have exaxtly the same problem as you, but the error message says also this:

[http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/binary-i386/Packages.bz2:](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/binary-i386/Packages.bz2:) MD5Sum isnt the same

i assume there is an internal issue with the ubuntu servers

---

### Post by wpshooter on 2006-09-13
> **Architeuthis said:**
> Hello, I have exaxtly the same problem as you, but the error message says also this:

[http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/binary-i386/Packages.bz2:](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/binary-i386/Packages.bz2:) MD5Sum isnt the same

i assume there is an internal issue with the ubuntu servers

Yes mine says that also, I just could not copy it.

Does this mean that these repositories will no longer be used and they should be taken off of our listings or should we just wait to see if there is as you say a problem with the Ubuntu servers ?

Thanks.

---

### Post by Architeuthis on 2006-09-14
I checked the update manager and the repository works again, it must have been a temporary issue. 
If they stopped using this repo they must have made an update removing this backport from the update manager, i think.

---

