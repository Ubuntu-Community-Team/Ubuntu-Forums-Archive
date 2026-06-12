---
title: "apt-get GPG error"
date: 2017-03-24
forum: Server Platforms
---

### Post by geohei on 2017-03-24
Hi.

I have this since 22.03.2017.
```
root@gan:~# apt-get update
Get:1 http://lu.archive.ubuntu.com trusty InRelease
Ign http://lu.archive.ubuntu.com trusty InReleaselib/apt/lists/partial/lu.archive.ubuntu.com_ubuntu_dists_trusty_InRelease into data and signature failed
E: GPG error: http://lu.archive.ubuntu.com trusty InRelease: Clearsigned file isn't valid, got 'NODATA' (does the network require authentication?)
```

System is productive (I can't fiddle around like crazy).
It runs 24/7 since +/- 2 1/2 years.
Didn't touch anything at system and/or network config.
Weekly apt-get update/upgrades.
Never any issues.

Why did this error show up all of a sudden?
How can I fix it?

Thanks

---

### Post by bhavi2 on 2017-03-24
Are you behind a proxy?

---

### Post by geohei on 2017-03-24
Forgot to mention ... sorry ... no proxy.
Nothing elso fancy.
No network change, except that I upgraded my FRITZ!Box (router) firmware from 6.52 to 6.80.
The error showed up more or less at the same time, but not sure if any correlation between both events.

---

### Post by geohei on 2017-03-24
F#&% ... I found the problem.
Parental control within the FRITZ!Box.
No surprise ... always a mess when AVM upgrades!

Besides this (OT), is it normal that I get asked every time I login into this forum my full name at the "Personal Data Request" page? A pain ...

Thanks,

---

### Post by geohei on 2017-05-30
> **geohei said:**
> ...
Besides this (OT), is it normal that I get asked every time I login into this forum my full name at the "Personal Data Request" page? A pain ...


Is it normal that this page always pops up?

> Personal Data Request

You are logging in to [https://ubuntuforums.org](https://ubuntuforums.org)

Ubuntu Forums https has requested some personal information, please choose what you would like to share:

    Full name: ...
    Username: ...
    Email address: ...

---

