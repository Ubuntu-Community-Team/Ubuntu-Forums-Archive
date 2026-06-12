---
title: "mysql &amp; postfix"
date: 2008-10-04
forum: Server Platforms
---

### Post by Vegan on 2008-10-04
I see an easy local file angle for setting up mx aliases.

% postmap -q [email]info@example.com[/email] hash:/etc/postfix/virtual 

I was wondering, can I leverage my SQL daemon since it is available in the standard LAMP platform?

---

### Post by windependence on 2008-10-04
This one:

[http://www.howtoforge.com/virtual_postfix_mysql_quota_courier_ubuntu_edgy_p2](http://www.howtoforge.com/virtual_postfix_mysql_quota_courier_ubuntu_edgy_p2)

Or this:

[http://www.postfix.com/MYSQL_README.html](http://www.postfix.com/MYSQL_README.html)

Should help you.

-Tim

---

