---
title: "Email client on server"
date: 2008-12-25
forum: Server Platforms
---

### Post by andyb88 on 2008-12-25
I am in the middle of moving my old windows 'server' (running on XP) to a Ubuntu Server.  Previously I had an email client running on the machine that simply received everyones emails as a simple way to back them up.  Is there an app that would do a similar thing in Ubuntu? I dont want an users to have to log on.

Also if anyone has any suggestions about any server apps that might be useful please feel free to share. :)
Im currently planning to run:
  Apache
  MySQL
  PHP
  Webmin
  proftpd
  firefly
  jinzora
  SAMBA
  also with SSH access

Thanks in advance for the help.

Andy

---

### Post by HermanAB on 2008-12-25
Email servers will retry for up to about 4 days to deliver messages.  So if your server is down, then you should not lose any email, provided that you can bring the new one up in about 2 to 3 days.

So, don't worry about it - just keep working on the new server.

By the way, you can have a complete new mail server up and running in about 20 minutes with the Citadel Easy Install Script:
[http://www.citadel.org/doku.php?id=installation:start](http://www.citadel.org/doku.php?id=installation:start)

Cheers,

Herman

---

