---
title: "how to disable the ping"
date: 2012-01-14
forum: Security
---

### Post by Fertech on 2012-01-14
I want to disable ping, I don't want anybody trying to ping me, If I need to use it I can always 
enable it.

---

### Post by mattxhand on 2012-01-15
On your local machine or on a network-wide scale?

To disable ping response:
echo 1 >/proc/sys/net/ipv4/icmp_echo_ignore_all

To reenable:
echo 0 >/proc/sys/net/ipv4/icmp_echo_ignore_all

---

### Post by Doug S on 2012-01-15
I only use iptables, without any frontend stuff such as ufw. Here is the iptables rule to drop echo requests:```
iptables -A INPUT -p icmp --icmp-type 8 -j DROP
```Myself, I prefer to leave echo requests enabled as the most basic debug tool in the event of network troubles.
 
Hope this helps.

---

### Post by hackertarget on 2012-01-15
Of course if you are refering to a home Internet connection with a NAT'd router. You will have to DROP icmp on the router to block external ping to your public IP. Look for an option in the router settings page.

[Test Ping]("http://ping-test.org")

---

