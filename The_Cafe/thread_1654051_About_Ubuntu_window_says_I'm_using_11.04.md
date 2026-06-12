---
title: "About Ubuntu window says I'm using 11.04"
date: 2010-12-27
forum: The Cafe
---

### Post by TheNerdAL on 2010-12-27
I wanted to see what version of Ubuntu I was running. I knew it was 10.10, but I wanted to see what name it was so I checked in the About me window and it said I was running 11.04. I'm confused. And no I'm not asking for help, I'm just stating that it's weird. Is this normal?

---

### Post by howefield on 2010-12-27
It is most likely this bug...

[https://bugs.launchpad.net/ubuntu/+source/ubuntu-docs/+bug/690248](https://bugs.launchpad.net/ubuntu/+source/ubuntu-docs/+bug/690248)

What is the output of the following terminal command ?

```
lsb_release -a
```

---

### Post by susema on 2010-12-27
Check it. &#304;n terminal;

```
uname -r
```
```
cat /etc/lsb-release
```

---

### Post by TheNerdAL on 2010-12-27
> **howefield said:**
> It is most likely this bug...

[https://bugs.launchpad.net/ubuntu/+source/ubuntu-docs/+bug/690248](https://bugs.launchpad.net/ubuntu/+source/ubuntu-docs/+bug/690248)

What is the output of the following terminal command ?

```
lsb_release -a
```

```
adrian@adrian-desktop:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 10.10
Release:	10.10
Codename:	maverick
adrian@adrian-desktop:~$ 

```

---

