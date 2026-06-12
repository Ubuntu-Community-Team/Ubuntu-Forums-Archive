---
title: "Postfix starts but doesn't"
date: 2009-11-27
forum: Server Platforms
---

### Post by kbo206 on 2009-11-27
When I run:
```
sudo postfix start
```and
```
sudo service postfix start
```It says:
```
postfix/postfix-script: starting the Postfix mail system
```and
```
* Starting Postfix Mail Transport Agent postfix
   ...done.

```respectively.

However, when I try stopping it (via "sudo postfix stop"), since it says it's started...
```
postfix/postfix-script: fatal: the Postfix mail system is not running
```Apparently, it says it's started but then when I stop it, it claims it was never running. Can anyone help me get to the bottom of this? :D

---

### Post by windependence on 2009-11-28
Can you post your postfix logs?
They are in /var/log/mail.log 
You can get the whole log like this:

```
sudo cat /var/log/mail.log | less
```

or just get the last 100 lines like this:

```
tail -n 100 /var/log/mail.log
```

I don't think it's going to make any difference but try starting Postfix like this:

```
sudo /etc/init.d/postfix start
```


-Tim

---

