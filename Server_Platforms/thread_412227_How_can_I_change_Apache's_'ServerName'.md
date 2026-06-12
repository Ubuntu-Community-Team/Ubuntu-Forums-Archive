---
title: "How can I change Apache's 'ServerName'?"
date: 2007-04-17
forum: Server Platforms
---

### Post by Xarok on 2007-04-17
I'm trying to give Apache2 (with Ubuntu 6.06 server)  a 'ServerName' but everything I've tried doesn't seem to work.  The config files I change don't even seem to have a line called 'ServerName'

I've tried looking this up on the Internet, but the tutorials all say different things and so far none of them have worked.

If you know how I might be able to do this please let me know. Thanks.

---

### Post by rmemm on 2007-04-17
You can search for them in the apache2 config directory:

grep -nr 'ServerName' /etc/apache2

Mine is in /etc/apach2/apache2.conf.  Don't know where your's is.

Rob

---

