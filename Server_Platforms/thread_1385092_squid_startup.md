---
title: "squid startup"
date: 2010-01-19
forum: Server Platforms
---

### Post by cong06 on 2010-01-19
I installed squid on my machine, and for a while it was starting up automatically when the computer would turn on, and I would only have to reconfigure on ip-up for the new dns, etc.

Now for some reason, I notice that squid isn't even started.

To fix  this, I wrote a start up script in /etc/rcS.d/ that runs:
/etc/init.d/squid3 start

And I notice it still isn't starting.
So I write "/etc/init.d/squid3 start" and put it in my ip-up.d/ script.
Everything in the script is being executed, but the squid server.

I've tried reinstalling squid... what am I missing? where does the computer start these services? Why isn't the commandline start working in my scripts?

---

### Post by Lars Noodén on 2010-01-19
There is a startup script in /etc/init.d/ that should be symlinked in the directory (e.g. /etc/init.d/rc2.d) appropriate to the runlevel you are using.

It should have happened automatically when you installed squid.

Here is an explanation of runlevels:

[http://www.debianadmin.com/debian-and-ubuntu-linux-run-levels.html](http://www.debianadmin.com/debian-and-ubuntu-linux-run-levels.html)

---

### Post by cong06 on 2010-01-20
Yeah, some confusion on run-levels. For some reason I thought "S" meant start up, but instead it's like "change level".

In anycase, shouldn't:
```

update-rc.d squid3 default

```
do it? (to start squid I run /etc/init.d/squid3 start) That's what the webpage says, but when I run it, I get the output:
```

usage: update-rc.d [-n] [-f] <basename> remove
       update-rc.d [-n] <basename> defaults [NN | SS KK]
       update-rc.d [-n] <basename> start|stop NN runlvl [runlvl] [...] .
                -n: not really
                -f: force

```
Which seems to suggest that I put it in the wrong format.

When I initially installed squid it was working fine, but I'm not even sure what happened anymore. It just stopped starting.

I just ran:
```

root@ubuntu1:/etc# find . -name "*squid3" -exec ls -al {} \;
-rwxr-xr-x 1 root root 90 2009-02-12 12:26 ./resolvconf.d/update-libc.d/squid3
lrwxrwxrwx 1 root root 16 2009-10-17 13:11 ./rc1.d/K30squid3 -> ../init.d/squid3
lrwxrwxrwx 1 root root 16 2009-10-17 13:11 ./rc0.d/K30squid3 -> ../init.d/squid3
total 192
drwxr-xr-x   2 proxy proxy   4096 2010-01-16 13:23 .
drwxr-xr-x 154 root  root   12288 2010-01-20 10:48 ..
-rw-r--r--   1 proxy proxy    421 2009-02-12 12:26 msntauth.conf
-rw-r--r--   1 root  root  161749 2010-01-13 18:05 squid.conf
-rw-r--r--   1 root  root    1726 2010-01-13 17:38 squidGuard.conf
-rw-r--r--   1 proxy proxy   1321 2009-10-27 10:49 squidGuard.conf~
lrwxrwxrwx 1 root root 16 2009-10-17 13:11 ./rc4.d/S30squid3 -> ../init.d/squid3
lrwxrwxrwx 1 root root 16 2009-10-17 13:11 ./rc5.d/S30squid3 -> ../init.d/squid3
lrwxrwxrwx 1 root root 16 2009-10-17 13:11 ./rc2.d/S30squid3 -> ../init.d/squid3
lrwxrwxrwx 1 root root 16 2009-10-17 13:11 ./rc6.d/K30squid3 -> ../init.d/squid3
lrwxrwxrwx 1 root root 16 2009-10-17 13:11 ./rc3.d/S30squid3 -> ../init.d/squid3
-rwxr-xr-x 1 root root 2942 2009-02-12 12:26 ./init.d/squid3
-rw-r--r-- 1 root root 226 2009-02-12 12:26 ./logrotate.d/squid3

```
So it looks like the links are already set up correctly since each folder has a (S|K)30squid3 which points to init.d/squid3

---

### Post by cong06 on 2010-01-23
I noticed what the problem is, but I'm not quite sure what to do about it:
In my squid.conf file I had put:
```

acl ubuntu_repo_A dst ke.archive.ubuntu.com
acl ubuntu_repo_B dst archive.ubuntu.com
acl ubuntu_repo_C dst security.ubuntu.com
acl ubuntu_repo_D dst archive.canonical.com
cache deny ubuntu_repo_A
cache deny ubuntu_repo_B
cache deny ubuntu_repo_C
cache deny ubuntu_repo_D

```
But this means that when squid starts up it needs Internet in order to tag those domains.
Ok, so as long as I start squid on IP-up, it should be fine, right? Starting it when the computer turns on would be better, but that would only work if I hard-coded the domains in, and I'm not sure I want to do that.

So, I put in in ip-up.d/
But it still fails, and my guess is because the user who controls ppp doesn't have access to start squid.

Any brilliant ideas? I don't really want to mess around with users... I could add IP addresses so it doesn't need Internet for the repositories, but that's not as flexible.

---

### Post by cong06 on 2010-02-17
The correct 'acl' is "dstdomain"

---

