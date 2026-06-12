---
title: "UFW and Virtualbox"
date: 2014-09-22
forum: Security
---

### Post by welefort on 2014-09-22
I have a server running in Virutalbox that hosts a simple nginx server, in bridged networking.  It only needs to be accessed by one outside Ip address on port 80.


The ufw on the VM is currently set to allow connections to port 80 from anywhere.  I'd like to restrict that to only allow from  one specific IP address.     How can I do that with ufw?  Something along the lines of 

```
sudo ufw allow from 1.1.1.1 only to port 80.


```

---

### Post by thnewguy on 2014-09-22
Try
```

sudo ufw allow 1.1.1.1 in 80/tcp

```

By default UFW blocks all incoming connections, so you only need to specify the address/port you wish to allow.

---

