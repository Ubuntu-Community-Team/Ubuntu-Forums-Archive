---
title: "Relay access denied"
date: 2012-08-23
forum: Server Platforms
---

### Post by senor_smile on 2012-08-23
In 2008 I set up a simple mail server (running ubuntu 8.04 LTS) to allow local automation controllers to send email alarms without limits.  I used to use gmx, but found that if an account had a ton of alarms, which indicates a problem, that gmx would block it.  I set up postfix and got it working.  I then needed to be able to allow this type of controller to send alarms from remote sites.  I set up firewall rules to my static I.P. address and all is well.  

Now, I have installed a new server, running ubuntu 12.04, doing the exact same thing as before.  Local controllers can connect to the server and send emails just fine.  However, when the remote controllers try to connect, I see the following in /var/log/mail.log :

```
Aug 23 16:21:24 localhost postfix/smtpd[6709]: NOQUEUE: reject: 
RCPT from unknown[xx.xx.xx.xx]: 554 5.7.1 <alarms@mydomain.com>: 
Relay access denied; from=<sender@localhost> 
to=<alarms@mydomain.com> proto=ESMTP helo=<localhost>
```

I found that editing a particular line in /etc/postfix/main.cf allows individual remote I.P. addresses to connect and send mail: 
```
mynetworks = 127.0.0.0/8,10.102.0.0/16,xx.xx.xx.xx
```

where xx.xx.xx.xx is the static i.p. address of the remote location.  I compared configuration files between the old server and the new server, and they're basically identical.  Does anyone know how to get it to work like it did before?

---

