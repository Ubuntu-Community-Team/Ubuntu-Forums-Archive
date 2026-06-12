---
title: "denyhosts errors"
date: 2010-05-19
forum: Security
---

### Post by quacked on 2010-05-19
Having had denyhosts, on 9.10 ,,, after upgrade , denhosts, quit working, the errors in the denyhosts logs always show the same thing 

>  Traceback (most recent call last):
  File "/usr/share/denyhosts/DenyHosts/sync.py", line 117, in receive_new_hosts
    self.__prefs.get("SYNC_DOWNLOAD_RESILIENCY"))
  File "/usr/lib/python2.6/xmlrpclib.py", line 1199, in __call__
    return self.__send(self.__name, args)
  File "/usr/lib/python2.6/xmlrpclib.py", line 1483, in __request
    allow_none=self.__allow_none)
  File "/usr/lib/python2.6/xmlrpclib.py", line 1132, in dumps
    data = m.dumps(params)
  File "/usr/lib/python2.6/xmlrpclib.py", line 677, in dumps
    dump(v, write)
  File "/usr/lib/python2.6/xmlrpclib.py", line 699, in __dump
    f(self, value, write)
  File "/usr/lib/python2.6/xmlrpclib.py", line 725, in dump_long
    raise OverflowError, "long int exceeds XML-RPC limits"
OverflowError: long int exceeds XML-RPC limits

Anyone know how I may fix this

---

### Post by teh_drizzle on 2010-05-19
I've not seen this error, but maybe editing the /etc/denyhosts.conf file and setting SYNC_DOWNLOAD_RESILIENCY to an integer will resolve the problem?

Do you have SYNC_DOWNLOAD_RESILIENCY set in the config?

---

### Post by bodhi.zazen on 2010-05-19
> **quacked said:**
> Having had denyhosts, on 9.10 ,,, after upgrade , denhosts, quit working, the errors in the denyhosts logs always show the same thing 

Anyone know how I may fix this

Try disabling syncronization mode:

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=546772](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=546772)

---

### Post by quacked on 2010-05-19
Thanks for the replies,,, and the link to the bug report,, will try several things to see if they work,,, Would rather have it working in synchronization mode, for the  advantages,,, Again,, thanks to all,,,

---

### Post by bodhi.zazen on 2010-05-19
> **quacked said:**
> Would rather have it working in synchronization mode, for the  advantages

What advantages would that be ? denyhosts works fine w/o synchronization and you can manage problematic IP by editing the config file.

Denyhosts will block problematic IP fast enough, and ip are easy enough to obtain or forge.

---

### Post by dholbert on 2010-09-28
There's a launchpad bug filed on this:
[https://bugs.launchpad.net/ubuntu/+source/denyhosts/+bug/564476](https://bugs.launchpad.net/ubuntu/+source/denyhosts/+bug/564476)

with a workaround included:
[https://bugs.launchpad.net/ubuntu/+source/denyhosts/+bug/564476/comments/3](https://bugs.launchpad.net/ubuntu/+source/denyhosts/+bug/564476/comments/3)

To get the current unix time (for the first step of the workaround), you can use the command:
```
date "+%s"
```

---

