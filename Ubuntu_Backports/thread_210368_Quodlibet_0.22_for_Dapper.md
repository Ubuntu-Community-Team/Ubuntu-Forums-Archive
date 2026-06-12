---
title: "Quodlibet 0.22 for Dapper"
date: 2006-07-06
forum: Ubuntu Backports
---

### Post by mlind on 2006-07-06
I backported Quodlibet for personal use, but I uploaded it if anyone else needs it
[http://www.freefilehoster.com/uploads/1152217284quodlibet-0.22_dapper.tar.gz](http://www.freefilehoster.com/uploads/1152217284quodlibet-0.22_dapper.tar.gz)

---

### Post by eewald on 2006-07-24
thank you very much, just what i was looking for! 

:)

---

### Post by mlind on 2006-07-24
> **eewald said:**
> thank you very much, just what i was looking for! 

:)

You can also grab cvs snapshot of quodlibet-plugins from
```

deb http://www.elisanet.fi/mlind/ubuntu dapper main 

```

---

### Post by mmcmonster on 2006-07-27
> **mlind said:**
> You can also grab cvs snapshot of quodlibet-plugins from
```

deb [http://www.elisanet.fi/mlind/ubuntu](http://www.elisanet.fi/mlind/ubuntu) dapper main 

```

Do you happen to have a GPG key for that repository?  Or at least a list of what else is in it?

I was surprised to notice that rhythmbox was updated as well.  Gaim is supposed to be updated, but it was kept back for some reason.

---

### Post by mmcmonster on 2006-07-27
Answered my own request for a GPG key.  It's funny what you can find with google, sometimes. (I googled for D0AFFF5E937215FF):
```

gpg --keyserver pgp.mit.edu --recv-key D0AFFF5E937215FF
gpg -a --export D0AFFF5E937215FF | sudo apt-key add -

```

---

