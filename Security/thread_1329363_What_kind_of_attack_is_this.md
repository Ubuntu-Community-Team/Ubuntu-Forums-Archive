---
title: "What kind of attack is this?"
date: 2009-11-17
forum: Security
---

### Post by zoomiest on 2009-11-17
I run a home webserver, to host a web app that I use at work, or whereever I am.

I have a typical firewall on a Dlink router, but that is all.

Looking at my apache logs, I see some interesting requests... What are they looking for?


1)
[Mon Nov 16 09:21:20 2009] [error] [client 203.82.66.207] Invalid method in request \xe5\xe1\xa2\x91G1s\xc9y\x196\x83{\x9c\xa3\xbc\xdf\xe4\x03;N

2) I see lots of these
[Sat Nov 14 08:59:43 2009] [error] [client 61.160.216.63] script '/var/www/prx2.php' not found or unable to stat

3)I see lots of these
[Mon Nov 09 22:50:28 2009] [error] [client 202.153.225.58] File does not exist: /var/www/components

4)Looks like I someone is totally trying to look over my machine..
[Wed Nov 11 15:53:07 2009] [error] [client 72.89.170.188] Invalid method in request !d\xab\xed)\xcb\x9c\x01
[Wed Nov 11 16:33:04 2009] [error] [client 61.136.208.20] File does not exist: /var/www/mysql
[Wed Nov 11 17:46:24 2009] [error] [client 61.136.208.20] File does not exist: /var/www/phpMyAdmin
[Wed Nov 11 20:32:43 2009] [error] [client 61.136.208.20] File does not exist: /var/www/pma
[Wed Nov 11 22:02:47 2009] [error] [client 61.136.208.20] File does not exist: /var/www/db
[Wed Nov 11 23:46:16 2009] [error] [client 61.136.208.20] File does not exist: /var/www/websql
[Thu Nov 12 01:39:04 2009] [error] [client 61.136.208.20] File does not exist: /var/www/phpadmin
[Thu Nov 12 03:30:27 2009] [error] [client 61.136.208.20] File does not exist: /var/www/admin
[Thu Nov 12 05:28:47 2009] [error] [client 61.136.208.20] File does not exist: /var/www/web
[Thu Nov 12 11:13:21 2009] [error] [client 192.168.0.253] File does not exist: /var/www/favicon.ico

There is a lot more!

Would IPTables or another firewall stop this?
What else should I do?
How can I tell if some hacker has been successful?

---

### Post by cdenley on 2009-11-17
Those requests from 61.136.208.20 look like they are scanning to see if you're using some common web applications. If those scripts existed, the attacker would probably then attempt to exploit a known vulnerability which has since been patched in the latest releases. If the scripts didn't exist, then the attack didn't succeed. If the attacker did find a script with a known vulnerability, then it wouldn't be logged as an error, but just another request not much different from those of actual users.

You can use fail2ban and attempt to detect and ban users checking for vulnerable scripts such as these at the risk of creating false positives and banning actual users. The best approach you can use is to make sure you keep your web applications updated and don't create security holes in your own code if you make your own web applications. These kind of "attacks" are very common, and harmless if you maintain your server properly.

---

### Post by rookcifer on 2009-11-17
> **cdenley said:**
> The best approach you can use is to make sure you keep your web applications updated and don't create security holes in your own code if you make your own web applications.

That along with utilizing AppArmor to help stop 0-days.

---

### Post by cdenley on 2009-11-17
> **rookcifer said:**
> That along with utilizing AppArmor to help stop 0-days.

Specifically, in the context of this thread, creating an apparmor profile for apache, which would restrict what apache is capable of doing in case a web application is exploited and attempts to do something it isn't supposed to do. Might be a little tricky. This probably wouldn't protect you from most web application vulnerabilities since they compromise the application itself, not your system.

---

### Post by bodhi.zazen on 2009-11-17
What you really need is NIDS, ie snort.

Snort will monitory your network traffic and alert you of suspicious activity. You will find, if you watch, tons of suspicious activity in your logs and reading the logs is tedious.

You can then consider some kind of HIDS to see if any of these attacks are successful. OSSEC for example.

---

