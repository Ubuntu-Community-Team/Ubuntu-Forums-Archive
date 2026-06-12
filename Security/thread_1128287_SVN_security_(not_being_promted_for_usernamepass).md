---
title: "SVN security (not being promted for username/pass)"
date: 2009-04-17
forum: Security
---

### Post by sea2dca on 2009-04-17
I just set up SVN and Apache on an UBUNTU 8.10 box, got my repositories setup, connected with subclipse/eclipse and all works great (was prompted for a username and password). However I can visit the repository address in a web browser form any computer I can see all files etc without being prompted for a username and pass. I followed the set up tutorial at [http://www.php-architect.com/blog/2008/10/07/install-subversion-with-web-access-on-ubuntu-804-hardy-heron/]("http://www.php-architect.com/blog/2008/10/07/install-subversion-with-web-access-on-ubuntu-804-hardy-heron/") and every other tutorial mentions upon visiting the address in a browser, you should be prompted. Clearly this is security risk, can anyone point me in the direction of locking this up?

Note: I have not currently setup the SSL connection and am doing this over port 80 for now.

Thanks

---

### Post by sea2dca on 2009-04-17
Waste of day!!  An Apache restart solved the issue, though I swear i did that multiple times. I did one more time after hours of researching how to secure an Apache directory and tada.

---

