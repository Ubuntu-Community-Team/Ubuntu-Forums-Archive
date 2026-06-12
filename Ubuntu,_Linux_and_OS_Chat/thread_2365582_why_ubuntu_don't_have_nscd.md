---
title: "why ubuntu don't have nscd"
date: 2017-07-07
forum: Ubuntu, Linux and OS Chat
---

### Post by unityforever on 2017-07-07
does ubuntu have no dns cache...?

---

### Post by QIII on 2017-07-08
Hello!

It isn't installed by default, but you can install nscd easily:

```
sudo apt install nscd
```

[Here]("http://manpages.ubuntu.com/manpages/zesty/man5/nscd.conf.5.html") is the man page for nscd so you can configure it.

Cheers!

---

### Post by unityforever on 2017-07-08
> **QIII said:**
> Hello!

It isn't installed by default, but you can install nscd easily:

```
sudo apt install nscd
```

[Here]("http://manpages.ubuntu.com/manpages/zesty/man5/nscd.conf.5.html") is the man page for nscd so you can configure it.

Cheers!

does ubuntu have any DNS cache? or it just queries servers every times?

---

