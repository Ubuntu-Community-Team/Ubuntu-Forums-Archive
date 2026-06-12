---
title: "eucalytpus server installation problem"
date: 2011-06-09
forum: Server Platforms
---

### Post by tushicomeng on 2011-06-09
I went through the documentation available online for installing eucalyptus through ubuntu enterprise edition. I have done it on ubuntu server 10.10 edition in a similar manner to the one explained for v10.04 in the article at the following link:
[http://cssoss.wordpress.com/2010/05/10/eucalyptus-beginner%E2%80%99s-guide-%E2%80%93-uec-edition-chapter-2-%E2%80%93-installation-%C2%A0configuration/](http://cssoss.wordpress.com/2010/05/10/eucalyptus-beginner%E2%80%99s-guide-%E2%80%93-uec-edition-chapter-2-%E2%80%93-installation-%C2%A0configuration/)

After making the changes in /etc/network/interfaces 
i.e., adding the specifications of eth1
Then restarting network, there is an error
> Failed to bring up eth1checked it using > ifconfig -a also.
It does not enlist eth1

 The details for eth1 on my network are:
auto eth1
iface eth1 inet static
address 10.10.10.55
netmask 255.255.255.0
netwotk 10.10.10.0
broadcast 10.10.10.255


What changes are required in eth1?
or there would be some mistake in my basic installation itself?

---

