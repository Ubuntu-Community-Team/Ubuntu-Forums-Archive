---
title: "Which process tries to open a network connection"
date: 2007-12-15
forum: Server Platforms
---

### Post by ubernoob on 2007-12-15
My computer tries to connect to a strange server on port 80, which is blocked by a firewall, since all connections should go trough the proxy. The packet dump shows that it is only SYN-packets that are sent. 

How do I find out which process this is? I also have the src port, so i guess its just a simple command I don't know about!

---

### Post by bnuytten on 2007-12-15
The command you are looking for is netstat. The following command will give you all (a) existing tcp connection (t) in numeric form (n) and if possible the process (p) that is responsible for the connection. Note the state of the connection, not all connections will be "ESTABLISHED".
```
netstat -tanp
```

For udp, you can use -u. For both tcp and udp, you may use for instance ```
netstat -tuanp.
```

PS: you should be root to execute this command or you may not see all processes/connections. Not sure about this though.

---

### Post by ubernoob on 2007-12-15
Excelent! I found the process, and it was a crontab i had made myself! wget failed since it was not set up with proxy. Thanks alot!

---

