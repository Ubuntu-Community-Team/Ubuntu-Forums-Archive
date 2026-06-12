---
title: "Blocklisting an ubuntu update server"
date: 2023-02-02
forum: Server Platforms
---

### Post by DigiAngel on 2023-02-02
Topic.  kazooie.canonical.com is terribly slow..is there a way I can prevent my server or workstation from trying to get updates from it?  Thank you.

---

### Post by Frogs Hair on 2023-02-02
Support request, moved to Server Platforms.

---

### Post by ajgreeny on 2023-02-02
The only reference I can find about this suggests it could be VPN related.
Are you using a vpn?
See [https://ubuntuforums.org/showthread.php?t=2453995](https://ubuntuforums.org/showthread.php?t=2453995) which may help.  Good luck!

---

### Post by LHammonds on 2023-02-06
You are talking about "apt update" command?

That is controlled by the /etc/apt/sources.list file...or files under /etc/apt/sources.list.d/*

More info about it can be found here: [https://ubuntu.com/server/docs/package-management](https://ubuntu.com/server/docs/package-management)

I am located in the US and this is the contents of my Ubuntu Server 20.04.5 LTS file (without including the comments):
```

deb http://us.archive.ubuntu.com/ubuntu/ focal main restricted
deb http://us.archive.ubuntu.com/ubuntu/ focal-updates main restricted
deb http://us.archive.ubuntu.com/ubuntu/ focal universe
deb http://us.archive.ubuntu.com/ubuntu/ focal-updates universe
deb http://us.archive.ubuntu.com/ubuntu/ focal multiverse
deb http://us.archive.ubuntu.com/ubuntu/ focal-updates multiverse
deb http://us.archive.ubuntu.com/ubuntu/ focal-backports main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu focal-security main restricted
deb http://security.ubuntu.com/ubuntu focal-security universe
deb http://security.ubuntu.com/ubuntu focal-security multiverse

```

Here is the contents of my Ubuntu Server 22.04.1 LTS file (without including the comments):
```

deb http://archive.ubuntu.com/ubuntu jammy main restricted
deb http://archive.ubuntu.com/ubuntu jammy-updates main restricted
deb http://archive.ubuntu.com/ubuntu jammy universe
deb http://archive.ubuntu.com/ubuntu jammy-updates universe
deb http://archive.ubuntu.com/ubuntu jammy multiverse
deb http://archive.ubuntu.com/ubuntu jammy-updates multiverse
deb http://archive.ubuntu.com/ubuntu jammy-backports main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu jammy-security main restricted
deb http://archive.ubuntu.com/ubuntu jammy-security universe
deb http://archive.ubuntu.com/ubuntu jammy-security multiverse

```

---

