---
title: "wget unable to resolve host address"
date: 2013-02-07
forum: Server Platforms
---

### Post by leechbee on 2013-02-07
i tried to install rutorrent in **vps**, but i am not able to use wget or anything...


```
--2013-02-08 02:04:57--  http://sourceforge.net/projects/autodl-irssi/files/autodl-setup/download
Resolving sourceforge.net (sourceforge.net)... failed: Temporary failure in name resolution.
wget: unable to resolve host address `sourceforge.net'
```


Tried this command too
**wget [www.google.com](www.google.com)**

```
--2013-02-08 02:02:37--  http://www.google.com/
Resolving www.google.com (www.google.com)... failed: Temporary failure in name resolution.
wget: unable to resolve host address `www.google.com'
```


Note:
even i got wget error in centos too.

---

### Post by SeijiSensei on 2013-02-07
You don't have any DNS servers defined.  If you get the network configuration automatically at start up, then the device handing out addresses and such, like a wifi router, needs to be configured with the identity of at least one and preferably a couple of servers.  If you've set up your addresses statically with NetworkManager or by editing /etc/network/interfaces, you need to specify the DNS servers there.  

If this is a virtual machine, your provider should be handling all this for you. Read their documentation or ask them.

---

### Post by Vegan on 2013-02-07
try googles free public servers and add them to the forwards pool

8.8.8.8
8.8.4.4

you can find lots of free DNS servers out there, I use lots of them on my appliance

---

