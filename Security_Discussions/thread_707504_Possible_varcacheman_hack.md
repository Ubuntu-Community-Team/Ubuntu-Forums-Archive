---
title: "Possible var/cache/man hack?"
date: 2008-02-25
forum: Security Discussions
---

### Post by aev on 2008-02-25
Hi,

our server running SUSE plus few linux boxes (some of them Ubuntu) got hacked into. I cant give away the files , but it seams like someone created additional groups and there were traces in the index.db files located in

/var/cache/man directory.

Also

>cat /etc/passwd

and 

>cat /etc/group 

showed some activity by unknown users - additional groups, etc.

Anyone with an idea what that is and is it a known thing?

May be one could look here:

[http://www.howtoforge.com/forums/showthread.php?t=18806]("http://www.howtoforge.com/forums/showthread.php?t=18806")

---

### Post by wirelessmonkey on 2008-02-25
There are no details for your situation.... How can we provide assistance?

---

### Post by aev on 2008-02-26
we have no idea what and how has happened. Otherwise I would have provided some info. :confused:

Nothing on my machine though :)

pp: apparently there was a new account created called GAMES with keys to other machines ???

Just asking - if people know, if not - we will figure it out.

---

### Post by wirelessmonkey on 2008-02-26
Is your system running any of the vmsplice vulnerable kernels?

---

