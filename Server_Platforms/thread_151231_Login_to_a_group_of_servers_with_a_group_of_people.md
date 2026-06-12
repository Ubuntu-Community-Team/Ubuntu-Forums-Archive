---
title: "Login to a group of servers with a group of people securely"
date: 2006-03-27
forum: Server Platforms
---

### Post by Takkie on 2006-03-27
At work we host webapplications on 20 different (own) debian servers. In our company there are about 4 persons that should be able to do administrative tasks and 10 to 15 persons that should be able to connect to the database, run svn commands and add/modify/remove files from/to the webroot.

Up till now security hasn't be a major issue (the company has grown from 4 to 20 in about two years) but is becomming more and more important each day (new colleagues arrive and others go away). Our password policy is currently based on an excel sheet containing all root (both shell and mysql) passwords of our servers which is 'protected' by a single password that everybody knows (including ex-colleagues and everybody that has ever worked with us for more than one day).

Since a few weeks I've switched my Windows XP install for an Ubuntu Dapper install and since I've learned a little more about SSH and certificates. That new knowledge has lead me to think about how to solve our security problems. Does anybody have any idea how we should set up our servers and clients?

---

### Post by stuporglue on 2006-03-27
> Our password policy is currently based on an excel sheet containing all root (both shell and mysql) passwords of our servers which is 'protected' by a single password that everybody knows (including ex-colleagues and everybody that has ever worked with us for more than one day).

Does anybody have any idea how we should set up our servers and clients?

No one will be able to give you a complete detailed answer without looking carefully at what the servers do, who's supposed to do what on the different servers, etc. 

Obviously though, the current situation is not ideal. 

Using ssh keys is one thing that could help. Another is using sudo. You notice how Ubuntu doesn't have a root login, but instead you use sudo to do admin tasks? Sudo is very powerfull. You could do something like change the root password any only let two people know it (ie. in case something happens to the other). The other users could be given their own shell accounts, and sudo configured so that they can only perform specific tasks. 

You can tell sudo that user x can only do command y, or that group A can only do commands B, C and D.

Everyone knowing the password is ok in a small company where everyone is wearing multiple hats, but as it grows and people have assigned roles, it's time to start putting up some walls and segmenting responsibilities and permissions.

---

### Post by Takkie on 2006-03-27
[QUOTE=stuporglue]Using ssh keys is one thing that could help. Another is using sudo. You notice how Ubuntu doesn't have a root login, but instead you use sudo to do admin tasks? Sudo is very powerfull. You could do something like change the root password any only let two people know it (ie. in case something happens to the other). The other users could be given their own shell accounts, and sudo configured so that they can only perform specific tasks. 

You can tell sudo that user x can only do command y, or that group A can only do commands B, C and D.[/QUOTE]

Giving each user an account on each server with an entry in the sudoers file seemed the obvious solution. The problem with this approach is that adding or removing users needs to be done on 20+ servers for both a mysql and shell user.

Maybe a little offtopic: I've been trying to disable password authentication for a specific user (only allowing that user to log in using certificates), but adding PasswordAuthentication No to ~/.ssh/sshd_config doesn't seem to work...

---

### Post by stuporglue on 2006-03-27
> Giving each user an account on each server with an entry in the sudoers file seemed the obvious solution. The problem with this approach is that adding or removing users needs to be done on 20+ servers for both a mysql and shell user.

That sounds like a job for ldap. Ldap lets you add users in a single location and manage which groups their in etc. It should be able to handle your mysql and shell account stuff.

---

