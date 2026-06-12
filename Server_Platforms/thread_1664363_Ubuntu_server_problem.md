---
title: "Ubuntu server problem"
date: 2011-01-10
forum: Server Platforms
---

### Post by BradNowacki on 2011-01-10
Alright so i think im connected to the internet, but when i try apt-get anything or apt-get update i get this (W: Failed to fetch (insert URL here) Temporary failure resolving (insert URL)

i dont know what to do about it any help?

---

### Post by samosamo on 2011-01-10
"failure resolving" means bad DNS config, post yours

---

### Post by stlsaint on 2011-01-10
1. Are you connected to a router?
2. Have you obtained a ipaddress? (192.168.X.XXX)
3. Can you ping out from the router?
command:
```

ping -c 4 www.google.com

```
4. Post the output of your resolv.conf
command:
```
cat /etc/resolv.conf
```

---

### Post by Rennek on 2011-01-11
I am having the same issue as the OP. On a fresh 10.10 Ubuntu server install I am able to ping the router and the box is pulling an IP address. When I check the resolv.conf it is also pulling the nameserver and correct domains from my ISP. However nothing resolves, be it google, cnn, or the Ubuntu repositories. Other computers on the network (be they Linux or Windows) are working dandy. Not new to Linux but apparently new enough to not figure this one out, any ideas?

Edit: Fixed it. A quick reboot sorted it out.

---

