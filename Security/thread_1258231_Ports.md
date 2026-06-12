---
title: "Ports"
date: 2009-09-04
forum: Security
---

### Post by starbright on 2009-09-04
Hello,

I just installed Xubuntu and was wondering if there are any ports open by default and how one can check which ports are open?

---

### Post by rookcifer on 2009-09-04
```
sudo netstat -atpvnl
```

This should show all TCP ports where a service is active and listening.

You could also try:

```
lsof -i
```

---

### Post by bear24rw on 2009-09-04
> **rookcifer said:**
> ```
sudo netstat -atpvnl
```


Thats a nice command thanks!

---

### Post by sasho_zl on 2009-09-05
Also make an online scan of the service ports. You can try that one - [http://nmap-online.com/](http://nmap-online.com/)

---

### Post by The Cog on 2009-09-05
> **sasho_zl said:**
> Also make an online scan of the service ports. You can try that one - [http://nmap-online.com/](http://nmap-online.com/)

That will of course just scan your public address. You should be aware that it will be scanning your router if you have one, and not your PC.

---

### Post by bodhi.zazen on 2009-09-05
I like the following :

```
netstat -an | grep LISTEN | grep -v ^unix
netstat -ntulp
lsof -i -n -P
```

---

### Post by starbright on 2009-09-06
Thanks! But now I have another question. I was wondering if all of the ports in Xubuntu are closed with a standard desktop installation, except those that are used for services. Because I know that in windows, every port is open and you have to install a firewall to block everything off. Do I have to do something similar in Xubuntu, or are all of the ports closed?

---

### Post by chandru155 on 2009-09-06
By Default All the ports in Ubuntu(All variants) are closed. If you want, u can open them using ufw(or gufw).

---

### Post by starbright on 2009-09-06
Thank you!

---

### Post by cariboo on 2009-09-07
Ufw will not open ports for you, ports are opened when you install a service eg: by default apache2 runs on port 80, you would use ufw to disallow connections to port 80.

---

### Post by chandru155 on 2009-09-07
Yes. Caribo is right.

---

### Post by __p1n__ on 2009-09-07
If you want to be doubly certain then go to a different computer on the network and do nmap SYN and UDP scans against the host.

---

