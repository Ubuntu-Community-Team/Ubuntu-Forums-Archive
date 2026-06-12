---
title: "Uec/privat cloud"
date: 2011-09-28
forum: Ubuntu Cloud and Juju
---

### Post by XquisiteBee on 2011-09-28
Hi,
 
[LEFT]I am new to Ubuntu and UEC and therefore requesting assistance from anyone who may have the answer to my problem.

I installed the CLC, CC, Walrus and Storage from a UEC/CD yesterday but noticed that today the IP Address for the CLC is different from yesterday, which was ".67" instead of ".65".  To add to that, the walrus is coming up as not being registered.  The exact message that is flagged is: 

**"(error 1): command attempted was "/usr/sbin/euca_conf --no-rsync --skip-scp- hostcheck --register-walrus 192.168.1.65**

[B]ERROR: failed to register Walrus, please log in to the admin interface and check cloud status."
[/B]
Can anyone please advise as to what I can do to rectify the problem?


Many thanks in advance




[/LEFT]

---

### Post by lcman on 2011-10-06
Are you using DHCP? Not really a good ideas for servers! You need to set the IP address back to .67 I think. Here's a nice tutorial:
```
http://www.cyberciti.biz/tips/howto-ubuntu-linux-convert-dhcp-network-configuration-to-static-ip-configuration.html
```

---

### Post by XquisiteBee on 2011-10-08
Thanks Icman for you response!

---

