---
title: "What is the best way to keep attackers off my mail server?"
date: 2011-06-08
forum: Security
---

### Post by wsonar on 2011-06-08
here is my mail log I have setup virtual hosting with postfix and courier

examples from my maikl.info file

```
 8 14:46:46 dynamicweb pop3d: LOGIN FAILED, user=arthur, ip=[::ffff:95.31.15.64]
Jun  8 14:46:46 dynamicweb pop3d: LOGIN FAILED, user=ashley, ip=[::ffff:95.31.15.64]
Jun  8 14:46:46 dynamicweb pop3d: LOGOUT, ip=[::ffff:95.31.15.64]
Jun  8 14:46:47 dynamicweb pop3d: Maximum connection limit reached for ::ffff:95.31.15.64
Jun  8 14:46:47 dynamicweb pop3d: Maximum connection limit reached for ::ffff:95.31.15.64
Jun  8 14:46:47 dynamicweb pop3d: LOGIN FAILED, user=anita, ip=[::ffff:95.31.15.64]
Jun  8 14:46:47 dynamicweb pop3d: Maximum connection limit reached for ::ffff:95.31.15.64
Jun  8 14:46:49 dynamicweb pop3d: last message repeated 6 times
Jun  8 14:46:49 dynamicweb pop3d: LOGOUT, ip=[::ffff:95.31.15.64]
Jun  8 14:46:49 dynamicweb pop3d: Maximum connection limit reached for ::ffff:95.31.15.64
Jun  8 14:46:50 dynamicweb pop3d: LOGIN FAILED, user=ann, ip=[::ffff:95.31.15.64]
Jun  8 14:46:50 dynamicweb pop3d: Maximum connection limit reached for ::ffff:95.31.15.64
Jun  8 14:46:51 dynamicweb pop3d: last message repeated 11 times
Jun  8 14:46:51 dynamicweb pop3d: LOGOUT, ip=[::ffff:95.31.15.64]
Jun  8 14:46:51 dynamicweb pop3d: LOGOUT, ip=[::ffff:95.31.15.64]
Jun  8 14:46:52 dynamicweb pop3d: Maximum connection limit reached for ::ffff:95.31.15.64
Jun  8 14:46:52 dynamicweb pop3d: last message repeated 2 times
Jun  8 14:46:52 dynamicweb pop3d: LOGIN FAILED, user=asia, ip=[::ffff:95.31.15.64]
Jun  8 14:46:52 dynamicweb pop3d: LOGIN FAILED, user=audrey, ip=[::ffff:95.31.15.64]
Jun  8 14:46:52 dynamicweb pop3d: Maximum connection limit reached for ::ffff:95.31.15.64
Jun  8 14:46:52 dynamicweb pop3d: LOGOUT, ip=[::ffff:95.31.15.64]
Jun  8 14:46:52 dynamicweb pop3d: Maximum connection limit reached for ::ffff:95.31.15.64
Jun  8 14:46:53 dynamicweb pop3d: last message repeated 4 times
Jun  8 14:46:53 dynamicweb pop3d: LOGIN FAILED, user=anton, ip=[::ffff:95.31.15.64]
Jun  8 14:46:54 dynamicweb pop3d: Maximum connection limit reached for ::ffff:95.31.15.64
Jun  8 14:46:55 dynamicweb pop3d: last message repeated 6 times
Jun  8 14:46:55 dynamicweb pop3d: LOGOUT, ip=[::ffff:95.31.15.64]
Jun  8 14:46:55 dynamicweb pop3d: Maximum connection limit reached for ::ffff:95.31.15.64
Jun  8 14:46:55 dynamicweb pop3d: Maximum connection limit reached for ::ffff:95.31.15.64
Jun  8 14:46:55 dynamicweb pop3d: LOGIN FAILED, user=annie, ip=[::ffff:95.31.15.64]
Jun  8 14:46:55 dynamicweb pop3d: Maximum connection limit reached for ::ffff:95.31.15.64
Jun  8 14:46:57 dynamicweb pop3d: last message repeated 14 times
Jun  8 14:46:57 dynamicweb pop3d: LOGOUT, ip=[::ffff:95.31.15.64]
Jun  8 14:46:57 dynamicweb pop3d: LOGOUT, ip=[::ffff:95.31.15.64]
Jun  8 14:46:58 dynamicweb pop3d: Maximum connection limit reached for ::ffff:95.31.15.64
Jun  8 14:46:58 dynamicweb pop3d: last message repeated 2 times
Jun  8 14:46:58 dynamicweb pop3d: LOGIN FAILED, user=august, ip=[::ffff:95.31.15.64]
Jun  8 14:46:58 dynamicweb pop3d: LOGIN FAILED, user=austin, ip=[::ffff:95.31.15.64]
Jun  8 14:46:58 dynamicweb pop3d: Maximum connection limit reached for ::ffff:95.31.15.64
Jun  8 14:46:58 dynamicweb pop3d: Maximum connection limit reached for ::ffff:95.31.15.64
Jun  8 14:46:58 dynamicweb pop3d: LOGOUT, ip=[::ffff:95.31.15.64]
Jun  8 14:46:59 dynamicweb pop3d: Maximum connection limit reached for ::ffff:95.31.15.64
Jun  8 14:46:59 dynamicweb pop3d: Maximum connection limit reached for ::ffff:95.31.15.64
Jun  8 14:46:59 dynamicweb pop3d: LOGIN FAILED, user=audrey, ip=[::ffff:95.31.15.64]
Jun  8 14:46:59 dynamicweb pop3d: Maximum connection limit reached for ::ffff:95.31.15.64
Jun  8 14:47:01 dynamicweb pop3d: last message repeated 10 times
Jun  8 14:47:01 dynamicweb pop3d: LOGOUT, ip=[::ffff:95.31.15.64]
Jun  8 14:47:01 dynamicweb pop3d: Maximum connection limit reached for ::ffff:95.31.15.64
Jun  8 14:47:01 dynamicweb pop3d: Maximum connection limit reached for ::ffff:95.31.15.64

```


