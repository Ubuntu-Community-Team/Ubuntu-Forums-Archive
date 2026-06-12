---
title: "Ubuntu One Sync Chewing Up CPU Cycles"
date: 2010-09-10
forum: Ubuntu One (CLOSED)
---

### Post by jjstables on 2010-09-10
I've got Ubuntu One syncing a single 25MB folder on 4 computers.  On one of these computers, the ubuntuone-syncdaemon process constantly pegs the CPU, using from 50-80% long after any sync-able files have been modified and successfully synced.  The process is only using 8.9MB of RAM.  Any ideas?

Specs:
Ubuntu 10.04 (lucid)
Kernel 2.6.32-24-generic
1000.8 MB RAM
Pentium 4 2.53GHz
Free disk space: 280.9 GB
System monitor shows 56.8% total RAM usage, 15.4% swap file usage.

---

### Post by howefield on 2010-09-10
Not particularly constructive, but I'd ditch it and use Dropbox.

Sorry for not directly addressing your actual question, but Ubuntu One imho, just doesn't cut it.

---

### Post by duanedesign on 2010-09-11
In order to better determine what the issue might be we need to get some debug logs. You can do that by running this command in a Terminal:

```
echo -e "[logging]\nlevel = DEBUG" > ~/.config/ubuntuone/logging.conf; u1sdtool -q; u1sdtool -c
```

Go through the steps to reproduce your issue. The log you can find at ~/.cache/ubuntuone/log/syncdaemon.log

My first guess would be [bug 545350]("https://bugs.launchpad.net/ubuntu/+source/ubuntuone-client/+bug/545350")

**Note** that attaching syncdaemon.log will show filenames you are attempting to sync with Ubuntu One. If you do not want this to be public, please obfuscate those names. Or you can file a bug and mark the bug as private and this bug report will only be available to you and the Ubuntu One team.

---

### Post by venik212 on 2010-11-01
I have the very same problem-- it is sickening...

---

### Post by Ramfanatic on 2013-04-19
Was there a resolution to this? Because it's killing my CPU too...

---

