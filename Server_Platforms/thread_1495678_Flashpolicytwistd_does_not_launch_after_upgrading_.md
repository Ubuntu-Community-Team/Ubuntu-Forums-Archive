---
title: "Flashpolicytwistd does not launch after upgrading to Ubuntu Server 10.04"
date: 2010-05-28
forum: Server Platforms
---

### Post by yaddoshi on 2010-05-28
I was running Ubuntu Server 8.04 LTS and using [flashpolicytwistd]("http://code.google.com/p/flashpolicytwistd/") from Google Code to support flash-based telnet on two websites.  After upgrading to 10.04 flashpolicytwistd no longer starts.

If I do the following to manually start flashpolicytwistd:
```
$ sudo /etc/init.d/flashpolicytwistd start
```
I get this response:
```
Starting flashpolicytwistd
flashpolicytwistd started
```

If I then immediately do the following:
```
$ sudo /etc/init.d/flashpolicytwistd stop
```
I get this response:
```
/sbin/start-stop-daemon: warning: failed to kill 24902: No such process
```

I also cannot locate the process with ps -e, nor can I confirm that it is listening on its assigned port (default is 843, I changed it to 4005).

No errors show up in the logs.  I also tried uninstalling and reinstalling with no change.

This problem has been confirmed on the Google Code issues page for this program on Ubuntu 10.04 LTS: [http://code.google.com/p/flashpolicytwistd/issues/detail?id=1]("http://code.google.com/p/flashpolicytwistd/issues/detail?id=1")

---

### Post by yaddoshi on 2010-06-22
Reposted here: [http://ubuntuforums.org/showthread.php?t=1515559](http://ubuntuforums.org/showthread.php?t=1515559)

---

### Post by BobVila on 2010-06-22
Why is this doubleposted? The problem is confirmed on the Google Code page... not much to do without rewriting it.

---

### Post by lisati on 2010-06-22
Thread closed. If you need to find your posts, click on Serach->Find all your posts.

---

