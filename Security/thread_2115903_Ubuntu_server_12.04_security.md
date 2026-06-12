---
title: "Ubuntu server 12.04 security"
date: 2013-02-14
forum: Security
---

### Post by ganewbie on 2013-02-14
Excuse my ignorance, I do have fail2ban working on my server properly (blocks whoever try to login whith wrong username or password) ufw is running. Now how to check for:
A log of who (IP address) is trying to hack into the server?
How to add my own IP addresses to like a safe list that will not be blocked? 
I would need help in detail as I am very new to servers if you do not mind.
Thanks in advance,

---

### Post by CharlesA on 2013-02-14
This should get you started.
[https://help.ubuntu.com/community/Fail2ban](https://help.ubuntu.com/community/Fail2ban)
[http://www.fail2ban.org/wiki/index.php/Main_Page](http://www.fail2ban.org/wiki/index.php/Main_Page)

---

### Post by Soul-Sing on 2013-02-15
ganewbie, there is a lot of reading and learning to be done before you'r runnung a server in a safe manner. It may take some time, but better save than sorry....

---

### Post by aerokid240 on 2013-03-07
Fail2ban has a directive, ignoreip, that would prevent that ip address from being ban ( stuff like 127.0.0.1 will go here). Also, fail2ban has its own log file at /var/log/fail2ban.log in which can be parsed to get information on who and when an IP was banned. Or you can just get it from iptables.

---

