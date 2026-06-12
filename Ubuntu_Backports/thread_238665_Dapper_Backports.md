---
title: "Dapper Backports?"
date: 2006-08-18
forum: Ubuntu Backports
---

### Post by earth2mark on 2006-08-18
I guess there are no Dapper Backports?  Can anyone tell me the status of them?  There are a few I'd really love to see, such as:

phpMyAdmin (the one in Dapper doesn't work with MySQL 5 AFAIK)
Squirrelmail (security issues)
Roundcubemail (the one is Dapper is totally disfunctional)
etc.

Thanks!

---

### Post by whatever on 2006-08-24
looks like dapper backports just startet :)
at least there's a new libtheora version and nexuiz packages in dapper-backports now.

---

### Post by jdong on 2006-08-24
They have just started today. It's been a long delay, as they had to port the Backports infrastructure to the new launchpad build system. Now that Backports is processing, I've been working overtime today trying to process as many requests as I could.

---

### Post by McQuaid on 2006-08-30
So what's dapper proposed, is it similar to the old staging?

[http://archive.ubuntu.com/ubuntu/dists/dapper-proposed](http://archive.ubuntu.com/ubuntu/dists/dapper-proposed)

And is there a list anywhere of whats in proposed backports?

I always wished there was an easy way of showing the source (i.e. what rep it's actually coming from) of a particular pkg in synaptic.

---

### Post by ubuntu_demon on 2006-08-30
> **jdong said:**
> They have just started today. It's been a long delay, as they had to port the Backports infrastructure to the new launchpad build system. Now that Backports is processing, I've been working overtime today trying to process as many requests as I could.
Great!

Thanks for your hard work and efforts.

---

### Post by jdong on 2006-08-30
> **McQuaid said:**
> So what's dapper proposed, is it similar to the old staging?

[http://archive.ubuntu.com/ubuntu/dists/dapper-proposed](http://archive.ubuntu.com/ubuntu/dists/dapper-proposed)

And is there a list anywhere of whats in proposed backports?

I always wished there was an easy way of showing the source (i.e. what rep it's actually coming from) of a particular pkg in synaptic.

dapper-proposed is the precursor to dapper-updates, not connected with backports. It's used as a staging area for dapper-updates that could potentially be risky.

dapper-backports does not have a staging area, but rather for backports that I feel I can't QA completely I'll attach testing debs to the launchpad request and ask users to test them for me.

---

### Post by tikal26 on 2006-09-02
what is the repo url

---

### Post by IanW on 2006-09-09
It's one of the standard repo's that come up when you open Synaptic's settings. Just scroll down towards Universe & Multiverse.

---

### Post by tikal26 on 2006-09-09
I don't have it so if someone could let me know which one it is

---

### Post by HAARP on 2006-09-10
# Ubuntu backports project (GPG key: 437D05B5)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

---

### Post by tikal26 on 2006-09-11
thanks really apreciate your help

---

### Post by LazyBoy on 2006-09-13
Seeing a MD5Sum problem with the lists from us.archive and archive....

---

### Post by Johan! on 2006-09-13
I see the problem too:

[http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/binary-i386/Packages.bz2:](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/binary-i386/Packages.bz2:) MD5Sum mismatch
[http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/source/Sources.bz2:](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/source/Sources.bz2:) MD5Sum mismatch

---

