---
title: "Strange netstat output - tcp connections on high ports?"
date: 2015-01-16
forum: Security
---

### Post by nicole9 on 2015-01-16
I have a linux server with Linode, and non-peak traffic on my server has been triggering CPU and i/o alerts in my dashboard. 


I've been monitoring things and I am finding find connections like this (in red):


```
root@myserver:/var/log# netstat -natpe
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       User       Inode       PID/Program name
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN      105        107210484   8770/mysqld
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      0          83819345    7804/sshd
tcp        0      0 127.0.0.1:25            0.0.0.0:*               LISTEN      0          9385        4292/exim4
[COLOR=#ff0000]tcp        0      0 my.svr.ip.add:53221     foreign.svr.ip.add:443        TIME_WAIT   0          0           -[/COLOR]
[COLOR=#ff0000]tcp        0      0 my.svr.ip.add:34255     my.svr.ip.add:80        TIME_WAIT   0          0           -[/COLOR]

```


If I then try to use ```
lsof -i tcp:53221 -P -R
``` (or whatever the port is at that time), I get no output. This connection keeps going in and out on my server, changing ports on my server each time - but they're always high numbers. 


Is this normal? Does anyone know what this is, or how I can figure out what it is?

---

### Post by schragge on 2015-01-16
See [this answer](http://serverfault.com/a/507610).

---

### Post by nicole9 on 2015-01-16
So it seems like this is normal? 

What's odd is that the port numbers are always so high (isn't that a sign of a hack?), and certain foreign IPs keep coming back.

---

### Post by Doug S on 2015-01-16
> **nicole9 said:**
> So it seems like this is normal?Yes.> **nicole9 said:**
> What's odd is that the port numbers are always so highYes, that is correct.> **nicole9 said:**
>  (isn't that a sign of a hack?),No.

In your case your computer has a secure web connection to from its port 53221 to some external server, and another regular web connection to itself from its port 34255.

---

### Post by nicole9 on 2015-01-16
Ugh thank goodness!!! Thank you all!!! I obviously need to stop being so paranoid about my server being hacked! :p

---

### Post by Doug S on 2015-01-16
> **nicole9 said:**
> I obviously need to stop being so paranoid about my server being hacked!It is good to be diligent about your server and look at logs and such. You were quite right to ask about something that maybe didn't seem right.

---

### Post by pfeiffep on 2015-01-17
> **nicole9 said:**
> Ugh thank goodness!!! Thank you all!!! I obviously need to stop being so paranoid about my server being hacked! :pA carefully moderated dose of paranoia coupled with a quest for understanding will serve you well in keeping your computing safe!

---

