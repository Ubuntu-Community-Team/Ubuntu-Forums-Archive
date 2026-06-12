---
title: "do-release-upgrade Error"
date: 2012-04-29
forum: Server Platforms
---

### Post by PierreRobiquet on 2012-04-29
I'm currently running 11.10 on my server, I previous upgraded from 11.04 a few months ago and everything went smoothly however I am having some problems when attempting to upgrade to 12.04. When running do-release-upgrade I am given the following error message:

> 
root@Samsung-NC10:/# do-release-upgrade
Checking for a new ubuntu release
Traceback (most recent call last):
  File "/usr/bin/lsb_release", line 22, in <module>
    import commands
EOFError: EOF read where object expected
lsb_release returned exitcode: 1
No new release found


I've attempted to reinstall update-manager-core however this does not rectify the problem, the server is fully updated through apt-get update and apt-get upgrade and it has also been rebooted with the same error being displayed. It is also shown whether using sudo or being root. 

Is there anyway this can be fixed? I'd rather not do a reinstall of the server as I am guaranteed to forget one of my config files plus I'd like to avoid the extra work load.

---

### Post by PierreRobiquet on 2012-04-29
I've fixed it by removing commands.pyc, here's the command I used:

```
sudo rm /usr/lib/python2.7/commands.pyc
```

---

