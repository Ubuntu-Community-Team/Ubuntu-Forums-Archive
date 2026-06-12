---
title: "Security Tips"
date: 2012-01-23
forum: Security
---

### Post by Cotheya on 2012-01-23
I'm working on securing Ubuntu Server Terminal 10.04 and was looking for every tip to secure my Ubuntu Server. If you guys have any advice, please post it below.

---

### Post by TheFu on 2012-01-23
What is an **Ubuntu Server Terminal 10.04**?  
* Which apps, 
* what services, 
* any local users? 
Can you please be specific?

Normal security would be to stay patched, disable unwanted services, use the built-in firewall to block both inbound AND outbound traffic that you do not want, do not allow local accounts, backup, backup, backup, use fail2ban and logwatch along with your normal performance monitoring and alarming software for your location. Monitoring logs is critical to security.

Do not enable FTP or telnet - PERIOD.

What sort of environment is this? A work gateway with 20K users or a home machine with just you and 1 friend to play on?  What do you want to prevent and what exactly do you want to allow?

---

### Post by cariboo on 2012-01-24
@TheFu, have a look [here]("http://www.ltsp.org/") for more info on the LTSP.

---

