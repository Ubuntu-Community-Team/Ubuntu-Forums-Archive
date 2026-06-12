---
title: "apt-get update downloads from sources.list not specifed?"
date: 2012-01-09
forum: Server Platforms
---

### Post by Sergius14 on 2012-01-09
Hello,

A coworker has build an Ubuntu Server x64 10.04.3 LTS to be used as general purpose IT stuff.

One of that "stuff" is a local repository / mirror (apt-mirror) which is sync'd and working just fine.

This server has it's own sources.list pointing to himself (it's self IP address).

When we run apt-get update, it gets updated from "himself" (the mirror) just fine, but then starts to download packages from 

[http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) karmic Release 


and many other from Karmic too.


Can be an old package that makes this behavour?


Karmic is not mentioned at all nor in sources.list nor mirror.list.

When I run 'apt-get upgrade', it tries to upgrade sun-java-jre from karmic repo.


Any suggestion?



[LIST]
[*]Ubuntu Server running an apt mirror.
[*]Mirror only sync  lucid.
[*]sources.list get sync'd from himself
[*]Karmic appears from nothing...
[/LIST]


Regards,

---

### Post by Sergius14 on 2012-01-09
I already found something...

For some reason another admin has installed PHP 5.2 and added a karmic.list inside sources.list.d

This is conflicting with other packages.


But at least I found that is making this.

---

