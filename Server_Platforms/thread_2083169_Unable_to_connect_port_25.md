---
title: "Unable to connect port 25"
date: 2012-11-11
forum: Server Platforms
---

### Post by pietjuhklaas on 2012-11-11
Hey all,

I reinstalled my ubuntu 12.04 server today, and configured postfix. The problem is that i cannot connect to my postfix server on port 25 from outside my server. From the localhost it's no problem to connect. As att, my iptables, and master and main from postfix.

Thanx in advance

---

### Post by Doug S on 2012-11-11
Please provide your complete iptables rule set. The file you gave seems to be some small sub-set. What does the user chain "PAROLE" do?
Suggest you provide the output for this:```
sudo iptables -v -x -n -L
```
Note: I did not look at the other files.

---

### Post by lisati on 2012-11-11
Is your router set to forward requests on port 25 to your server?

---

