---
title: "where is file mailgraph use to update rrd database?"
date: 2011-06-27
forum: Server Platforms
---

### Post by venol on 2011-06-27
helo, I have install postfix system on my mail server with ubuntu 10.04, and the server works as well. for monitoring I use mailgraph to create graph on web browser. But, when I test to delete rrd file on /var/lib/mailgraph*.rrd and then make sure /var/log/mail.log empty, and next restart mailgraph. But, Why the old graph was shown ? I have delete rrd file and make sure mail.log empty.
And configuration on /etc/default/mailgraph like this :
> BOOT_START=
MAIL_LOG=/var/log/mail.log
IGNORE_LOCALHOST=false

what is problem? What does mailgraph not use /var/log/mail.log to update rrd file?
thanks for your help.

---

### Post by venol on 2011-06-29
somebody can help me please, n_n

---

