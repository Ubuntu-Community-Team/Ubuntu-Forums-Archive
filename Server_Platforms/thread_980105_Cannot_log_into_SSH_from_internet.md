---
title: "Cannot log into SSH from internet"
date: 2008-11-12
forum: Server Platforms
---

### Post by rkovvur on 2008-11-12
I installed the ubuntu server edition (8.10) and installed open-ssh server. I can access it great from my local network. I even changed its listening port to 81 from 22. 

Now i used a website that tells me which ports are blocked and which are not by my isp. I found that port 81 was not blocked. 

But when i use putty to ssh from the internet to my ubuntu box on port 81, it just times out. Any idea whats going on?

FYI: I did port-forward port 81 in my router. I can access my apache server over port 80 okay from the net, but not ssh. 

help !! 

-raj

---

### Post by hictio on 2008-11-12
Maybe obvious, but, we have to start somewhere...
Did you restarted the sshd daemon after changing the port, right?

---

### Post by rkovvur on 2008-11-12
yup

---

### Post by HermanAB on 2008-11-12
Test it with telnet:
$ telnet localhost 81

then
$ telnet pcipaddress 81

finally 
$ telnet routerpublicipaddress 81

By then you should have an idea of what is wrong where.

Cheers,

Herman

---

### Post by martien on 2008-11-12
Do you have configured firewall? Maybe its blocking port 81

---

### Post by Dr Small on 2008-11-12
In your router, you need to forward port 81 to port 81 of the local machine running the SSH daemon. It isn't necessary to change the listening port if you are behind a router, as you can set the router up to forward the public port (81) to the private port (22).

---

