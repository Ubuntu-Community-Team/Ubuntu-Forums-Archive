---
title: "Newbie With UFW"
date: 2024-02-03
forum: Security
---

### Post by timlab55 on 2024-02-03
I'm totally confused (aren't we all in this world now days) about UFW.  I follow all the right directions checking my list twice (sorry santa), and my ufw still doesn't work as I was hoping it would.  Your my last hope in resolving this problem.  To you might be easy, but to me a newbie in this land of Unix, it's not.  My OS is raspiberry Pi, running Debian 12.  I have two questions for you.
#1:  Nothing is being blocked!  Let me explain.  Let's say I want to block IP address 111.111.111.000.  So I SSH into my webserver and type "sudo ufw deny from 111.111.111.000 to any".  Then I check in to places.  First I type in "sudo cat /etc/ufw/user.rules" and I see it :).  Then I type in "tail -f /var/log/fail2ban.log".  Yes, I'm also running Fail2ban as well.  Now I go back to my apache log in about 3 hours later and guess what I see 111.111.111.000.  Why?  But wait, there is another problem that I noticed as well that I've never seen before.  When I type in sudo cat /etc/usw/user.rules" this is what I see:  First line: ### tuple ### deny any any 0.0.0.0/0 any 111.111.111.000 in -A ufw-user-input -s 111.111.111.000 -j DROP.  On the first line I see (2) any any, is this correct?
#2:  I would like to be able to block the world execpt myself, and the services (SSH, etc) that I'm using.  Then when I start off with a clean Apache2 access log at the stroke of midnight, I would like to look at it again, and not see any outside ip address.  Is this possible?
Thank You
If you need anything else from me to determine what the problem might be, please ask (asking for logs and things).  But remember I'm new so if you want let's say the apache2 log, please don't ask for just the Apache2 log.  Please direct me in where to find them (i.e.  go to var/apache2/access.log.

---

### Post by deadflowr on 2024-02-04
*Thread moved to **Security***
Posting this in the Resolution center would have been of no help to you, since only Forum Staff can post responses there.

---

### Post by timlab55 on 2024-02-04
Thanks didn't know about this section.  I'm hoping someone can answer me, as I would like to move forward with my website.

---

### Post by timlab55 on 2024-02-05
Well, I guess no one in this fourm knows about UFW.

---

