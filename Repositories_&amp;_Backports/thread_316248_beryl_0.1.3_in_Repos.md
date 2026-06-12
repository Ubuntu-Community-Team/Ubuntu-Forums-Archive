---
title: "beryl 0.1.3 in Repos?"
date: 2006-12-10
forum: Repositories &amp; Backports
---

### Post by redDEADresolve on 2006-12-10
Does anyone know when Beryl 0.1.3 is going to hit the repos? 

So far I only see 0.1.2.

And does anyone know where I can grab the .deb and install it myself if the repos are going to take awhile?

---

### Post by daou on 2006-12-10
This was discussed in the Beryl forums.
[http://forum.beryl-project.org/viewtopic.php?t=56]("http://forum.beryl-project.org/viewtopic.php?t=56")

beerorkid posted:
> put these in your sources.list and comment out other beryl repo's

Code:
 deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) edgy beryl-svn
deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) edgy beryl-svn


then it a simple apt-get update / upgade 

You will get the newest plugins with it as well, including 3D world.

---

### Post by redDEADresolve on 2006-12-11
The repos just got upgraded with Beryl 0.1.3


!!YAY!!

---

### Post by Ferio on 2006-12-12
Please, may I know which the public key for that repos is? I want them to be signed.

---

### Post by redDEADresolve on 2006-12-12
> **Ferio said:**
> Please, may I know which the public key for that repos is? I want them to be signed.

[http://wiki.beryl-project.org/wiki/Install/Ubuntu](http://wiki.beryl-project.org/wiki/Install/Ubuntu)

thats the offical beryl guide on setting up ubuntu and beryl

if you have any questions I'll be home from school later tonight and I'll try to help

---

### Post by Ferio on 2006-12-13
All I needed was the public key of the repos, since I was using other ones; but now I've got it, thanks to you ;)

---

