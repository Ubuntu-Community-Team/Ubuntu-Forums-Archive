---
title: "likewise-open5 Login Issues, Openofire &amp; SVN"
date: 2009-07-09
forum: Server Platforms
---

### Post by digitalexpl0it on 2009-07-09
I have setup 3 Ubuntu Server 9.04 Linux boxes here at work. One is running Openfire Jabber Server, ones is running Subversion (SVN), and the last one is running a web server.

All Servers have Likewise-open5 installed and are joined to my windows 2003 server AD. Everything was working great, I can login to ssh, openfire, use apache/PHP ldap etc...

I recently changed my password on my main windows xp pro workstation since I have a policy to change the password every 30 days. The problem is once I changed my password I could not log into any of the Linux servers using my domain account. (Note I have setup Domain Admins group in the sudoers file, %DOMAIN\\Domain^Admins ALL=(ALL) ALL)

I have been trying to find a way to make likewise re-cache the credentials. I did find a command to flush and delete the cache (kdestroy) This allowed me to be able to log into the Linux server with my domain account.

The thing is, I cannot log into SVN with my domain account now nor OpenFire. 

Any ideas?

---

