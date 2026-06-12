---
title: "Reading FTP Accounts"
date: 2010-08-24
forum: Server Platforms
---

### Post by bumcheekcity on 2010-08-24
I have a server with Fasthosts using the Matrix control panel, which I think is running CentOS. We have a few other servers on various Linux flavours, all of which run Plesk. So we can read FTP and mail account information using the wonderful psa database that Plesk stores information in. pleskhacker.com has great examples of this.

But Matrix doesn't do that, so we'd have to read FTP/Mail information manually. How could we do this using a PHP script running on a remote server? 

[For the other servers, we just connect remotely to the IP using a mysql_connect(), whitelist our internal server's IP through 3306 and read the psa database.]

---

