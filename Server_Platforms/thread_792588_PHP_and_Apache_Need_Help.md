---
title: "PHP and Apache Need Help"
date: 2008-05-13
forum: Server Platforms
---

### Post by Zeck on 2008-05-13
Hi all,
I have a server problem on Ubuntu 8.04. When my internet broken my php didn't work. When internet connected, it works. My webroot located in /var/www. How to solve this problem. Please help me !


Sorry poor English.

---

### Post by p_quarles on 2008-05-13
Can you post the output of the following commands?
```
cat /etc/network/interfaces
```
and
```
cat /etc/apache2/ports.conf
```
Not sure those would have anything to do with the problem, but it's one place to start. Basically, the problem sounds like it's related to the loopback network device ("lo" or "localhost") not working correctly.

---

