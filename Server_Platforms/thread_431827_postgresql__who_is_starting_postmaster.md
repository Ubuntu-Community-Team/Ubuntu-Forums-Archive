---
title: "postgresql:  who is starting postmaster?"
date: 2007-05-03
forum: Server Platforms
---

### Post by zedmaster on 2007-05-03
I have been configuring postgresql 8.1 on my Ubuntu Feisty box.  It's AMD64, and I used the standard postgresql-8.1 package that's available in the Ubuntu repositories.  I've successfully created my cluster and database.  The problem is that postmaster is always started when I boot up.  I'd like to set it to run under the postgres user, but for the life of me, I cannot figure out WHAT is starting the postmaster!  I've checked a few possible suspects, like etc/rc.local. 

Can somebody point this poor lost soul in the right direction?

Matt

PS:  In general, is there an easy way to determine what started a process?

---

### Post by chriscando on 2007-05-03
You can view who/what started a process by:
```
ps -aux
```

Im not sure how to prevent it from starting (maybe somewhere in /etc/inid.d ??) but an ugly fix would be just to kill the process and start it up from user postgres.

---

### Post by kaamos on 2007-05-03
Postgresql runs as the user postgres already. The daemon is started at boot with a script in /etc/rc***X***.d that is linked to /etc/init.d/postgresql-*VERSION*.

---

### Post by garba on 2007-05-03
all i know is the postmaster executable in debian is wrapped by such an abysmal amount of cascaded scripts that i eventually decided to override them all and start it directly from rc.local, there's nothing i hate more than debian's init scripts policies and their automate everything attitude

---

