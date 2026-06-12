---
title: "Apache with Multi Virtual Domain"
date: 2010-10-07
forum: Server Platforms
---

### Post by joek71 on 2010-10-07
Hello Guys

I installed Apache2 and I added a second virtual host, now can i separate the 2 hosts and let them access 2 different internal test sites? 
For Example lets say"

User1 uses one IP
User2 uses second IP

How can I separate it in Apache2 and in the /var/www ?

Thank you

---

### Post by bluefrog on 2010-10-07
[http://httpd.apache.org/docs/2.0/vhosts/ip-based.html](http://httpd.apache.org/docs/2.0/vhosts/ip-based.html)

---

### Post by joek71 on 2010-10-07
Thanks, I did that.  But how do I separate it in the /var/www

Should I make a another directory?  I have 2 developers that are working on 2 different projects, and each has there own IP.  But they both address the same directory /var/www
can I separate this, each user has there own /var/www

Thanks

---

### Post by joek71 on 2010-10-07
Also I need by IP not by name.

---

### Post by SeijiSensei on 2010-10-07
Are you trying to keep user1 from accessing the directories visible to user2 and vice versa?  Use Apache's [access controls]("http://httpd.apache.org/docs/2.2/howto/access.html") which can permit or deny access to specific directories by IP.  Put user1's stuff in /var/www/user1 and user2's stuff in /var/www/user2.  Then apply access controls to the directories either in the virtualhost declarations or via .htaccess files in each directory.

---

