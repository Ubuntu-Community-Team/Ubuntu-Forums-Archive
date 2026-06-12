---
title: "rkhunter daily monitoring email"
date: 2016-02-02
forum: Security
---

### Post by david486 on 2016-02-02
hi, i have TS3 server on ubuntu and i install rkhunter, but i dont know how make daily report to email,can you help me? :)

---

### Post by Habitual on 2016-02-02
/etc/rkhunter.conf
```
MAIL-ON-WARNING="user@domain.com"
```

Requires postfix|sendmail|other_MTA if you want to mail to [email]user@some_domain.com[/email]

[http://rkhunter.cvs.sourceforge.net/viewvc/rkhunter/rkhunter/files/FAQ](http://rkhunter.cvs.sourceforge.net/viewvc/rkhunter/rkhunter/files/FAQ)

---

### Post by david486 on 2016-02-03
There?
[IMG]http://jpeg.cz/images/2016/02/03/62Rp.png[/IMG]

---

### Post by Habitual on 2016-02-03
What does /etc/rkhunter.conf say about "there"?

---

