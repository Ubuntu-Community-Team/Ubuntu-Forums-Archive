---
title: "System Information upon login"
date: 2012-08-02
forum: Server Platforms
---

### Post by discorsage on 2012-08-02
How is the system information displayed upon login in Ubuntu Server 12.04?

I ask for two reasons :

1) I'd just like to know what program this is

2) I have upgraded a 10.04 machine to 12.04 recently, using do-release-upgrade, and this server does not show system information upon login.  I would like to fix that.

---

### Post by Loki57701 on 2012-08-02
I think this is part of the landscape-common package.

(Must be run with sudo or as root)

You can disable this by running:
```

dpkg-reconfigure landscape-common

```

Chose the option to not display system information.

Also, if you don't want all that other stuff showing up when you login:

```

unlink /etc/motd
echo "" > /etc/motd
echo "" > /var/run/motd

```

That should clear up everything. Then you can add you own message into /etc/motd.

You'll have to log out and log back in to see the results.

Hope this helps.

---

### Post by discorsage on 2012-08-02
Actually I was in the middle of signing up for a trial landscape thing and so I happened to install the landscape packages.

Thank you!

---

### Post by d4m1r on 2012-08-02
Not sure what 12.04 displays when logging in but here's what 11.10 does and I'd guess it isn't very different:

Welcome to Ubuntu 11.10 (GNU/Linux 3.0.0-12-generic-pae i686)

 * Documentation:  [https://help.ubuntu.com/](https://help.ubuntu.com/)

  System information as of Thu Aug  2 19:16:59 EDT 2012

  System load:  0.0               Processes:           64
  Usage of /:   8.3% of 35.96GB   Users logged in:     0
  Memory usage: 11%               IP address for eth0: xxxx
  Swap usage:   1%

  Graph this data and manage this system at [https://landscape.canonical.com/](https://landscape.canonical.com/)
New release '12.04 LTS' available.
Run 'do-release-upgrade' to upgrade to it.

Last login: Thu Aug  2 18:29:51 2012 from 192.168.1.102

---

### Post by Loki57701 on 2012-08-02
Hey, I forgot to mention, when you unlink /etc/motd, you are removing the soft link (shortcut) to /var/run/motd, so if you want to have a message of the day you will need to re-create /etc/motd as an actual file and not just a link. (touch /etc/motd)

also, I'm pretty sure the landscape package comes pre-installed on all ubuntu releases.

---

