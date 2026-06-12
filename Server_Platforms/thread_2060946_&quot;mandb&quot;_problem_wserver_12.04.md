---
title: "&quot;mandb&quot; problem w/server 12.04"
date: 2012-09-21
forum: Server Platforms
---

### Post by Krupski on 2012-09-21
Hi all,

Whenever I do an "apt-get update" on my server (Ubuntu 12.04.1 server 64 bit) I get the following error message:

[FONT="Courier New"]**/usr/bin/mandb: the setuid man user "man" does not exist**[/FONT]


The user does indeed exist (from /etc/passwd):
[FONT="Courier New"][B]
man:x:6:12:man:/var/cache/man:/bin/sh[/B][/FONT]

I searched here and Google, but can't find anything relevant. 

Anyone have an idea?

Thanks!

-- Roger

---

