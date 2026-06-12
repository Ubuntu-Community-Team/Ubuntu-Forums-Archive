---
title: "Why firefox is outdated?"
date: 2017-04-09
forum: Ubuntu Development Version
---

### Post by enricobe on 2017-04-09
Hello,
I'm running Xubuntu 17.04. I've updated the system in this moment. There are no more updates, but... Firefox is v50.1.0. 
The last update on Firefox's website is 52.0.2.

Why Firefox is outdated on 17.04? Is there some kind of "feature freeze" for the software?

Thank you,
Enrico

---

### Post by deadflowr on 2017-04-09
It's because updates to Firefox are security updates, primarily, and the development branch doesn't do security updates.

---

### Post by enricobe on 2017-04-09
So I need to wait the official release of 17.04 to update Firefox to v52?

---

### Post by dino99 on 2017-04-09
firefox (52.0.1+build2-0ubuntu1) zesty; urgency=medium (proposed archive)
02 Mar 2017 22:59:32 +0000

---

### Post by harry332 on 2017-04-10
Or,
you can download and install the newest version (52.0.2) from Ubuntu Mozilla Security PPA (Yakkety branch).
It works fine with zesty too.

Here:
[https://launchpad.net/~ubuntu-mozilla-security/+archive/ubuntu/ppa/+packages?field.name_filter=&field.status_filter=published&field.series_filter=yakkety](https://launchpad.net/~ubuntu-mozilla-security/+archive/ubuntu/ppa/+packages?field.name_filter=&field.status_filter=published&field.series_filter=yakkety)

---

### Post by howefield on 2017-04-11
Looks like it has come through from -proposed into -updates now..

```
firefox/zesty-updates,zesty-security 52.0.1+build2-0ubuntu1 amd64 [upgradable from: 50.1.0+build2-0ubuntu1]
firefox-locale-en/zesty-updates,zesty-security 52.0.1+build2-0ubuntu1 amd64 [upgradable from: 50.1.0+build2-0ubuntu1]
```

---

### Post by linuxyogi on 2017-04-12
> **deadflowr said:**
>  the development branch doesn't do security updates.

I didn't know that. So its not safe to use the development branch ?

---

### Post by howefield on 2017-04-13
> **linuxyogi said:**
> I didn't know that. So its not safe to use the development branch ?

Why would you think an unreleased version of Ubuntu would care about your security ?

That's not meant to sound as blunt or as blasé as it might, it is just that the primary focus of a development release is in getting all the pieces working together, including introducing new features. It is as secure as it can be on release day, not necessarily before. <Shrug>.

The development release is intended for testers and testing :)

To get back on topic, I believe there was a Firefox build failure on one of the architectures that led to the delay.

---

### Post by enricobe on 2017-04-14
Thank you, with the last updates (I think after the official release) Firefox has been updated ;)

---

