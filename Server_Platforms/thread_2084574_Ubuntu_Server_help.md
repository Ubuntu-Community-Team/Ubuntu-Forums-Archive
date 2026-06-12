---
title: "Ubuntu Server help"
date: 2012-11-15
forum: Server Platforms
---

### Post by Redallover on 2012-11-15
Hello I installed Ubuntu Server 12.04 on my machine and installed different apps like ejabberd(instant messaging server), openswan(vpn), davical(carddav,caldav). Is there a way to have centralized authentication to each app instead of creating new users within each of them. I plan to make users accounts for my friends so they can use it. But I don't want to have the accounts create directories in my hd like /home/user1 and I don't want the users to be able to ssh into the server.
I think it through PAM or maybe some database, I have been searching online but not sure how to phrase my question.

---

### Post by oldos2er on 2012-11-15
Moved to Server Platforms.

---

### Post by lolium on 2012-11-15
In order to do this you will need to find an authentication method that all the software you want to use will support. 

Quick search on google suggests that the afore mentioned software supports LDAP authentication. I would advise looking into that.

---

