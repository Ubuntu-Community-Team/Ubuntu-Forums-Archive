---
title: "Fail2Ban Question"
date: 2016-04-09
forum: Security
---

### Post by SchnappiJedi on 2016-04-09
Hi,

After running: 
"sudo fail2ban-client set jailname unbanip IP"

How long until Fail2Ban will block that same IP IP again for further failed login attempts? Basically how permanent is the unban? Dies Fail2Ban immediately start recording any further failed login attempts from that IP after running the above command?

Thanks.

---

### Post by Habitual on 2016-04-10
> **schnappi2 said:**
> How long until Fail2Ban will block that same IP IP again for further failed login attempts?
If you unban it, it could occur on the next scan of the "logpath", or a fail2ban-server restart, or
if that IP hits x times in x seconds

 > **schnappi2 said:**
> Basically how permanent is the unban?
see "bantime" value(s) in /etc/fail2ban/jail.local or /etc/fail2ban/jail.conf

> **schnappi2 said:**
> Dies Fail2Ban immediately start recording any further failed login attempts from that IP after running the above command?
Yes.

[https://help.ubuntu.com/community/Fail2ban](https://help.ubuntu.com/community/Fail2ban)
[http://www.fail2ban.org/wiki/index.php/Main_Page](http://www.fail2ban.org/wiki/index.php/Main_Page)

---

### Post by SchnappiJedi on 2016-04-10
Thanks. Findtime and bantime is set to one day so as soon as unbanned IP it was re-banned as soon as the logs were scanned.

---

### Post by Habitual on 2016-04-11
Glad it worked out.
```
bantime = -1 #forever
```
and 
findtime default is 600 # that's seconds.

Any value not present in an explicit jail will use values from the 
"DEFAULT" section of /etc/fail2ban/jail.local or /etc/fail2ban/jail.conf
I believe that value is 600 and is measured in seconds.

---

