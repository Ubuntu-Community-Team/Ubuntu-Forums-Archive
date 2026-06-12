---
title: "Permission denied"
date: 2011-05-07
forum: Ubuntu Cloud and Juju
---

### Post by viswacse02 on 2011-05-07
Hi,

cloud@cloud:~$ sudo iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
[sudo] password for cloud: 
[B]cloud@cloud:~$ echo 1 > /proc/sys/net/ipv4/ip_forward
bash: /proc/sys/net/ipv4/ip_forward: Permission denied
cloud@cloud:~$ sudo echo 1 > /proc/sys/net/ipv4/ip_forward
bash: /proc/sys/net/ipv4/ip_forward: Permission denied


What i should do?
[/B]

---

### Post by mr_luksom on 2011-05-07
What exactly are you trying to do?

You are getting 'permission denied' because you are writing outside of the user cloud's userspace. You could use a suds command, but you can do damage if you are unsure of what you are changing.

I've never had to write anything to proc before, maybe there is another way?

---

### Post by kim0 on 2011-05-10
Yeah, make sure you understand what you're doing, other than that use 'sudo -i' to get a root shell, then use your echo commands
Good luck

---

