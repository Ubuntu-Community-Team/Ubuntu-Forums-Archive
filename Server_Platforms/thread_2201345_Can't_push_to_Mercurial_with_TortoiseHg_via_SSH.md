---
title: "Can't push to Mercurial with TortoiseHg via SSH"
date: 2014-01-24
forum: Server Platforms
---

### Post by japtar on 2014-01-24
Hello, everyone.  I'm trying to setup a personal Ubuntu Mercurial server using SSH.  Here are the stats on my server:

```
Ubuntu 12.04.4 LTS (GNU/Linux 3.2.0-58-generic-pae i686)


$ ssh -v
OpenSSH_5.9p1 Debian-5ubuntu1.1, OpenSSL 1.0.1 14 Mar 2012


$ hg version
Mercurial Distributed SCM (version 2.8.2)
(see http://mercurial.selenic.com for more information)


Copyright (C) 2005-2013 Matt Mackall and others
This is free software; see the source for copying conditions. There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
```
I'm using TortoiseHg on my Windows computer to clone, commit, and push to this server (I'm the only one using it).  Unable to do so, I've tried using Powershell to see if it provided any more information.
```
PS C:\Users\****\Mercurial\Monet> hg versionMercurial Distributed SCM (version 2.8.1)
(see http://mercurial.selenic.com for more information)


Copyright (C) 2005-2013 Matt Mackall and others
This is free software; see the source for copying conditions. There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.


PS C:\Users\****\Mercurial\Monet> hg push -vpushing to ssh://****/repo/Monet.hg
running "C:\Program Files\TortoiseHg\TortoisePlink.exe" -ssh -2 -batch -C kyoto "hg -R repo/Monet.hg serve --stdio"
abort: no suitable response from remote hg!
```

Which isn't a very useful error message.  What might be the problem here, and what can I do to figure out what may be the cause for this issue?

Edit: Originally, Ubuntu 12.04.4 used Mercurial version 2.0.2.  I tried upgrading recently to 2.8.2 as seen above, but that didn't seem to fix the problem.

---

### Post by japtar on 2014-01-29
I hate to bump, but *bump*!  I still haven't figured out why this problem occurs.

---

