---
title: "User Permissions Integration with Nautilus &amp; Other File Managers"
date: 2012-03-04
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by 0011235813 on 2012-03-04
I've read several posts in this forum where the user has asked help in opening certain files or directories that, for one reason or another, end up belonging to root. This often confuses new users as they don't understand why they can't open some of their own folders, and as the current system of doing things (chown and gksu) are quite unintuitive and difficult.

I think that in nautilus, right clicking something should also give you the option to change it's permissions and open it as root (by authentication of course). Same with sh scripts, there should be a "run" and a "run as root" function.

Additionally, I'd like to see some "encrypt this" options (with password or a preconfigured file key) in the right hand menu, and maybe a "move to cryptkeeper EncFS folder" option as well (I think utilities like cryptkeeper and KeePass should come pre-installed). I'd also love to see browsers integrate with them, like "fetch password from .kdbx database" or "where to store cookies and history: -Cryptkeeper file folder" type thing.

Thanks.

---

### Post by grahammechanical on 2012-03-04
I have considered all of your suggestions and I reject them. I spent all of 2 seconds considering your ideas.

What else do you expect? This forum is not the place for making suggestions to improving Ubuntu. 

This section of the forum is for those who are sharing in testing the next release of Ubuntu that is under development. You should remember that decisions regarding what goes into each release are made months and months in advance. The soon to be released 12.04 is implementing design decisions that have long been made. 

And this forum was not involved in making those decisions.

If you have what you think is a bright idea then go here:

[http://brainstorm.ubuntu.com/]("http://brainstorm.ubuntu.com/")

---

### Post by 0011235813 on 2012-03-04
> **grahammechanical said:**
> I have considered all of your suggestions and I reject them. I spent all of 2 seconds considering your ideas.

What else do you expect? This forum is not the place for making suggestions to improving Ubuntu. 

This section of the forum is for those who are sharing in testing the next release of Ubuntu that is under development. You should remember that decisions regarding what goes into each release are made months and months in advance. The soon to be released 12.04 is implementing design decisions that have long been made. 

And this forum was not involved in making those decisions.

If you have what you think is a bright idea then go here:

[http://brainstorm.ubuntu.com/]("http://brainstorm.ubuntu.com/")
I wasn't aware of the link previously, but now I've bookmarked it and hope to look there. 

But anyway, thanks for your kind and considerate reply :)

---

### Post by x-shaney-x on 2012-03-04
Much of what you want may well be available (if not by default).

There are several nautilus context extensions in the repos and many more nautilus scripts dotted around the net.

---

### Post by 0011235813 on 2012-03-04
> **x-shaney-x said:**
> Much of what you want may well be available (if not by default).

There are several nautilus context extensions in the repos and many more nautilus scripts dotted around the net.

I've played around with nautilus-utils, but I always found installation tricky and a lot of bugs.

---

### Post by mc4man on 2012-03-04
> **0011235813 said:**
> I've played around with nautilus-utils, but I always found installation tricky and a lot of bugs.

pretty much all you mentioned are here, initiated from r. click thru python-nautilus extensions

The ppa is heavily maintained & any issues are dealt with promptly

[https://launchpad.net/~nae-team/+archive/ppa](https://launchpad.net/~nae-team/+archive/ppa)

or a bit forward

[https://launchpad.net/~nae-team/+archive/daily](https://launchpad.net/~nae-team/+archive/daily)

actions can be installed as a select group, (nautilus-actions-extra), and or individually

---

