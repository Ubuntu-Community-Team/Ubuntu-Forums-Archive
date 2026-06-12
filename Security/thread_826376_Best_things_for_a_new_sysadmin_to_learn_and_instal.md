---
title: "Best things for a new sysadmin to learn and install"
date: 2008-06-11
forum: Security
---

### Post by borahshadow on 2008-06-11
As discussed in [this thread]("http://ubuntuforums.org/showthread.php?p=5163187#post5163187") I will probably be running a local only samba server and public webserver. What are the most important things to learn and install for security.

In my current local only samba server has clamav scan every night and email me the results. Also lm-sensors sends me temp info. I realize I probably need to learn what a normal log looks like and have something like logwatch but I currently know nothing about it.

Is my DSL/router enough of a firewall?

Do I need a rootkit hunter? if so I know nothing about them and would appreciate some insight on how to use them.

How can I have apt-get or something run every night to notify me about updates but not install them?

Anything else I need to know/learn/install?

Also I don't know but if you can guess but, how much traffic will a hobby site, for friends and family, hosting a photo album and wordpress be looking at? will it tax my ~ 720 kb/s upload DSL? I would guess at most 1 hit a day but obviously much more when I first tell people about it.

---

### Post by molotov00 on 2008-06-11
Ubuntu comes with a firewall, iptables. There are frontends that make editing it easier, the most popular being firestarter.

Install and love ssh: sudo apt-get install openssh-server
You can connect from a linux box with just "ssh servername" and from a windows box with a client called Putty. If you forward port 22 for ssh, which I do, make your password good but also install fail2ban, which blocks an IP after 6 failed login attempts by default.

There is a way to do automatic updates. I don't know it.

---

### Post by borahshadow on 2008-06-12
Does ip tables need any extra configuration from me or does it automatically block all ports that an application has not opened? and what about command line iptables config programs?

Thanks about ssh I actually have used it before but I didn't know about fail2ban.

---

### Post by llebegue on 2008-06-12
In order to have apt-get run nightly without update and giving yu information about possible changes you need some cron task such as :

```
00 03 * * * /usr/bin/apt-get update && apt-get autoclean &&  /usr/bin/apt-get -q -d -y -u upgrade
``` 

you can add this cron task with

```
sudo crontab -e
```

The result will be sent to root@yourhostname. You need to have a mailing gateway installed and configured. Mine is postfix. Make sure that (If that is your will) only your host can send emails but no spammers can use it to send emails. To do this I commented out a line in /etc/postfix/master.cf

```
sudo vi /etc/postfix/master.cf
```

and comment this line :

```
smtp      inet  n       -       -       -       -       smtpd
```

and verify that this line exists in the same /etc/postfix/master.cf file

```
127.0.0.1:smtp      inet  n       -       n       -       -       smtpd
```

restart postfix

```
 sudo /etc/init.d/postfix restart
```

according to your needs you may have to tweak /etc/postfix/main.cf

---

### Post by llebegue on 2008-06-12
> **borahshadow said:**
> Does ip tables need any extra configuration from me or does it automatically block all ports that an application has not opened?

By default iptables blocks nothing has ubuntu distribution has no open ports by default as well.

---

### Post by borahshadow on 2008-06-12
Great thanks everybody. Anybody else have any tips? or answers to any of my other questions?

---

### Post by FakeOutdoorsman on 2008-06-12
The Tome of Security, +3 against hackers, summons dogs that bark and shoots bees out of their muzzles when they bark:
[Securing Debian Manual]("http://www.debian.org/doc/manuals/securing-debian-howto/").

---

