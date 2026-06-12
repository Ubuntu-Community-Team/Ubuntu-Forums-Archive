---
title: "UFW not working as expected on an arm dedicated server"
date: 2015-10-08
forum: Security
---

### Post by tsk1979 on 2015-10-08
I am running a VPS
Distributor ID: Ubuntu
Description:    Ubuntu 14.04.2 LTS
Release:        14.04
Codename:       trusty

I decided to lock down the system with ufw
Here are the steps I do
sudo ufw default deny incoming
sudo ufw allow 22/tcp
sudo ufw enable
At this point, I just get locked out of server. Existing connection is flushed, and port 22 also stays blocked.
I am trying to setup a rule so that from outside, all ports except 22 are blocked, but internally from localhost itself I can connect to any port.

---

### Post by Doug S on 2015-10-10
Disclaimer: I do not use ufw.

ufw is just a front end for iptables, so you should be able to determine what is wrong by observing the resulting iptables rule set. do "sudo iptables -v -x -n -L".
Myself, instead of:
```
sudo ufw default deny incoming
sudo ufw allow 22/tcp
sudo ufw enable
```I would try this:```
sudo ufw allow 22/tcp
sudo ufw default deny incoming
sudo ufw enable
```

---

### Post by Doug S on 2015-10-11
You have changed the status of this one to "SOLVED". For the benefit of others, would you care to share what the solution was?

---

### Post by tsk1979 on 2015-10-12
> **Doug S said:**
> You have changed the status of this one to "SOLVED". For the benefit of others, would you care to share what the solution was?
Solution was exactly what you said. I changed the order, and it worked!

---

