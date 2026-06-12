---
title: "proftpd disable ftp"
date: 2015-06-26
forum: Server Platforms
---

### Post by davidricq87 on 2015-06-26
Hi,

I am currently using proftpd to use sftp.
I know I can use openssh but I need proftpd.

There is a way to disable ftp and keep sftp ?

---

### Post by cariboo on 2015-06-26
When you install the openssh server the sftp protocol is included, so you can safely remove proftpd.

---

### Post by davidricq87 on 2015-06-26
Hi cariboo,
Thanks for your answer.

I know about that, but I need some functionnality from proftpd like virtual user, virtual host, transfer log, multiple port ...
I don't know if it's possible with openssh.

I also think it's more secure (maybe I am wrong) to clearely separate ssh and sftp.

So there is a way to disable ftp from proftpd and keep sftp ?

---

### Post by Lars Noodén on 2015-06-27
I don't use proftp at all but looking around the web there seems to be at least one way to use it with SFTP only and have FTP turned off.  Here is one example:

[https://forums.proftpd.org/smf/index.php?topic=3840.0](https://forums.proftpd.org/smf/index.php?topic=3840.0)

But again as a I don't use proftp I am not sure.

---

### Post by davidricq87 on 2015-06-27
Hi,
I watched this post but I didnt see the second part of the thread.

It seems to be what I am searching.
Thanks for the answer.

---

