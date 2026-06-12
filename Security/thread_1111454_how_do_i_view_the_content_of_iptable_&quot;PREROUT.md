---
title: "how do i view the content of iptable &quot;PREROUTING&quot;"
date: 2009-03-30
forum: Security
---

### Post by firsttimeuser on 2009-03-30
I wrote some rules using 

iptables -A PREROUTING x.x.x.x.x

and 

iptables -A POSTROUTING X.X.X.X

and iptables -L -vn does not show anything, what is the command to list the rules I just appended into the chains? thanks

---

### Post by bodhi.zazen on 2009-03-30
sudo iptables -L -vt nat

---

### Post by firsttimeuser on 2009-03-30
thanks a lot!

---

