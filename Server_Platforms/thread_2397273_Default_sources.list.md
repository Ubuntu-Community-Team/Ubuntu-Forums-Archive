---
title: "Default sources.list"
date: 2018-07-27
forum: Server Platforms
---

### Post by sshaikh on 2018-07-27
I've reinstalled Ubuntu Server 18.04 three times now but the contents of the sources.list is always as follows:

```

$ cat /etc/apt/sources.list
deb http://archive.ubuntu.com/ubuntu bionic main
deb http://archive.ubuntu.com/ubuntu bionic-security main
deb http://archive.ubuntu.com/ubuntu bionic-updates main

```

This seems unusual, not least because it doesn't allow much to be installed by default. Is this typical with the Server edition? My concern is that if not there may be other things broken with the install.

---

### Post by sshaikh on 2018-07-27
According to this page: [https://help.ubuntu.com/lts/serverguide/configuration.html.en](https://help.ubuntu.com/lts/serverguide/configuration.html.en) we should expect more entries in sources.list:

```

deb http://archive.ubuntu.com/ubuntu bionic universe multiverse
deb-src http://archive.ubuntu.com/ubuntu bionic universe multiverse

deb http://us.archive.ubuntu.com/ubuntu/ bionic universe
deb-src http://us.archive.ubuntu.com/ubuntu/ bionic universe
deb http://us.archive.ubuntu.com/ubuntu/ bionic-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ bionic-updates universe

deb http://us.archive.ubuntu.com/ubuntu/ bionic multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ bionic multiverse
deb http://us.archive.ubuntu.com/ubuntu/ bionic-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ bionic-updates multiverse

deb http://security.ubuntu.com/ubuntu bionic-security universe
deb-src http://security.ubuntu.com/ubuntu bionic-security universe
deb http://security.ubuntu.com/ubuntu bionic-security multiverse
deb-src http://security.ubuntu.com/ubuntu bionic-security multiverse

```

---

### Post by sshaikh on 2018-07-27
It appears the default iso from the server download page is a "live" version which does not have universe and multiverse enabled.

Using the alternative server installer iso has given me a system with the complete list of sources.

---

### Post by kinghat on 2018-08-31
> **sshaikh said:**
> It appears the default iso from the server download page is a "live" version which does not have universe and multiverse enabled.

Using the alternative server installer iso has given me a system with the complete list of sources.
can you post that exact list of sources for me? what comes as default?

---

