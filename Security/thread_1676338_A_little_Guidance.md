---
title: "A little Guidance"
date: 2011-01-27
forum: Security
---

### Post by inobe on 2011-01-27
i have openssh on my box with kubuntu 10.10, i didn't install it and would like to know it's purpose being on here?

thanks

---

### Post by crashed111 on 2011-01-27
openssh client or openssh server?

openssh client is always installed as you never know when you may want to ssh somewhere and dosent really pose any security risk.

---

### Post by inobe on 2011-01-27
thanks, can i just remove it?

```
@linux-boss:~$ dpkg -s openssh-client
Package: openssh-client
Status: install ok installed
Priority: standard
Section: net

```

```
@linux-boss:~$ dpkg -s openssh-server
Package `openssh-server' is not installed and no info is available.
```

---

### Post by uRock on 2011-01-27
ssh is not a security risk when openssh-server is not installed. I would leave it be.

---

### Post by inobe on 2011-01-27
will do, much appreciated.

---

