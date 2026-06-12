---
title: "whatismyip.com can detect that I'm running tinyproxy...?"
date: 2012-01-18
forum: Server Platforms
---

### Post by sirspazzolot on 2012-01-18
is there a more covert method or alternative? ssh tunneling does work but I'm a little reluctant to give people ssh access to my server, unless I can figure out how to create a user with no privileges whatsoever.

---

### Post by sirspazzolot on 2012-01-19
oh, nobody wants to help. that's disappointing.

---

### Post by lisati on 2012-01-19
Just an observation: some proxies are easier to detect than others. Some of the differences are described here: [http://whatismyipaddress.com/proxy-server](http://whatismyipaddress.com/proxy-server)

edit: [This page]("http://lisati.homelinux.com/whoami") is able to use the information provided by *some* proxies.

---

### Post by CharlesA on 2012-01-19
> **sirspazzolot said:**
> is there a more covert method or alternative? ssh tunneling does work but I'm a little reluctant to give people ssh access to my server, unless I can figure out how to create a user with no privileges whatsoever.
You can always use the forcecommand to create a user account that can only use ssh for tunneling.

Either that or just do a chroot jail, so they cannot mess with the system.

EDIT: Found a good thread about it:
[http://ubuntuforums.org/showthread.php?t=1627240](http://ubuntuforums.org/showthread.php?t=1627240)

---

