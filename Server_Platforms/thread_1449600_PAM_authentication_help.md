---
title: "PAM authentication help"
date: 2010-04-08
forum: Server Platforms
---

### Post by dragos2 on 2010-04-08
Hi guys,

I need some help with PAM and authentication of users.

I want to define for each user when he can login, something like:

user1:monday to friday from 8 to 18
user2:monday to friday from 8 to 16
user3:anytime

Can this be done ? How ?

Thank you

---

### Post by HermanAB on 2010-04-08
Hmmm, RADIUS does that.

The usual Linux authentication systems only deal with user names and passwords.

So, you could look at this old guide:
[http://www.aeronetworks.ca/radius.html](http://www.aeronetworks.ca/radius.html)

Or you could use the pam_time module:
[http://articles.techrepublic.com.com/5100-10878_11-1055269.html](http://articles.techrepublic.com.com/5100-10878_11-1055269.html)

---

### Post by bluefrog on 2010-08-17
edit /etc/security/time.conf

add the following lines

*;*;user1;AlWd0800-1800
*;*;user2;AlWd0800-1600

no need to add anything for user3, he is allowed to do whatever whenever.

Then add the following line to /etc/pam.d/common-account

account requisite pam_time.so

---

