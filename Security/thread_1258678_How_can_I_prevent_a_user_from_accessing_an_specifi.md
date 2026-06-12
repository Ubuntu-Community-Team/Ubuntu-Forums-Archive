---
title: "How can I prevent a user from accessing an specific network interface?"
date: 2009-09-05
forum: Security
---

### Post by legolas_w on 2009-09-05
Hi
Thank you for reading my post, can someone please let me know how I can prevent a user from accessing an specific network adapter (interface)?

My computer has two network interfaces and I want to make sure that second user has no access to that interface.


PS: this is a cross post from [http://ubuntuforums.org/showthread.php?t=1258237](http://ubuntuforums.org/showthread.php?t=1258237) I though I may have better chance to get the answer here instead of beginners forum.

Thanks

---

### Post by bodhi.zazen on 2009-09-05
You can do this with iptables

```
sudo iptables -A INPUT -i eth0 -m owner --uid-owner 1001 -j DROP
sudo iptables -A OUTPUT -o eth0 -m owner --uid-owner 1001 -j DROP
```

get your users id from the command id

---

### Post by Old_Grey_Wolf on 2009-09-05
> **bodhi.zazen said:**
> You can do this with iptables

```
sudo iptables -A INPUT -i eth0 -m owner --uid-owner 1001 -j DROP
sudo iptables -A OUTPUT -o eth0 -m owner --uid-owner 1001 -j DROP
```

get your users id from the command id

To change which interface is blocked change eth0 to eth1 or wlan or whatever it is labeled in your Linux version.

Replace 1001 in the command with the userid you want to block.

You can read about other iptables capabilities or understand the command at this site [http://linux.die.net/man/8/iptables](http://linux.die.net/man/8/iptables) easier to read than using man in terminal.

---

