---
title: "Guvcview webcam app removed from repository"
date: 2024-09-12
forum: Ubuntu Development Version
---

### Post by corradoventu on 2024-09-12
guvcview is a great application to manage the webcam with many options but it has been removed from the repository in exchange for the terrible snapshot/camera
[https://discourse.ubuntu.com/t/guvcview-removed-from-repository/47991/1](https://discourse.ubuntu.com/t/guvcview-removed-from-repository/47991/1)
removed because in error, but if we remove an app because has a bug our system becomes a desert

---

### Post by jbicha on 2024-09-12
It was removed because it was preventing other work from being finished in Ubuntu. It had a Debian Release Critical [bug]("https://bugs.debian.org/1072421") for more than 2 months.

But it sounds like it can be fixed soon and there is a decent chance it can be restored to Ubuntu in time.

Maybe it ought to have been removed earlier so that someone would have taken action sooner!

This has nothing to do with the GNOME Snapshot app. The [critical bug]("https://launchpad.net/bugs/2061687") that broke Snapshot for me and many others (affecting Ubuntu 24.04 LTS too) was fixed upstream and it should get fixed in Ubuntu "soon".

---

### Post by corradoventu on 2024-09-21
Problem fixed and guvcview again in repository
```
corrado@corrado-n3-oo-0908:~$ apt policy guvcview
guvcview:
  Installed: 2.1.0-0.1
  Candidate: 2.1.0-0.1
  Version table:
 *** 2.1.0-0.1 500
        500 http://archive.ubuntu.com/ubuntu oracular/universe amd64 Packages
        100 /var/lib/dpkg/status
corrado@corrado-n3-oo-0908:~$ 

```

---

