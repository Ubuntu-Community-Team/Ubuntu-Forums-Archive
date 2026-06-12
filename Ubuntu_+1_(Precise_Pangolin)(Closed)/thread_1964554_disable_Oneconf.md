---
title: "disable Oneconf?"
date: 2012-04-24
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by x-shaney-x on 2012-04-24
I generally do my updates through the terminal and have noticed that every time I complete a dist-upgrade, the fan on my laptop ramps up and the desktop slows down considerably.

Looking in top, Oneconf is using all my CPU power.
According to an app search: "oneconf - synchronize your configuration data over the network"

I would assume this means to install the same apps and sources on different computers on the network?

I don't need this at all but if I try to remove oneconf, it also wants to remove Software Centre.
So is it possible to stop oneconf from running?

---

### Post by dino99 on 2012-04-24
actually it is not working well, so remove it.

[https://bugs.launchpad.net/ubuntu/+source/oneconf/+bug/894314](https://bugs.launchpad.net/ubuntu/+source/oneconf/+bug/894314)

---

### Post by x-shaney-x on 2012-04-24
Like I said, it takes Software Centre with it, which I would rather keep but thanks for the heads-up on the bug.
Should get fixed and the bug report gives instructions how to disable oneconf.

---

### Post by VMC on 2012-04-24
From [post#10]("https://bugs.launchpad.net/ubuntu/+source/oneconf/+bug/894314/comments/10"), I decided to go that route for now, even though I don't use software-center:

```
sudo chmod a-x /usr/share/oneconf/oneconf-service
sudo chmod a-x /usr/share/oneconf/oneconf-query
sudo chmod a-x /usr/share/oneconf/oneconf-update

Then:

oneconf-service --stop
```

---

