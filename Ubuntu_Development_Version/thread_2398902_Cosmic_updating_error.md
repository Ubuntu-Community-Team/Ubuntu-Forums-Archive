---
title: "Cosmic updating error"
date: 2018-08-19
forum: Ubuntu Development Version
---

### Post by dino99 on 2018-08-19
Looks like the latest appstream does not support yet the latest apturl changes:

E: Problem executing scripts APT::Update::Post-Invoke-Success 'if /usr/bin/test -w /var/cache/app-info -a -e /usr/bin/appstreamcli; then appstreamcli refresh-cache > /dev/null; fi'
E: Sub-process returned an error code

---

### Post by awamunro on 2018-08-19
I have the same error. How are we going to fix this??

---

### Post by flocculant on 2018-08-19
Works fine for me.

I had the issue this morning when I enabled -proposed to see if there was something there, when I disabled it again it's fine.

> **awamunro said:**
> I have the same error. How are we going to fix this??

So - using proposed for some reason? Disable proposed and see if it works.

---

### Post by awamunro on 2018-08-19
> **flocculant said:**
> Works fine for me.

I had the issue this morning when I enabled -proposed to see if there was something there, when I disabled it again it's fine.



So - using proposed for some reason? Disable proposed and see if it works.

Yes disabling proposed worked for me too.

---

### Post by flocculant on 2018-08-19
> **awamunro said:**
> Yes disabling proposed worked for me too.

Don't doubt it - still bewildered why people think running with it enabled permanently is at all useful.

---

### Post by rrnbtter on 2018-08-19
Greetings,

> **flocculant said:**
> Don't doubt it - still bewildered why people think running with it enabled permanently is at all useful.

This section is for the discussion of development of Cosmic Cuttlefish, and the testing of Bionic and Xenial point releases.  There is a perfectly good reason for keeping Proposed permanently enabled. One shouldn't be bewildered by that fact.  In an unstable version packages can be broken regardless of the status of Proposed.  I have had Proposed enable on my primary machine for years and I've only had to reinstall thirty or forty times. So its harmless.  If one can't handle it, one should disable Proposed and use a stable version. Thats why we have choices.

---

### Post by jbicha on 2018-08-19
> **rrnbtter said:**
> 

I have had Proposed enable on my primary machine for years and I've only had to reinstall thirty or forty times.


I bet you could significantly reduce that number by not running -proposed during the development cycle.

Anyway, it looks like this issue has been fixed in [Debian]("https://bugs.debian.org/868018") and will be fixed in Ubuntu whenever appstream 0.12.2-2 is synced.

autosync is temporarily disabled but someone will probably manually sync it this week.

---

### Post by rrnbtter on 2018-08-19
Greetings,

> **jbicha said:**
> I bet you could significantly reduce that number by not running -proposed during the development cycle.



Yep, and I'll bet I could significantly reduce what I learned by doing those installs by not running proposed.  But I still believe that the worst package failures have occurred during past dev cycles even without proposed and especially with the wifi problems which can really leave one in a bind if they only have a single machine. Hence, an inexperienced user can have major problems running a development (unstable) version. And experience comes from surviving decisions (right or wrong). I will say though that Ubuntu Cosmic/Gnome/Wayland is a delight.  I can understand a new user wanting to be a part of this current cycle. And anything that can attract a new user into becoming an experienced user is a good thing.

---

### Post by flocculant on 2018-08-20
> **rrnbtter said:**
> Greetings,



This section is for the discussion of development of Cosmic Cuttlefish, and the testing of Bionic and Xenial point releases.  There is a perfectly good reason for keeping Proposed permanently enabled. One shouldn't be bewildered by that fact.  In an unstable version packages can be broken regardless of the status of Proposed.  I have had Proposed enable on my primary machine for years and I've only had to reinstall thirty or forty times. So its harmless.  If one can't handle it, one should disable Proposed and use a stable version. Thats why we have choices.

How is using -proposed and I suppose testing packages in there useful? 

You don't know for sure that those packages will even be used - or superseded by packages that work properly ... 

That is what bewilders me.

As far as what this sub-forum is for - I'll know a whole lot more about it than you. You don't know me - you don't know who I've been, nor how long I've been about.

---

### Post by dino99 on 2018-08-20
appstream 0.12.2-2 have solved that issue. Thanks to Jeremy for glancing at this forum & syncing.

---

