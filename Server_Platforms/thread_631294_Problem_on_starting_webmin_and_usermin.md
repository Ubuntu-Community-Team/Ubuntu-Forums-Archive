---
title: "Problem on starting webmin and usermin"
date: 2007-12-04
forum: Server Platforms
---

### Post by satimis on 2007-12-04
Hi folks,

Ubuntu 7.04 server amd64 (Host OS)
VMWare
CentOS 5 (Guest OS)


Webmin and Usermin are running on Ubuntu.  I can't start Webmin and Usermin on Firefox by running;

[https://localhost:10000](https://localhost:10000)
[https://localhost:20000](https://localhost:20000)

I must run;
[https://domain.com:10000](https://domain.com:10000)
[https://domain.com:20000](https://domain.com:20000)

to start them.


On console
$ sudo /etc/init.d/webmin restart```

Password:
Stopping Webmin server in /usr/share/webmin
Starting Webmin server in /usr/share/webmin

```
Webmin doesn't start


$ sudo /etc/init.d/usermin restart```

Stopping Usermin server in /usr/share/usermin
Starting Usermin server in /usr/share/usermin

```
Usermin doesn't start


Please help.  TIA


satimis

---

### Post by BillDozer on 2007-12-06
```
sudo /etc/init.d/xxxx restart
```
restarts the xxxx (fill in webmin or usermin) process.

Do you mean that the process won't start or that you cannot see the web interface.

[https://localhost:10000](https://localhost:10000) will only work from the local server, I expect you call it from firefox from you Guest OS and then you will have to specify the name of the server.

---

### Post by satimis on 2007-12-06
> **BillDozer said:**
> ```
sudo /etc/init.d/xxxx restart
```
restarts the xxxx (fill in webmin or usermin) process.

Do you mean that the process won't start or that you cannot see the web interface.

[https://localhost:10000](https://localhost:10000) will only work from the local server, I expect you call it from firefox from you Guest OS and then you will have to specify the name of the server.
Hi,


Thanks for your advice.


Problem already solved.  There was nothing wrong only iptables blocking the ports.  After running "sudo iptables -F" both webmin and usermin work locally and remotely.

I'm now searching for rules to be added on /etc/rc.local to accept ports for them.


B.R.
satimis

---

