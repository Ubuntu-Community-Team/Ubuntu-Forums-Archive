---
title: "Read somewhere that I should disable login shells for most users -Ubuntu Server 11.04"
date: 2011-09-14
forum: Security
---

### Post by bvz on 2011-09-14
Hi there, I was reading this site (along with others):

[http://linuxadminzone.com/5-steps-to-secure-your-linux-server/](http://linuxadminzone.com/5-steps-to-secure-your-linux-server/)

and it recommended that I remove the login shell from all other users except wheel user.

When I list all of my users (cat /etc/passwd) I see that I have a lot of automatically generated users.  Most of them have a login shell (I think) of /bin/sh

These are users such as syslog, sshd, mail, games, etc.

There is also a user called sync who has a login of /bin/sync


Should I be resetting their login shells to be /usr/sbin/nologin?

Would that break things?


Sorry for the basic level of this question, I am still new to the server scene (but learning fast)

Thanks

---

### Post by Ibidem on 2011-09-16
Daemons get started by root, then they change UID.  This does not involve login shells.
Some programs are started by root via su <username> -c <command>.
This also does not involve login shells.
So I would recommend trying it with a few accounts and testing. It probably won't break things, but I'd try with (for example) mail, test whether the mail subsystem is working, and if it is, apply it to the other accounts.
sulogin and sshd would be the two I wouldn't try at first.

---

### Post by bvz on 2011-09-16
Thanks for the info.

Makes sense.  I am going to start removing login access to some of these accounts.  I'm pretty sure that nothing is going to break if I remove login access for, say, games.

---

