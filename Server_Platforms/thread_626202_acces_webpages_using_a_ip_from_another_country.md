---
title: "acces webpages using a ip from another country"
date: 2007-11-28
forum: Server Platforms
---

### Post by monkeyking on 2007-11-28
Hi,

In Denmark the public service tv channel has set up a nice web interface to all their programs.
So you can sit and watch their shows whenever you want.


But you can only use it,
if you have a danish ip.

So when I go travel is there someway, to use a danish ip.

I have access to severel servers/ computers in denmark.


thanks

---

### Post by netlogic on 2007-11-28
You can setup a proxy server like SQUID on your Denmark server. That should do it. If you want an instant gratification, you can use ssh.

1. ssh -D <localport> <remotehost> server1.denmark.com
2. change your firefox --> socks5 --> localhost --> port number you routed to..

---

