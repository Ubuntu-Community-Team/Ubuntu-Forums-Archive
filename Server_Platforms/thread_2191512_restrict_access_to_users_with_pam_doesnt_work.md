---
title: "restrict access to users with pam doesnt work"
date: 2013-12-03
forum: Server Platforms
---

### Post by st_cyron on 2013-12-03
Hi,

There are two user on my system which are root and user2 and I need to restrict access of root user that is accessible only from a static IP but user2 could be accessible from anywhere So I thought that Pam is useful for such that request.

I've found some documents on the net.
[http://www.cyberciti.biz/tips/openssh-root-user-account-restriction-revisited.html](http://www.cyberciti.biz/tips/openssh-root-user-account-restriction-revisited.html)
[http://lifeunix.blogspot.com/2012/11/pam-and-ssh-user-account-restriction.html](http://lifeunix.blogspot.com/2012/11/pam-and-ssh-user-account-restriction.html)
[http://www.tuxradar.com/content/how-pam-works](http://www.tuxradar.com/content/how-pam-works)

All of them is easy and well-writen, I did whatever they said but pam doesnt work.

There 2 files that I need to edit;
* /etc/security/access.conf
append following line
    + : root : 127.0.0.1
* /etc/pam.d/sshd
append following line
   account  required     pam_access.so

According to configuration root user only login from localhost I mean just from inside of server. but I can still make ssh from local network which I use in my house such as 192.168.2.x network; for example server is 192.168.2.10 and client 192.168.2.11

What am I missing here?

---

