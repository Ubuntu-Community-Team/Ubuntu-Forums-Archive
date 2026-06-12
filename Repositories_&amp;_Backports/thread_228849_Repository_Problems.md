---
title: "Repository Problems"
date: 2006-08-03
forum: Repositories &amp; Backports
---

### Post by SpongeBob SquarePants on 2006-08-03
I've just moved from Ubuntu to Kubuntu and although I'm using the same repositories, they're incredibly slow in Kubuntu, and some of them seem to time out.

Any ideas?


myname@myname:~$ sudo apt-get update
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release.gpg
Get: 1 [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release.gpg [191B]
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/free Packages
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial/main Packages
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/non-free Packages
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/free Sources
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/non-free Sources
Hit [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/free Packages
Hit [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/non-free Packages
Hit [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/free Sources
Hit [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/non-free Sources
Errhttp://archive.ubuntu.com dapper Release.gpg
  Could not connect to archive.ubuntu.com:80 (82.211.81.182), connection timed out
Get: 2 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [189B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Sources
Errhttp://archive.ubuntu.com dapper-updates Release.gpg
  Could not connect to archive.ubuntu.com:80 (82.211.81.182), connection timed out
Errhttp://archive.ubuntu.com dapper-backports Release.gpg
  Could not connect to archive.ubuntu.com:80 (82.211.81.182), connection timed out
Fetched 2B in 6m0s (0B/s)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg)  Could n                                                                                             ot connect to archive.ubuntu.com:80 (82.211.81.182), connection timed out
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg)                                                                                                     Could not connect to archive.ubuntu.com:80 (82.211.81.182), connection timed out
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-backports/Release.gp](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/Release.gp)                                                                                                   g  Could not connect to archive.ubuntu.com:80 (82.211.81.182), connection timed ou                                                                                                   t
Reading package lists... Done
W: Some index files failed to download, they have been ignored, or old ones used i                                                                                                   nstead.

---

### Post by gmc on 2006-08-03
Your not the only one, I've been having time out problems with I belive the securit repository for a couple of days now. Frustrating to say the least.

G.

---

### Post by SpongeBob SquarePants on 2006-08-03
Hi G,

So maybe the problem's actually with the repositories themselves? I was just wondering why when I change to Kubuntu everything suddenly slows down. If it's just the servers are running slow, annoying thought that is, I can deal with it.....until they get their act together anyway.

---

### Post by vaenyc on 2006-08-03
try the US repositories

[http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu)

---

### Post by burquedout on 2006-08-03
I agree I've been having really bad problems with the speed of the updates.  I found that if you try using the repository mirrors in this post [http://www.ubuntuforums.org/showthread.php?t=133803&page=3](http://www.ubuntuforums.org/showthread.php?t=133803&page=3) they work good for me but don't use them too much I don't want MTSU to take them off their servers.

---

### Post by SpongeBob SquarePants on 2006-08-04
Thanks for the responses guys. But has this just become a problem for everyone in the past few days? I was quite happy with the repositories I was running in Ubunto and have been doing so for a few months. Then I start up Kubuntu, install the exact same repos and suddenly I get time outs. I was wondering whether there was another problem going on here, or whether it was just pure coincidence that the time outs have occurred after I installed Kubuntu.

---

### Post by nismohasan on 2006-08-04
the past week repos have sucked, slow speeds on the us server, AU server has files missing. before then all was fine.

---

