---
title: "Availability of Schedulesdirect-Enabled Version Of MythTv Packages"
date: 2007-08-26
forum: Repositories &amp; Backports
---

### Post by tom purl on 2007-08-26
The MythTv project recently changed their TV schedule provider from Zap2It to Schedulesdirect.  Apparently, this involves a code change, which means that a new stable version of MythTv has either been released or will be released soon.  

Does anyone know of this new version will be available from the "official" repositories, or should I look for it in the backports repository?  I am running Ubuntu 6.10.  

Thank you,

Tom Purl

---

### Post by spottedcow on 2007-08-27
This questions should go to the package maintainers:

```
mythtv:~$ apt-cache show mythtv
Package: mythtv
Priority: optional
Section: multiverse/graphics
Installed-Size: 68
Maintainer: MythTV Ubuntu Maintainers <ubuntu-mythtv@lists.ubuntu.com>
Original-Maintainer: Christian Marillat <marillat@debian.org>
Architecture: all
Version: 0.20-svn20070122-0.0ubuntu6
...
```

A google search for the Maintainers email address finds this link:
[https://lists.ubuntu.com/mailman/listinfo/Ubuntu-mythtv]("https://lists.ubuntu.com/mailman/listinfo/Ubuntu-mythtv")
Which has a link to the archives of the mailing list.

If you look at the last couple posts to that list, it looks like the maintainers are aware and are testing the update right now.  I'd guess we are a few days away from the package release of the update.

---

### Post by tom purl on 2007-08-27
> **spottedcow said:**
> This questions should go to the package maintainers:

...

A google search for the Maintainers email address finds this link:
[https://lists.ubuntu.com/mailman/listinfo/Ubuntu-mythtv]("https://lists.ubuntu.com/mailman/listinfo/Ubuntu-mythtv")
Which has a link to the archives of the mailing list.

Thanks for the tip!  I posted the question to this forum instead of trying to contact a maintainer directly because I wanted everyone to benefit from the question.  I didn't, however, know that the mythtv on Ubuntu package mantainers had their own mailing list.  I will look for something like that in the future.

> **spottedcow said:**
> If you look at the last couple posts to that list, it looks like the maintainers are aware and are testing the update right now.  I'd guess we are a few days away from the package release of the update.

I really thought that I did a search on "schedulesdirect" in the forum before I posted my question and didn't find any results.  I just did another search, and found that there was already [a long-running thread]("http://ubuntuforums.org/showthread.php?t=479061&highlight=schedulesdirect") on this subject.  I apologize for the unnecessary post.

Thanks again for the help!

Tom Purl

---

