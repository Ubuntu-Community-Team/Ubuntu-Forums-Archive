---
title: "APT network traffic through port 21"
date: 2007-04-12
forum: Repositories &amp; Backports
---

### Post by Woek on 2007-04-12
At my work I'm behind a firewall that filters http, closes all other ports, except port 21, which is wide open, unfiltered. I noticed that I can't sync APT, let alone retrieve packages, so I was wondering: is it possible to force all network traffic of apt to go through port 21?
I COULD make a tunnel through port 21 to an outside server and forward all ports, but that would be a direct violation of company security...
TIA

---

### Post by tomchuk on 2007-04-13
Just change http for ftp in your /etc/apt/sources.list. My sources.list would change from:
```

deb http://archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://archive.ubuntu.com/ubuntu/ feisty main restricted

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted

```
to:
```

deb ftp://archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src ftp://archive.ubuntu.com/ubuntu/ feisty main restricted

deb ftp://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src ftp://security.ubuntu.com/ubuntu feisty-security main restricted

```

---

### Post by Woek on 2007-04-13
Really, it's that easy?? The servers accept connections on multiple ports?
Thanks Tomchuk, I'll try it first thing on monday!

---

### Post by Surgeon General on 2007-04-19
> **tomchuk said:**
> Just change http for ftp in your /etc/apt/sources.list. My sources.list would change from:
```

deb http://archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://archive.ubuntu.com/ubuntu/ feisty main restricted

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted

```
to:
```

deb ftp://archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src ftp://archive.ubuntu.com/ubuntu/ feisty main restricted

deb ftp://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src ftp://security.ubuntu.com/ubuntu feisty-security main restricted

```


is this like the 'way" to do it? if only port 25 is open then "deb smtp://archive.ubuntu.com" will work?

---

### Post by eentonig on 2007-04-19
I doubt If smtp will work to download repo's.

But both http and ftp are suitable for downloading.

Woek, you worry about breaking company policy, but yet you want to do something they clearly don't allow via port 25. What' s the difference, from your companies point of view, from abusing  port 25 directly or via a tunnel on a unknown server?

---

