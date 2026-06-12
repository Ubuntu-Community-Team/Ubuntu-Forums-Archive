---
title: "Problems with proftpd"
date: 2013-08-17
forum: Ubuntu Cloud and Juju
---

### Post by inge2 on 2013-08-17
Hello!
Although this is my first question here, I'm an experienced Ubuntu (server) user.

I have just set up an Amazon Web Service (AWS), based on Ubuntu 13.04 server.
The reason I ask here is that I can't find a way to post in the AWS support forum.

I have access to ssh, but in order to transfer files and set up a LAMP server I need an ftp program.
I installed vsftpd, but it mysteriously vanished from the system.
I installed proftpd, but it won't run. Here's the error message:

ip-172-31-15-218 proftpd[3608]: warning: unknown/unsupported LANG environment variable 'en_US.UTF-8', ignoring
ip-172-31-15-218 proftpd[3608]: mod_tls_memcache/0.1: notice: unable to register 'memcache' SSL session cache: Memcache support not enabled

I guess I can ignore the first one although it's very strange that THAT language definition should be missing.
About the other one: I see no "memcache" entry in the proftpd.conf file, and I can find no example.

I was tipped to use sftp instead. This was already installed and works right out of the box.

---

