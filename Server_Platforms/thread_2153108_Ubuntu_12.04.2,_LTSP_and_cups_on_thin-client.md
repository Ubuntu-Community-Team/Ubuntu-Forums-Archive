---
title: "Ubuntu 12.04.2, LTSP and cups on thin-client"
date: 2013-06-10
forum: Server Platforms
---

### Post by vladsol on 2013-06-10
Hi, all!

I have a problem With LTSP on Ubuntu precise (12.04.2 LTS)

Trying to set-up cupsd on thin client`s side, on example, by [this article]("https://help.ubuntu.com/community/UbuntuLTSP/LocalAppsLucidPrinting"). (yes, i'll do "ltsp-update-image" :) )
Unfortunately, cups init script does not appears on thin client's side.

In chroot:
[B]root@ltsp:/# ls -l /etc/init.d/cups 
lrwxrwxrwx 1 root root 21 &#1052;&#1072;&#1081; 13 18:09 /etc/init.d/cups -> /lib/init/upstart-job[/B]

On thin client:
[B]root@ltsp66:~# ls -l /etc/init.d/cups
ls: cannot access /etc/init.d/cups: No such file or directory[/B]

With other services all is ok (on example, ssh).

---

