---
title: "Squid server with two internet connections"
date: 2010-02-03
forum: Server Platforms
---

### Post by Ashishkhandelwal on 2010-02-03
Hi,

I have to configure squid server which will have two internet connections on two separate lan cards and both will run simultaneously.I know how to configure squid server with one internet connection but i have no idea about this problem so please help me in this regards.

Thanks in advance

---

### Post by Lars Noodén on 2010-02-03
Perhaps each interface has its own address.  

You should be able to set squid to listen to either address.  See the configuration directives [http_port ](http://www.visolve.com/squid/squid27/network.php#http_port) and [https_port](http://www.visolve.com/squid/squid27/network.php#https_port).

Which version of squid?  For Ubuntu 9.10 it is [Squid version 2.7](http://www.visolve.com/squid/squid27/contents.php).

---

