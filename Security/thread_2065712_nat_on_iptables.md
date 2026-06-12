---
title: "nat on iptables"
date: 2012-10-02
forum: Security
---

### Post by Leo Matheus on 2012-10-02
im tring to make a nat, so i create a rule to test:

iptables -t nat -I PREROUTING -p icmp -s 192.168.XX.yy -d 192.168.XX.zz -j DNAT --to 192.168.ZZ.xx

and them i ping the nat machine to see if its is working, but when i ue wireshark to check the 2 interfaces. The fist show the icmp request,but in the other is not showing anything. any idea what could be?

im new on iptables, so a really need some help.

---

### Post by CharlesA on 2012-10-02
See here:
[http://www.revsys.com/writings/quicktips/nat.html](http://www.revsys.com/writings/quicktips/nat.html)

---

### Post by Doug S on 2012-10-02
I guess CharlesA replied while I was away trying to figure out a reply. Anyway...
 
If your default policy for your FORWARD chain is DROP, then you will also need to define a path through the FORWARD chain. I tested this on my computer. I think you would need:```
iptables -A FORWARD -p icmp -s 192.168.XX.yy -d 192.168.ZZ.XX -j ACCEPT
```Note that I am using the DNAT'd address for the destination above.
If your FORWARD chain default policy is ACCEPT then I do not know why it is not working.

---

### Post by Leo Matheus on 2012-10-04
Well, its works!
really thank charlie for the great tutorial, and thanks doug for that tip, i have used to create some rules for make it work.

thanks you guys!:D

---

### Post by Doug S on 2012-10-04
Glad you got it sorted out. And thanks for reporting back.

---

