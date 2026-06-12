---
title: "VPS OS upgrade?"
date: 2012-07-08
forum: Server Platforms
---

### Post by albertdiones on 2012-07-08
Hi, I have an ubuntu vps with the following info:



```
lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 11.04
Release:        11.04
Codename:       natty
```

My first question is, can I or is it recommended to upgrade to Ubuntu 12?

Second, what is the simplest way to upgrade it?

---

### Post by CharlesA on 2012-07-08
You would have to upgrade to 11.10 then again to 12.04.

[http://askubuntu.com/questions/125693/how-can-i-upgrade-from-11-04-to-12-04](http://askubuntu.com/questions/125693/how-can-i-upgrade-from-11-04-to-12-04)

---

### Post by albertdiones on 2012-07-11
cool, seems like this is the right direction for me. Thanks! :) , I'm now trying this out.

---

### Post by albertdiones on 2012-07-19
Sorry for the late reply :P
it worked!

I just installed the package manager
and ran do-release-upgrade

and just answered defaults on the prompts (cause I don't really understand mostly what it's asking :P)

---

