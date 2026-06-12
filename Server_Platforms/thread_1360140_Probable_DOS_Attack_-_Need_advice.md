---
title: "Probable DOS Attack - Need advice"
date: 2009-12-20
forum: Server Platforms
---

### Post by guessswh0 on 2009-12-20
So, this is the first time that I've been administering a linux server.  I think right now it's going under a dos attack.  I know someone is/was trying to get in.  Earlier when looking at syslog, I saw a single IP continually trying to connect to the pop3 service with different usernames.

I set up an IPTables rule to reject all traffic from the IP.  Now, my bandwidth that the server is using is slowly shooting through the roof.  However, it only happens when my e-mail MTA is on (postfix).

If i stop the servive, then everything drops back down.  I need this open so that people can connect to the e-mail server from outside, however, when I look at the syslogs, I'm not seeing anything out of the ordinary.  But this only happens when the service is on.

Any suggestions?  I could use the help

Thanks guys

---

### Post by tgalati4 on 2009-12-20
sudo apt-get install fail2ban

man fail2ban

---

### Post by guessswh0 on 2009-12-20
ok, I installed that in addition with aide and tiger.  EVerything seems to have settled down at the moment.

One last question, when using aide, it did not create an initial database, so I am getting an error when it runs, because the db isn't there.  How do I make it create one?

---

### Post by dragos2 on 2009-12-21
> **guessswh0 said:**
> ok, I installed that in addition with aide and tiger.  EVerything seems to have settled down at the moment.

One last question, when using aide, it did not create an initial database, so I am getting an error when it runs, because the db isn't there.  How do I make it create one?

How about not installing stuff on production servers? :P

Sooner or latter you will crash it, but its fun because you learn how to do it
well :)

---

