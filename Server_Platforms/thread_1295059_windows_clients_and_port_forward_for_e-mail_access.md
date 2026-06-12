---
title: "windows clients and port forward for e-mail access"
date: 2009-10-19
forum: Server Platforms
---

### Post by kyo21 on 2009-10-19
Hello everyone, I am new to the forum and wanted to submit to you a problem with a ubuntu (9.04) PC.  
 This has 2 network interfaces.  

 eth0 (192.x.x.x) connected to a router with a direct access to the internet;  
 eth1 (10.x.x.x) connected to a switch with others Windows clients on the LAN.  

 The PC is therefore a server, sharing (on eth1) a set of resources and, through squid, even the Internet connection.  
 So far so good, except that with only squid, I can not allow the Windows clients (always connected on eth1) to receive and send e-mail. 

 Can someone help me solve this problem? They told me that I should configure "iptables" for forwarding ports 25 and 110, but I don't know how :confused:. 

 I thank everyone in advance for all :)

---

### Post by crazyasyou on 2009-10-19
sounds to me like you have setup squid to proxy the web traffic but your machine is not a gateway so its not really sharing the internet as such.

You will need to setup iptables and ip forwarding to ensure NAT is working.

I'm new to linux myself but have pretty good networking skills, you might find iptables a steep learning curve, I think google will be your friend alone with a few pages from ubuntu

try these to get you started

[https://help.ubuntu.com/9.04/serverguide/C/firewall.html](https://help.ubuntu.com/9.04/serverguide/C/firewall.html)

[https://wiki.ubuntu.com/UbuntuFirewall](https://wiki.ubuntu.com/UbuntuFirewall)

[http://www.linuxjournal.com/article/3866](http://www.linuxjournal.com/article/3866)

---

### Post by kyo21 on 2009-10-19
Thanks. I'm trying to configure the firewall.  
 Outcome will inform you

---

### Post by kyo21 on 2009-10-20
> **kyo21 said:**
> Thanks. I'm trying to configure the firewall.  
 Outcome will inform you
I'm trying to configure the firewall with firestarter, but without succes :confused:.
Can you help to build the port forwarding for SMTP and POP3?
Thanks :)

---

