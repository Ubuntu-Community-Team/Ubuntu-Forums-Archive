---
title: "Can't disable ping."
date: 2010-09-15
forum: Security
---

### Post by epz on 2010-09-15
Hello everyone,

I realise that such a problem has been exposed (and somehow fixed) in the past but yet none of the solution google gave me hasn't worked.

I'm using ufw on ubuntu 10.04 and pinging myself even after editing before.rules to DROP icmp (ok i messed abit with after.rules too but that I know nothing there should compromise my icmp) results successfull, so far i can't state then if my firewall is really working (status says its enabled to deny from anywhere).

Any suggestions? I don't think its a bug, am I missing anything? How am i supposed to disable ping from ufw?

Odd enough I remember that after doing it on older versions it used to block ping.


thank you for any reply

---

### Post by Soul-Sing on 2010-09-15
via ufw  ```
/etc/ufw/before.rules
```
comment this line out via #
-A ufw-before-input -p icmp --icmp-type echo-request -j ACCEPT

disable and enable ufw and done

a slightly diff way and imho not correct: [https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)

---

### Post by FemmeFatale on 2010-09-15
You may just:

echo 1 >/proc/sys/net/ipv4/icmp_echo_ignore_all

and keep doing rest of your fw stuff using ufw.

Moreover, 

/etc/ufw/sysctl.conf:

#Ignore Broadcast
net/ipv4/icmp_echo_ignore_broadcasts=1

#Ignore ping
net/ipv4/icmp_echo_ignore_all=1

#No response to icmp bogus
net/ipv4/icmp_ignore_bogus_error_responses=1

---

### Post by epz on 2010-09-15
> **leoquant said:**
> via ufw  ```
/etc/ufw/before.rules
```
comment this line out via #
-A ufw-before-input -p icmp --icmp-type echo-request -j ACCEPT

disable and enable ufw and done

a slightly diff way and imho not correct: [https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)

tried it already and didn't disable ping.



> **FemmeFatale said:**
> You may just:

echo 1 >/proc/sys/net/ipv4/icmp_echo_ignore_all

and keep doing rest of your fw stuff using ufw.



i found this like after 5 minutes after i posted here, on gentoo handbook, well i thought, there must be a way to do it using ufw (since gentoo doesn't use ufw that i know)


> **FemmeFatale said:**
> You may just:

Moreover, 

/etc/ufw/sysctl.conf:

#Ignore Broadcast
net/ipv4/icmp_echo_ignore_broadcasts=1

#Ignore ping
net/ipv4/icmp_echo_ignore_all=1

#No response to icmp bogus
net/ipv4/icmp_ignore_bogus_error_responses=1

thanks that did it thank you very much

---

