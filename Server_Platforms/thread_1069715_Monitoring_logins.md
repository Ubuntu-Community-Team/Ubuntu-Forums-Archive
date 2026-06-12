---
title: "Monitoring logins"
date: 2009-02-14
forum: Server Platforms
---

### Post by spinanicky on 2009-02-14
Hi, 

I have a server set up and I wanted to know how I could monitor logins to phpmyadmin, ssh.. etc. Basically I just want to make sure im not being brute forced with lots of fake logins. 

btw i have set up phpmyadmin to have a .htaccess as well so there are two logins :D

Many thanks

---

### Post by spinanicky on 2009-02-15
bump

---

### Post by linux_tech on 2009-02-15
You can monitor the file /var/log/auth.log for successful and unsuccessful login attempts

ie.
```
sudo tail -F /var/log/auth.log | grep sshd
```

denyhosts and fail2ban are 2 programs to help prevent these types of attacks

Setting up email notifications is not a bad idea, see how here-
[http://adminlinux.blogspot.com/2007/10/system-security-monitor-root-access.htm](http://adminlinux.blogspot.com/2007/10/system-security-monitor-root-access.htm)

---

