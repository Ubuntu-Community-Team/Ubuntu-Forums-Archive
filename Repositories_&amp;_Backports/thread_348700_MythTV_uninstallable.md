---
title: "MythTV uninstallable"
date: 2007-01-29
forum: Repositories &amp; Backports
---

### Post by Yumi on 2007-01-29
I tried to install MythTV from the repositories. It is not installable due to unresolved dependencies. Following the dependency-tree I end up at libfaad0 not installable without further dependencies. Any advice?

Michael

---

### Post by renzokuken on 2007-01-29
have you got all the repos enabled? you may need to enable the universe and multiverse repos

```
sudo gedit /etc/apt/sources.list
```

(replace gedit with kate if you are using KDE instaed of gnome)

and remove the # from the multiverse and universe repository lines

---

### Post by Titus A Duxass on 2007-01-29
Follow the How-To that can be found in the community documents, MythTV is installable and takes only about 45 minutes to do the whole process.

---

### Post by Yumi on 2007-01-29
All repositories are enabled. But I noted that libfaad0 may have recently been replaced by libfaad2.0. My update manager shows this package as "transitional".

The whole way is that MythTV requires MythBackend which requires libavcodec51d. The last one needs libfaad0. Now I have to find libfaad0 or libavcodec51d has to change requirements. 

This is really a little above my abilities as a user. Maybe I just have to wait a little until it is sorted

Michael

---

### Post by Yumi on 2007-02-03
Filed bugreport 83029 about this.

MM

---

### Post by Titus A Duxass on 2007-02-03
Did you really find a bug?

Did you follow the How-To in the community documents, this How-To has been followed by many people, including myself, without meeting this dependency issue.

> This is really a little above my abilities as a user. Maybe I just have to wait a little until it is sorted - The ability you need is to be able to follow the How-To correctly.

Try again but follow the How-To.

Simply down loading mythtv from the repositories will get you nowhere fast, very fast.

SuperM1 has put a great deal of effort in writing excellent guides, repay him by using them.

---

### Post by Yumi on 2007-02-03
The bug is not in MythTV, The problem is download from repositories and dependencies. Bug has been confirmed.

Michael

---

### Post by Patrick Dixon on 2007-02-09
> **Titus A Duxass said:**
> Follow the How-To that can be found in the community documents, MythTV is installable and takes only about 45 minutes to do the whole process.

I'm sorry but this is complete rubbish.  I've been trying for over two weeks and still no success - and yes I have followed the guides ... 4 times!

---

### Post by basketcase on 2007-02-09
> **Patrick Dixon said:**
> I'm sorry but this is complete rubbish.  I've been trying for over two weeks and still no success - and yes I have followed the guides ... 4 times!


There is a bug or there isn't? Am I p*ssing in the wind trying to Install Myth now?

---

