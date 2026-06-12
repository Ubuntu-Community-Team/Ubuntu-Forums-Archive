---
title: "Enabling Shadow Passwords???"
date: 2006-09-02
forum: Server Platforms
---

### Post by unraveled on 2006-09-02
Hey all, I'm new to Ubuntu but I've heard good things about it so I thought that I'd give it a try.

So here's my problem - I just installed Ubuntu dapper via debootstrap (running as a xen domU) and during the install process I noticed a lot of packages complained about a missing shadow file. Sure enough there's no /etc/shadow and my passwords are being stored in /etc/passwd. 

So how do I set up Ubuntu to use shadow passwords? I normally use Debian for my domU's and it seems to use shadow passwords without any configuration. Sorry if I'm missing something that's well known in the Ubuntu community, but my attempts to finding good documentation for installing Ubuntu via debootstrap had come up nil.

Thanks,
Brent

---

### Post by skymt on 2006-09-02
Shadow passwords are the default, I don't know how your install messed that up. Anyway try 'sudo shadowconfig on'. If that doesn't work, post back.

---

### Post by unraveled on 2006-09-02
Bingo, that fixed it. Thanks a lot!

-Brent

---

### Post by quentinsf on 2006-10-12
I had exactly the same question - debootstrap-ing under Xen - and needed just the same answer.  So thanks, both!

My dom0 is Fedora core 5, so I needed to get debootstrap running under that to start with. I found a hint somewhare that you can [download the .deb file]("http://archive.ubuntulinux.org/ubuntu/pool/main/d/debootstrap/") and convert it to an RPM using [Alien]("http://kitenet.net/~joey/code/alien.html").

You're right that docs for this are hard to come by. After debootstrapping, and configuring the interfaces, I used:
```

ifup eth0
apt-get update
apt-get install ubuntu-base
apt-get upgrade
shadowconfig on

```
and for my own typical web-server setup:
```

apt-get install apache2 mysql-client mysql-server php5 phpmyadmin
apt-get install jed emacs-nox subversion openssh-server

```
after which you mustn't forget to set a MySQL root password.

Just in case anyone else is searching...

---

