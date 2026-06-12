---
title: "Python-Twisted experts on Ubuntu 10.04 needed"
date: 2010-06-22
forum: Server Platforms
---

### Post by yaddoshi on 2010-06-22
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

### Post by koenn on 2010-06-22
> **yaddoshi said:**
> 
This problem has been confirmed on the Google Code issues page for this program on Ubuntu 10.04 LTS: [http://code.google.com/p/flashpolicytwistd/issues/detail?id=1]("http://code.google.com/p/flashpolicytwistd/issues/detail?id=1")

so what is your question ?

---

### Post by yaddoshi on 2010-06-22
> **koenn said:**
> so what is your question ?

Is there a way to generate some sort of error message (or is there a log file I am unaware of that is already being generated) by either python-twisted or flashpolicytwistd so that I might have some idea as to what is failing?

Unfortunately this particular application has nothing in the way of support documents, and my understanding of python is limited to the praise heaped upon it by XKCD.com - so any ideas as to how I could troubleshoot this would be great.

Thanks!

---

### Post by koenn on 2010-06-22
If it's a know bug, logging it isn't going to help much, you'd need a newer version where the bug is fixed, I'd think.



Other than that :

I'd expect that a service either logs to syslog, or a dedicated log in /var/log  - have you check *all* likely candidates ?

If you have the source code of this app, you might be able to see where it logs to, if it logs at all.


You might also be able to add logging to it;
both python and twisted seem to have something to handle that:
[http://twistedmatrix.com/documents/current/core/howto/logging.html](http://twistedmatrix.com/documents/current/core/howto/logging.html)
[http://docs.python.org/library/logging.html](http://docs.python.org/library/logging.html)
[http://www.mechanicalcat.net/richard/log/Python/Simple_usage_of_Python_s_logging_module](http://www.mechanicalcat.net/richard/log/Python/Simple_usage_of_Python_s_logging_module)

At this point, you're probably better of in the Programming forum

---

