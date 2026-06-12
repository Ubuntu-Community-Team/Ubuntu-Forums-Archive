---
title: "Upgrade 6.06 to 6.10, some issue arose"
date: 2007-07-18
forum: Server Platforms
---

### Post by Royel on 2007-07-18
Hi Ubuntu, 

I upgraded a server machine to 6.10 from 6.06 today, I guess I should consider myself fairly lucky that almost all went well with this one exception, below is a snippet of the problem.
If anyone can tell me what steps to take to resolve this, I'd greatly appreciate it.

[http://pastebin.com/m35509d96](http://pastebin.com/m35509d96)

```
root@pengserv:~ # apt-get -f install
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  courier-authdaemon courier-authlib
The following NEW packages will be installed:
  courier-authlib
The following packages will be upgraded:
  courier-authdaemon
1 upgraded, 1 newly installed, 0 to remove and 3 not upgraded.
8 not fully installed or removed.
Need to get 0B/83.9kB of archives.
After unpacking 164kB of additional disk space will be used.
Do you want to continue [Y/n]?
dpkg: error processing courier-authdaemon (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
terminate called after throwing an instance of 'std::logic_error'
  what():  basic_string::_S_construct NULL not valid
Aborted
root@pengserv:~ # Errors were encountered while processing:
 courier-authdaemon
```

---

