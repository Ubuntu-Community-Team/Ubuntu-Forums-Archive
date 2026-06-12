---
title: "Local repository using pt-mirror"
date: 2013-05-20
forum: Server Platforms
---

### Post by chrisguk on 2013-05-20
I have install apt-mirror with an attempt to make a local repo.  I have a step by step guide to use but I have come unstuck at this stage:

```


$ sudo su apt-mirror
$ apt-mirror


```
```


apt-mirror: invalid line in config file (1: k############################################################# ...) at /usr/bin/apt-mirror line 213, <CONFIG> line 1.


```

This is what is present on line 1 pf the apt-mirror config file:

```


#!/usr/bin/perl -w


```

I cant seem to find the answer anywhere.  Any ideas?

---

### Post by lykwydchykyn on 2013-05-20
When you say "apt-mirror config file", which file is it?  The configuration file for apt-mirror is /etc/apt/mirror.list, and it should not be a perl file.

---

### Post by chrisguk on 2013-05-20
Its this perl file:


/usr/bin/apt-mirror

The mirror.list file is a type of config file I agree.  The perl script above is the initiation file for apt-mirror

---

### Post by chrisguk on 2013-05-20
Its okay im such a nutter lol.  I found the error.  There was a character out of place in the mirror.list.

Thanks for checking in ;)

---

