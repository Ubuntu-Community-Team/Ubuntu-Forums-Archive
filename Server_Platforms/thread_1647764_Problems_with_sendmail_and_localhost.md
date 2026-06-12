---
title: "Problems with sendmail and localhost"
date: 2010-12-17
forum: Server Platforms
---

### Post by walnut100 on 2010-12-17
Hey guys!

I've been struggling to get sendmail working on my chroot setup, I am using mini_sendmail to try to get around the chroot problem

I haven't been able to find what's causing my test mails to not send, but I've looked around and saw that I had to setup my hosts file to get sendmail to work

/etc/hosts

127.0.0.1 localhost.localdomain localhost
<Linode server IP> foo.mydomain.com foo

Also when I input localhost instead of 127.0.0.1 on anything I install (Like MediaWiki) it can't connect to its MySQL database

Am I doing something totally obviously wrong here?

---

