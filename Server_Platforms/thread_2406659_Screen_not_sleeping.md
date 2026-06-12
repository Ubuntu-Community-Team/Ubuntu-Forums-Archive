---
title: "Screen not sleeping"
date: 2018-11-23
forum: Server Platforms
---

### Post by HavocXphere on 2018-11-23
My laptop screen never seems to go to sleep. Since I log in via SSH anyway that's less than ideal.

I've managed to switch it off via:
```
sudo vbetool dpms off
```

But I'd like classic sleep behaviour in case I lock myself out of SSH.

Any ideas? Most of googling leads to topics on how to disable it and/or are about graphical interfaces

Edit...18.10

---

### Post by dbergst on 2018-11-23
You may want to see this bug report:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1767568](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1767568)

In particular my comment here [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1767568/comments/24](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1767568/comments/24)

---

### Post by HavocXphere on 2018-11-24
> **dbergst said:**
> You may want to see this bug report:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1767568](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1767568)

In particular my comment here [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1767568/comments/24](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1767568/comments/24)
Thanks. Might be dealing with an actual bug then :/

Any idea how to get it to turn the screen off though, instead of blanking it? Cause that's my main aim here.

---

