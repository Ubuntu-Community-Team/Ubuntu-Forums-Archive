---
title: "apt-get update error:"
date: 2009-06-28
forum: Server Platforms
---

### Post by Gorlist on 2009-06-28
Good day, just installed Ubuntu 8.04 minimal. when running apt-get update I keep receiving this error:

> # apt-get update
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release.gpg
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Packages
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/Release](http://archive.ubuntu.com/ubuntu/dists/hardy/Release)  Unable                                   to find expected entry  multiuniverse/binary-amd64/Packages in Meta-index file (                                  malformed Release file?)

E: Some index files failed to download, they have been ignored, or old ones used                                   instead.


Any suggestions?

Thanks.

---

### Post by LepeKaname on 2009-06-28
Can you post your /etc/apt/sources.lst ?
Try using a mirror server, for example:

[http://ca.archive.ubuntu.com/ubuntu/dists/](http://ca.archive.ubuntu.com/ubuntu/dists/)
[http://jp.archive.ubuntu.com/ubuntu/dists/](http://jp.archive.ubuntu.com/ubuntu/dists/)
[http://mx.archive.ubuntu.com/ubuntu/dists/](http://mx.archive.ubuntu.com/ubuntu/dists/)
[http://fr.archive.ubuntu.com/ubuntu/dists/](http://fr.archive.ubuntu.com/ubuntu/dists/)

etc...

Sometimes it may fix your problem.

---

### Post by Gorlist on 2009-06-29
Hi Lepe, heres my source list:

```
deb http://archive.ubuntu.com/ubuntu hardy main
deb http://archive.ubuntu.com/ubuntu hardy universe
deb http://archive.ubuntu.com/ubuntu hardy multiuniverse
```

Must be caused by how ive entered the universe/multi...

Does anyone have an example of their 8.04 Server sources.list? currently have the minimal installation.

---

### Post by LepeKaname on 2009-06-29
Here is your error:

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hardy multiuniverse

must be:

deb [http://jp.archive.ubuntu.com/ubuntu/](http://jp.archive.ubuntu.com/ubuntu/) hardy **multiverse**

This is mine:

> deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hardy main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hardy-updates main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hardy universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hardy-updates universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hardy multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hardy-updates multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse

#Sources:
#deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hardy main restricted
#deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hardy-updates main restricted
#deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hardy universe
#deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hardy-updates universe
#deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hardy multiverse
#deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hardy-updates multiverse
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse

---

### Post by Gorlist on 2009-06-29
thank you :) all working.

---

