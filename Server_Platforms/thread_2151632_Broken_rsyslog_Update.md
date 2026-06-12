---
title: "Broken rsyslog Update?"
date: 2013-06-05
forum: Server Platforms
---

### Post by JSeymour on 2013-06-05
Ubuntu 12.04 LTS 

$ uname -a
Linux www 3.2.0-45-generic-pae #70-Ubuntu SMP Wed May 29 20:31:05 UTC 2013 i686 i686 i386 GNU/Linux

Trying to apply the latest updates, and get...

Setting up rsyslog (5.8.6-1ubuntu8.3) ...
Skipping profile in /etc/apparmor.d/disable: usr.sbin.rsyslogd

and there it hangs indefinitely.

Ever since this, earlier this morning, rsyslogd does not appear to be working properly any more.  I'm getting nothing in many of my log files any more.

Jim

---

### Post by JSeymour on 2013-06-05
Have tried removing the rsyslog package so I can reinstall it.  Can't, because it also wants to remove ubuntu-minimal.  Have tried --reinstall.  No go: Hangs the same way.

---

### Post by SeijiSensei on 2013-06-05
How about "sudo apt-get -f install" with no packages?

---

### Post by JSeymour on 2013-06-05
This cannot be good:

```

$ /usr/sbin/rsyslogd -d

5520.517325027:b77416c0: rsyslogd 5.8.6 startup, compatibility mode 0, module path '', cwd:/etc/init.d
5520.517814681:b77416c0: caller requested object 'net', not found (iRet -3003)
5520.517972863:b77416c0: Requested to load module 'lmnet'
5520.518087006:b77416c0: loading module '/usr/lib/rsyslog/lmnet.so'
5520.518606883:b77416c0: module of type 2 being loaded.
5520.518712532:b77416c0: entry point 'isCompatibleWithFeature' not present in module
5520.518808030:b77416c0: source file conf.c requested reference for module 'lmnet', reference count now 1
5520.518956274:b77416c0: rsyslog runtime initialized, version 5.8.6, current users 1
5520.519161483:b77416c0: source file syslogd.c requested reference for module 'lmnet', reference count now 2
*** glibc detected *** /usr/sbin/rsyslogd: malloc(): memory corruption: 0x09eddad8 ***

```

How can I get back to a **working** rsyslogd?

Thanks,
Jim

---

### Post by JSeymour on 2013-06-05
I don't think that's going to address the problem.

I think it's hanging because rsyslog no longer starts/stops properly.  For example:

```

./rsyslog start
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service rsyslog start

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the start(8) utility, e.g. start rsyslog

```

And there it sits.  Forever.  Yet...

```

$ ps -ef |grep rsyslog
root      6183     1  0 08:38 ?        00:00:00 rsyslogd -c5
root      6193  2847  0 08:39 pts/1    00:00:00 grep rsyslog

```

Trying to stop it fails to stop it.   That just hangs forever, too.

Jim

---

### Post by mjmckinnon on 2013-06-05
I've had the exact same thing happen to me just now.  It has just hung and I'd love to know what to do next?

```

..
Setting up rsyslog (5.8.6-1ubuntu8.3) ...
Skipping profile in /etc/apparmor.d/disable: usr.sbin.rsyslogd
rsyslog stop/waiting

```

```

24732 pts/0    S+     0:00  |                   \_ apt-get upgrade
30835 pts/1    Ss+    0:00  |                       \_ /usr/bin/dpkg --status-fd 39 --configure libc-dev-bin:i386 linux-libc-dev:i386 libc6-dev:i386 libssl-doc
31295 pts/1    S+     0:00  |                           \_ /bin/sh /var/lib/dpkg/info/rsyslog.postinst configure 5.8.6-1ubuntu8.1
31512 pts/1    S+     0:00  |                               \_ /bin/sh /usr/sbin/invoke-rc.d rsyslog restart
31536 pts/1    S+     0:00  |                                   \_ /bin/sh -e /etc/init.d/rsyslog restart
31570 pts/1    S+     0:00  |                                       \_ start rsyslog

```

Tail of syslog reveals this and then nothing since.

```

Jun  5 22:47:28 hostname kernel: Kernel logging (proc) stopped.
Jun  5 22:47:28 hostname rsyslogd: [origin software="rsyslogd" swVersion="5.8.6" x-pid="719" x-info="http://www.rsyslog.com"] exiting on signal 15.

```

---

### Post by Toz on 2013-06-05
Have a look at [this bug report]("https://bugs.launchpad.net/ubuntu/+source/rsyslog/+bug/1187654").

Workaround suggested is to manually kill the rsyslog process during the upgrade. Something like "sudo killall -9 rsyslogd" should work.

---

### Post by mjmckinnon on 2013-06-05
That was exactly what I needed, thanks so much.  It worked a treat. :p

---

### Post by JSeymour on 2013-06-05
Thanks for the pointer, Toz.  That allowed the upgrade to succeed, but I'm still missing most of my logging.  In fact: The only logging I'm getting is Apache.  Nothing new in syslog.  Nothing new in mail.*.

Jim

---

### Post by JSeymour on 2013-06-05
[https://bugs.launchpad.net/ubuntu/+source/rsyslog/+bug/1187820](https://bugs.launchpad.net/ubuntu/+source/rsyslog/+bug/1187820)

---

### Post by 20111161 on 2013-06-06
> **toz said:**
> have a look at [this bug report]("https://bugs.launchpad.net/ubuntu/+source/rsyslog/+bug/1187654").

Workaround suggested is to manually kill the rsyslog process during the upgrade. Something like "sudo killall -9 rsyslogd" should work.

thank you. It worked  like a charm :p

---

### Post by bruce421116 on 2013-06-06
Thank you!I just had the same problem.

---

