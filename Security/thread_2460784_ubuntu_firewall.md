---
title: "ubuntu firewall  ?"
date: 2021-04-18
forum: Security
---

### Post by ubroot on 2021-04-18
sudo ufw default deny 


The ubuntu firewall only uses the above sentence.
Is it safe?

---

### Post by CharlesA on 2021-04-18
Here's what the [man page]("http://manpages.ubuntu.com/manpages/focal/man8/ufw.8.html") shows about that command:

> 
       **default allow|deny|reject DIRECTION**
              change  the  default  policy for traffic going DIRECTION, where DIRECTION is one of
              incoming, outgoing or routed. Note that existing rules will  have  to  be  migrated
              manually  when  changing  the  default policy. See RULE SYNTAX for more on deny and
              reject.

Verify you have the correct rules in place by running the following:

```
sudo ufw status
```

---

### Post by TheFu on 2021-04-19
For typical home users, it is sufficient.
There are exceptions for systems running network services. If you didn't specifically setup up a service, don't worry.

---

### Post by ipv2 on 2021-04-20
there is always the gui app if you wish to tweak the ufw :

```
sudo apt install gufw
```

---

