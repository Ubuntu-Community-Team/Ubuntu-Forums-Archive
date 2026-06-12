---
title: "dns causing mail errors"
date: 2006-11-15
forum: Server Platforms
---

### Post by huggy77 on 2006-11-15
when i try and send email to my linux boses postmail server - i get a 553 error... i can send and recieve fine if i send it from one account on my machine to another... i can also send mail out of the box without a problem... does anoyone have any ideas?

---

### Post by cyris| on 2006-11-15
I dont know what MTA you are using, but if its qmail then id tail -f my smtp log file to see what was going on.

---

### Post by huggy77 on 2006-11-16
i am using postfix - courier from:
[http://www.howtoforge.com/virtual_postfix_mysql_quota_courier](http://www.howtoforge.com/virtual_postfix_mysql_quota_courier)

i think i might have to add a zone to my DNS but i am not sure... i am running bind9 on edgy

---

