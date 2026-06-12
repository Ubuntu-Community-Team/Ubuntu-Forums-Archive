---
title: "Problems with NBD server"
date: 2019-01-22
forum: Server Platforms
---

### Post by Tadaen_Sylvermane on 2019-01-22
I am trying to migrate to 18.04 on my server. Everything is working fine except LTSP. This is what comes out of my /var/log/syslog on my LTSP server when booting a client. The test LTSP server is currently an LXD container running bionic.

```
Jan 23 05:09:00 ltsp nbd_server[344]: Can't open authorization file /etc/ltsp/nbd-server.allow (No such file or directory).Jan 23 05:09:01 ltsp nbd_server[350]: Can't open authorization file /etc/ltsp/nbd-server.allow (No such file or directory).
```

Everytime I boot my client it loads awhile, TFTP works fine. Then it hangs while loading up and says nbd0 timed out. Every few lines it says something about a squashfs error. Have the exact same results with Debian buster right now.

*EDIT* Things have changed. Follow the wiki and all is well. Been running it so long never thought to check if anything was wrong or changed in the ppa vs the official repo version of ltsp.

[http://wiki.ltsp.org/wiki/Installation/Ubuntu](http://wiki.ltsp.org/wiki/Installation/Ubuntu)

Found via finding this.

[https://bugs.launchpad.net/ubuntu/+source/ltsp/+bug/1797839](https://bugs.launchpad.net/ubuntu/+source/ltsp/+bug/1797839)

I will be making my 18.04 migration next week :)

---

