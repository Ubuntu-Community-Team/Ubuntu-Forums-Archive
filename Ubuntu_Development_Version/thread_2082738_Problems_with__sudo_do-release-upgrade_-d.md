---
title: "Problems with  sudo do-release-upgrade -d"
date: 2012-11-10
forum: Ubuntu Development Version
---

### Post by heavyonion on 2012-11-10
I tried to run sudo do-release-upgrade -d  and I got this error

Traceback (most recent call last):
  File "/usr/bin/do-release-upgrade", line 145, in <module>
    fetcher.run_options += ["--mode=%s" % options.mode,
AttributeError: type object 'DistUpgradeFetcherCore' has no attribute 'run_options'

What do I need to do to fix this?
I was trying to see if I good get the ubuntu 13.04 dailybuild to install. I guess I should post a new thread for this, but can I upgrade to the daily build without having to install fresh from an ISO?

Thanks.

---

### Post by ibjsb4 on 2012-11-10
Is it happening again?

[https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1076186](https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1076186)

---

### Post by Old_Grey_Wolf on 2012-11-10
Since the command "do-release-upgrade -d" is used to upgrade to a development release, I think the post will be best answered in the U +1 (Raring Ringtail) forum.

Moved.

---

### Post by cariboo on 2012-11-10
See my answer, in [this]("http://ubuntuforums.org/showthread.php?t=2082861") thread.

---

