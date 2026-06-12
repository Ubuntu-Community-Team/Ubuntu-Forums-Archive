---
title: "need help setting up email server"
date: 2010-10-05
forum: Server Platforms
---

### Post by rcayea on 2010-10-05
Hey everyone,

I recently bought my own domain name and have started working on my website. I am way excited about setting this site up. My question is, what would be the best way to setup an email system where users are able to login and check their email...I guess like, a web-based system? Then they can configure a client if they wish with their email address.

Would something like postfix be the place to start for this?

Thanks for any and all tips. I will take any.

Thanks,
Randy

---

### Post by e79 on 2010-10-05
I am personnaly using the ZIMBRA Community Edition, works like a charm and is not that hard to install and configure as long as you have basic knowloedge of mail servers; they have nice tutorials and forums, and it can be installed on Ubuntu Server 32/64 bit as well as many other distro. This edition, among other things, install a PoP/IMAP server as well as providing you with Web Mail portal.
 
[http://www.zimbra.com/](http://www.zimbra.com/)
 
[http://www.zimbra.com/community/](http://www.zimbra.com/community/)
 
just my 0.02$
 
Hope this helps

---

### Post by rcayea on 2010-10-05
Thanks. You say you are using Ubuntu Server. I have Ubuntu Server but I planned on setting up my email server through the webhosting company I use. 

Can I still do that with Zimbra?

Thanks!

---

### Post by e79 on 2010-10-05
Well as long as your hosting company supports Ubuntu, I'd say yes :P Simply call them and ask if they have server they could rent with Ubuntu server preinstalled, so you could SSH into the box and install Zimbra on top of it. I suggest you give it a try in a virtual machine (if you can) first before attempting to deploy it.

---

### Post by rcayea on 2010-10-05
OK thanks. I did ask if my hosting company supports linux and they said they do. So, I'll see from here. Thanks, again.

---

### Post by e79 on 2010-10-06
My pleasure and good luck !
:)

---

### Post by ootuoyetahi on 2010-10-07
Before you start find out if port 25 is blocked. If it is its going to be a pita.

---

