---
title: "No candidate version found for ..."
date: 2009-11-05
forum: Server Platforms
---

### Post by boondocks on 2009-11-05
On a "Ubuntu 8.04.3 LTS" server, I wanted to install Asterisk.

```
sudo   aptitude   install  asterisk
```

> Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
[B]No candidate version found for asterisk
No candidate version found for asterisk[/B]
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
But I have seen Asterisk running on another Ubuntu 8.04
What am I missing?

---

### Post by cdenley on 2009-11-05
> **boondocks said:**
> What am I missing?

Probably the universe repository.
```

grep "^[^#]" /etc/apt/sources.list

```

Or maybe you just need to do a
```

sudo apt-get update

```

---

### Post by boondocks on 2009-11-05
> **cdenley said:**
> 

Or maybe you just need to do a
```

sudo apt-get update

```

I tried this.  It did not make any difference.

---

### Post by boondocks on 2009-11-05
> **cdenley said:**
> Probably the universe repository.
```

grep "^[^#]" /etc/apt/sources.list

```

The results are:
```
deb http://archive.ubuntu.com/ubuntu hardy main restricted
deb http://archive.ubuntu.com/ubuntu hardy-updates main restricted
deb http://security.ubuntu.com/ubuntu/ hardy-security main restricted

```

---

### Post by cdenley on 2009-11-05
> **boondocks said:**
> The results are:
```
deb http://archive.ubuntu.com/ubuntu hardy main restricted
deb http://archive.ubuntu.com/ubuntu hardy-updates main restricted
deb http://security.ubuntu.com/ubuntu/ hardy-security main restricted

```

I don't see universe in there.

add these to /etc/apt/sources.list (or uncomment them)
```

deb http://archive.ubuntu.com/ubuntu hardy universe restricted
deb http://archive.ubuntu.com/ubuntu hardy-updates universe restricted
deb http://archive.ubuntu.com/ubuntu hardy-security universe restricted

```

then
```

sudo apt-get update
sudo apt-get install asterisk

```

---

### Post by boondocks on 2009-11-05
Thank you, cdenley.

That helped.

---

