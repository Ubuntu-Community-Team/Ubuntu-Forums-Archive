---
title: "LAMP configured, never loads"
date: 2011-03-21
forum: Server Platforms
---

### Post by imaginarythomas on 2011-03-21
I've installed LAMP and all it's necessities and it works fine locally and on the local network. I was ready for primetime and set my router to forward http (port 80) requests to the correct machine but when I point a browser it's way it loads for 5 minutes and then throws a "too long to respond" error.

I tried canyouseeme.org and I can be seen but I can't seem to figure out this last issue. Can anyone help?

---

### Post by volkswagner on 2011-03-21
Have you tried from outside your LAN?

Have you checked log files?  /var/log/apache2/access.log and error.log

What does your host file look like?

---

### Post by imaginarythomas on 2011-03-21
1. [SEE EDIT]

2. What should I be looking for in these files?

3. 
```
192.168.0.80    qwfwq   # Added by NetworkManager
127.0.0.1       localhost.localdomain   localhost
::1     qwfwq   localhost6.localdomain6 localhost6
127.0.1.1       qwfwq

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```


EDIT: I was able to check from an outside source and it works! Could this be an issue with the hosts file on my local machine?

---

### Post by falko on 2011-03-21
I guess your router doesn't support loopbacks.

---

