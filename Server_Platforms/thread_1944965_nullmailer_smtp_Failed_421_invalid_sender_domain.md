---
title: "nullmailer: smtp: Failed: 421 invalid sender domain"
date: 2012-03-22
forum: Server Platforms
---

### Post by speedAmaster on 2012-03-22
I do have my ubuntu 11.10 running as server. While basic installation I might have made some mistakes as I do get following error messages in /var/log/syslog

```
localhost nullmailer[8597]: smtp: Failed: 421 invalid sender domain 'basement.basement' (misconfigured dns?)
localhost nullmailer[1394]: Sending failed:  Temporary error in sending the message
localhost nullmailer[1394]: Starting delivery: protocol: smtp host: smtp.1und1.de file: 1332411301.5305

```

my hostname is "basement"
```
@basement:~$ hostname
basement
```
```
@basement:~$ more /etc/hosts
127.0.0.1       localhost basement.xyz.de basement

```

I am using 1und1 (1&1) as smtp service and nullmailer has the following config:
```
@basement:~$ more /etc/nullmailer/remotes
smtp.1und1.de smtp --port=587 --user=abc@xyz.de --pass=___
```
```
@basement:~$ more /etc/nullmailer/defaultdomain
xyz.de
```

How do I need to change the configuration to avoid the log entries? Do I have a million unsent-message I furst have to purge?

---

### Post by SeijiSensei on 2012-03-22
If you're forwarding through an external mail server, you need to use a real domain, not one you made up.  The relay server will have no idea what @basement means and will reject your mail.

---

### Post by speedAmaster on 2012-03-22
yep - this is what I tried with the hosts entry. WHERE do I administer the domain used by nullmailer? sorry for that newbie question.

---

