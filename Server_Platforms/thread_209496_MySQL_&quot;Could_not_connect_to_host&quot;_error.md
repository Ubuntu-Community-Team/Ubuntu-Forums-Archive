---
title: "MySQL &quot;Could not connect to host&quot; error"
date: 2006-07-05
forum: Server Platforms
---

### Post by loftx on 2006-07-05
Hi all, I hope this is the best forum to discuss my problem in.

I'm running MySQL and want to be able to connect to it from other machines on my local network i.e. 192.168.*.*, but for some reason I get the error "Could not connect to host" when I try to connect using the machine's  IP - even from that machine!

I've tried connecting to "localhost" and "127.0.0.1" and they both work fine, but when I use the machine's own IP "192.168.0.4" I get this error - can anyone help?

Thanks.

---

### Post by loftx on 2006-07-05
I've managed to find out what was going on here. By default MySQL only listens on TCP/IP for connections from the localhost. To enable other connections:

Edit the config file and comment out the bind-address line

```
sudo gedit /etc/mysql/my.cnf
```

Then restart MySQL and it should accept connections from the local network

```
sudo /etc/init.d/mysql restart
```

---

