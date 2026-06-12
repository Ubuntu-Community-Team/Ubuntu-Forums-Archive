---
title: "DHCP general question"
date: 2010-01-22
forum: Server Platforms
---

### Post by --Steve on 2010-01-22
I'm going to load ubuntu server to a computer just for testing and learning.   There is one ethernet card on this computer that will only be used occasionally to connect to the internet.  This computer will not have any computers or routers connected to it.  

So my question is, once installed and running, will DHCP just sit quietly and wait for a request or is it going to complain a lot that it is not finding any other computers?

---

### Post by kiranmurari on 2010-01-22
Are you talking about setting up a DHCP Server or a DHCP Client?

---

### Post by --Steve on 2010-01-22
Thank you kiranmurari for the reply.   

It is the default installation of "DHCP server" for the ubuntu server edition 9.04.    

I just want to know how the default installation of the DHCP server will behave once installed on a computer with no other computer or routers.  I also wonder if it will be sending requests to my ethernet card when I am connected to the internet.   

Thank you sir for the reply!

---

### Post by kiranmurari on 2010-01-22
Installing DHCP server (sudo apt-get install dhcp3-server) alone is not sufficient. You need to have a valid DHCP configuration file (/etc/dhcpd.conf). If a valid dhcp.conf file is not found, the server wouldn't run at all. For more details on setting up a DHCP server, please refer the following link: [https://help.ubuntu.com/community/dhcp3-server](https://help.ubuntu.com/community/dhcp3-server)
       
Assuming you have a working DHCP server, the server will not send any requests. But will simply wait for a DHCP request from a client, say from a host running dhclient.
       
If you intend to learn about DHCP and other network services, installing VirtualBox ([http://virtualbox.org]("http://virtualbox.org/")) will give you the ability to run multiple VMs, using which you can simulate and test various scenarios.

---

### Post by adam814 on 2010-01-22
+1

Set up a whole little network in VirtualBox if you like.  It's a great way to learn how network services work without downing the network on your host accidentally.

---

