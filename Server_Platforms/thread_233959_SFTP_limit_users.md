---
title: "SFTP limit users"
date: 2006-08-10
forum: Server Platforms
---

### Post by stormblue on 2006-08-10
I've searched around the internet and the forum and I'm looking to limit all sftp users to /var/www how would I go about doing this?  I'd be interested in a guid to ssh and/or sftp for someone who isn't too familiar with it, but understand the basics and configuration of it.

Thanks.

---

### Post by simonn on 2006-08-11
You need to use openssh chroot to do this:

[http://www.brandonhutchinson.com/chroot_ssh.html](http://www.brandonhutchinson.com/chroot_ssh.html)

---

### Post by stormblue on 2006-08-11
Alright, thanks.  Looks like it's exactly what I'm trying to do.  Thanks!

---