```
Jun  6 13:56:27 dynamicweb pop3d: LOGIN FAILED, user=amanda, ip=[::ffff:210.46.85.170]
Jun  6 13:56:33 dynamicweb pop3d: LOGIN FAILED, user=daniel, ip=[::ffff:210.46.85.170]
Jun  6 13:56:40 dynamicweb pop3d: LOGIN FAILED, user=daniel, ip=[::ffff:210.46.85.170]
Jun  6 13:56:46 dynamicweb pop3d: LOGIN FAILED, user=tomy, ip=[::ffff:210.46.85.170]
Jun  6 13:56:52 dynamicweb pop3d: LOGIN FAILED, user=tomy, ip=[::ffff:210.46.85.170]
Jun  6 13:56:59 dynamicweb pop3d: LOGIN FAILED, user=michelle, ip=[::ffff:210.46.85.170]
Jun  6 13:57:05 dynamicweb pop3d: LOGIN FAILED, user=michelle, ip=[::ffff:210.46.85.170]
Jun  6 13:57:11 dynamicweb pop3d: LOGIN FAILED, user=nicole, ip=[::ffff:210.46.85.170]
Jun  6 13:57:18 dynamicweb pop3d: LOGIN FAILED, user=nicole, ip=[::ffff:210.46.85.170]
Jun  6 13:57:24 dynamicweb pop3d: LOGIN FAILED, user=linda, ip=[::ffff:210.46.85.170]
Jun  6 13:57:31 dynamicweb pop3d: LOGIN FAILED, user=linda, ip=[::ffff:210.46.85.170]
Jun  6 13:57:37 dynamicweb pop3d: LOGIN FAILED, user=robert, ip=[::ffff:210.46.85.170]
Jun  6 13:57:43 dynamicweb pop3d: LOGIN FAILED, user=robert, ip=[::ffff:210.46.85.170]
Jun  6 13:57:50 dynamicweb pop3d: LOGIN FAILED, user=matthew, ip=[::ffff:210.46.85.170]
Jun  6 13:57:56 dynamicweb pop3d: LOGIN FAILED, user=matthew, ip=[::ffff:210.46.85.170]
Jun  6 13:58:02 dynamicweb pop3d: LOGIN FAILED, user=james, ip=[::ffff:210.46.85.170]
Jun  6 13:58:08 dynamicweb pop3d: LOGIN FAILED, user=james, ip=[::ffff:210.46.85.170]
Jun  6 13:58:15 dynamicweb pop3d: LOGIN FAILED, user=clark, ip=[::ffff:210.46.85.170]
Jun  6 13:58:21 dynamicweb pop3d: LOGIN FAILED, user=clark, ip=[::ffff:210.46.85.170]
Jun  6 13:58:27 dynamicweb pop3d: LOGIN FAILED, user=thomas, ip=[::ffff:210.46.85.170]
Jun  6 13:58:34 dynamicweb pop3d: LOGIN FAILED, user=thomas, ip=[::ffff:210.46.85.170]
Jun  6 13:58:40 dynamicweb pop3d: LOGIN FAILED, user=jason, ip=[::ffff:210.46.85.170]
Jun  6 13:58:46 dynamicweb pop3d: LOGIN FAILED, user=jason, ip=[::ffff:210.46.85.170]
Jun  6 13:58:53 dynamicweb pop3d: LOGIN FAILED, user=justin, ip=[::ffff:210.46.85.170]

```

any help greatly appreciated

---

### Post by wsonar on 2011-06-08
I emailed abuse@theprovider address in the whois info

---

### Post by Clachair on 2011-06-08
I've had this problem on a grand scale for several years. Usually a couple of thousand attempts each night - the whois information invariably leads to a couple of small towns in China. Not sure about the mail server, but I've had to limit the access to my website server via Apache, and if you see recurrent IP addresses as in your example you can always write a script to automatically direct responses to localhost. 
Good Luck!

---

### Post by lisati on 2011-06-08
[Fail2Ban]("https://help.ubuntu.com/community/Fail2ban") is one option you might want to look at.

---

### Post by hackertarget on 2011-06-08
Really depends on your server usage. Some ideas to get going....

* If for example you have a small business and users login from pre-determined ISP's or static IP's you could only allow access from these addresses.

* Ensure users are aware of the need for strong passwords.

* Run OSSEC.net or something similar so you are aware of what's happening on your server. You may need to filter some of the alerts from these sorts of attacks, but you will still get alerts if someone actually breaches the server and starts making changes or gets a valid login following a brute force attack.

* There are various ways to block ip's dynamically including with ossec.

---

### Post by wsonar on 2011-06-09
It's just a web server for some small websites and apps I host and I host email on it for them.

In the mean timeI used UFW to block the IP's I may see If I can make a script to automate it

I will investigate the fail2ban  

thanks for the help

---

