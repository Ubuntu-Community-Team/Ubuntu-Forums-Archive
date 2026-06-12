---
title: "Synaptic Package Manager returns old versions of IDEs"
date: 2007-12-26
forum: Repositories &amp; Backports
---

### Post by vagenas on 2007-12-26
Hello! I needed to install Netbeans and Eclipse IDEs on Ubuntu 7.10. After searching by means of the Synaptic Package Manager, I found out that the available versions are:
- netbeans5.5.1-2 and
- eclipse3.2.2-3, respectively,
while the latest ones, according to the official sites are:
- netbeans6.0 and
- eclipse3.3, respectively, Moreover, none of the aforementioned IDE versions are Beta (I think eclipse 3.3 is more-than-5-month-old).
Is this because we are waiting for these versions to get more stable?
Thanks in advance!

(By mistake, I posted the same question in "Programming Talk" and just found out that "Repositories & Backports" group of discussions is more suitable.)

---

### Post by F-3582 on 2007-12-27
Try [Prevu]("https://wiki.ubuntu.com/Prevu").

Make sure that the line in your sources.list goes as follows:

```
deb-src http://archive.ubuntu.com/ubuntu hardy main restricted universe multiverse
```

EDIT: Sorry, I just checked. Hardy doesn't include those latest versions, either. You might want to file a [sync request]("https://wiki.ubuntu.com/SyncRequestProcess") for [netbeans-ide]("http://packages.debian.org/sid/netbeans-ide") from Debian sid contib (eclipse is still at version 3.2.2, even in unstable).

Once the package is sync'ed, you can backport it yourself with Prevu.

---

### Post by vagenas on 2007-12-29
Thanks F-3582! If I find some time, I will check this procedure in detail. I guess that Debian users will be glad if the software providers start providing their products in .deb format apart from a setup file appropriate for all Linux distributions. For example, Google provides its "Google Desktop" in .deb and .rpm file formats ( [http://desktop.google.com/en/linux/download.html](http://desktop.google.com/en/linux/download.html) )
Regards!

---

### Post by F-3582 on 2007-12-29
Yeah, that would be a good start. On the other hand, it would be even more convenient, if the software providers started releasing their packages in the Partners/Contrib repository like Opera Software.

---

