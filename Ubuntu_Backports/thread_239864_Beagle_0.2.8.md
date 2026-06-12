---
title: "Beagle 0.2.8"
date: 2006-08-19
forum: Ubuntu Backports
---

### Post by shomati_sen on 2006-08-19
I'd like to request a backport of beagle 0.2.8 into Dapper. The key feature in this release is support for Thunderbird.

Thanks,

Shomati

---

### Post by hansdezwart on 2006-08-21
I would like that as well...:D

---

### Post by emix on 2006-08-26
You can try [this]("http://au.ubuntu.cafuego.net/") unofficial build ;)

---

### Post by baumer1122 on 2006-08-31
For those of you who can't wait for it to be official,
[http://au.ubuntu.cafuego.net/dists/dapper-cafuego/beagle/](http://au.ubuntu.cafuego.net/dists/dapper-cafuego/beagle/)

---

### Post by shomati_sen on 2006-09-01
Thanks a lot for the package. I installed it. It's working fine except that it doesn't seem to recognize my Thunderbird Mail folders. Is there something special that I need to do ?

Appreciating your help,

Shomati

---

### Post by shomati_sen on 2006-09-01
So, I built beagle from the source tree listed at your repository and that seems to work with Thunderbird. The reason appears to be that your package didn't contain the backend for Thunderbird which should be listed under /usr/lib/backends/beagle/Backends.

Hope thie helps,

Shomati

---

### Post by hansdezwart on 2006-09-04
Could you please explain exactly what you did to get Thunderbird and MS Word working? I would love some help!

---

### Post by shomati_sen on 2006-09-05
I downloaded the source of Beagle and built it from scratch and installed it under /usr/local. I first uninstalled the official version to avoid clashes between files being in /usr and in /usr/local. 

That was it. However, it crashes repeatedly when trying to index my Thunderbird mail folders; the crash happens about an hour or two into the indexing. I tried 0.2.9, but it appears to have the same problem. 

Shomati

---

