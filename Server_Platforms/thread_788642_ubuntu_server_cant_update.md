---
title: "ubuntu server cant update"
date: 2008-05-09
forum: Server Platforms
---

### Post by nuclearmaker on 2008-05-09
after

```
sudo apt-get update
```

got

> Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/source/Sources.bz2](http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/source/Sources.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/gutsy/universe/binary-i386/Packages.gz)  Could not connect to us.archive.ubuntu.com:80 (91.189.88.45). - connect (111 Connection refused) [IP: 91.189.88.45 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy/universe/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/gutsy/universe/source/Sources.gz)  Could not connect to us.archive.ubuntu.com:80 (91.189.88.45). - connect (111 Connection refused) [IP: 91.189.88.45 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/binary-i386/Packages.gz)  Could not connect to us.archive.ubuntu.com:80 (91.189.88.45). - connect (111 Connection refused) [IP: 91.189.88.45 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/source/Sources.gz)  Could not connect to us.archive.ubuntu.com:80 (91.189.88.45). - connect (111 Connection refused) [IP: 91.189.88.45 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/binary-i386/Packages.gz)  Could not connect to us.archive.ubuntu.com:80 (91.189.88.45). - connect (111 Connection refused) [IP: 91.189.88.45 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/binary-i386/Packages.gz)  Could not connect to us.archive.ubuntu.com:80 (91.189.88.45). - connect (111 Connection refused) [IP: 91.189.88.45 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/source/Sources.gz)  Could not connect to us.archive.ubuntu.com:80 (91.189.88.45). - connect (111 Connection refused) [IP: 91.189.88.45 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/source/Sources.gz)  Could not connect to us.archive.ubuntu.com:80 (91.189.88.45). - connect (111 Connection refused) [IP: 91.189.88.45 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/binary-i386/Packages.gz)  Could not connect to us.archive.ubuntu.com:80 (91.189.88.45). - connect (111 Connection refused) [IP: 91.189.88.45 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/source/Sources.gz)  Could not connect to us.archive.ubuntu.com:80 (91.189.88.45). - connect (111 Connection refused) [IP: 91.189.88.45 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/binary-i386/Packages.gz)  Could not connect to us.archive.ubuntu.com:80 (91.189.88.45). - connect (111 Connection refused) [IP: 91.189.88.45 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/source/Sources.gz)  Could not connect to us.archive.ubuntu.com:80 (91.189.88.45). - connect (111 Connection refused) [IP: 91.189.88.45 80]
Reading package lists... Done
W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release: The following signatures were invalid: NODATA 1 NODATA 2
W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release: The following signatures were invalid: NODATA 1 NODATA 2
W: GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release: The following signatures were invalid: NODATA 1 NODATA 2
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by tamoneya on 2008-05-09
i just saw this problem in a similar thread.  Seems like some key got corrupted on a server.  Here is what we have determined so far:
[http://ubuntuforums.org/showthread.php?p=4923346](http://ubuntuforums.org/showthread.php?p=4923346)

---

### Post by cdtech on 2008-05-10
gpg key is your problem, without it or corrupted your connection will be refused.

Did you get it repaired?

---

### Post by tamoneya on 2008-05-10
since this happened to two people at the same time I am guessing it is a server side issue.  You could try switching your mirror.  I recommeneded that the other user with this error should try this and he hasnt replied back yet.  Try that if you get a chance.

---

### Post by cdtech on 2008-05-10
> **tamoneya said:**
> since this happened to two people at the same time I am guessing it is a server side issue.  You could try switching your mirror.  I recommeneded that the other user with this error should try this and he hasnt replied back yet.  Try that if you get a chance.

What two people? I just see one posting this. Just curious, am I missing another thread somewhere? :)

I have no problems with my us archives.

---

### Post by jgni on 2008-05-11
No alternative way to get updated?
I can see the mirrors fine, but what about the key-problem?

---

### Post by nuclearmaker on 2008-05-11
change the mirror got same error.
by da way,thx for fast reply. ^^

---

### Post by letrappe on 2008-05-13
I've got a similar problem.  Every time I try to update or install software, it gives me 302 Redirect.

I can ping multiple internet sites and even the repositories themselves.  

I tried to change the PGP key, but it won't accept it.  It replies: "gpg:  no valid OpenPGP data found.

---

### Post by cdtech on 2008-05-15
This is a server issue, not the first time this has happened. 

Some users say to remove the "us" from the sources.list (us.archive.ubuntu.com) to say "archive.ubuntu.com" instead, and that this will work, but the security concerns me without the authentication of the pgp key. 

Has anyone found out what the problem from the server is?

---

### Post by letrappe on 2008-05-16
I tried the suggestion of removing the "us" from "us.archive...etc" from the sources.list, but still get the same result.  

I'm gonna bypass my firewall and go directly through the main internet connection to see if it will get the updates or not.  The server has full access, but somehow it keeps receiving the "302 Redirect" messages.

Thanks for the suggestion, cdtech.:wink:

---

### Post by letrappe on 2008-05-16
I've bypassed my firewall and ran "apt-get update" after deleting the "us" from the "us.*****.***" and it successfully updates.  

I'm also able to download applications and install them now. 

ALL SET!

Now I have to figure out where in the firewall that it's redirecting and how to change it so the "apt-get" command doesn't get redirected.  

:-({|=

---

