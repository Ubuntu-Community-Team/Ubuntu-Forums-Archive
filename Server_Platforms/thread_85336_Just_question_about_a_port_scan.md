---
title: "Just question about a port scan"
date: 2005-11-02
forum: Server Platforms
---

### Post by zappa86 on 2005-11-02
I'm running 5.04.
I wanted to see how open my system was so I did a port scan on myself from another computer. The ports opened were:
25 smtp
80 www
111 sunrpc
139 netbios-ssn
445 microsoft-ds
631 ipp
710 unknown

I know what port 80 is for, but are the other ports a problem. Does anyone know what their used for and how to close them. Thanks.

---

### Post by Dr. Nick on 2005-11-02
25 is mail server
139 is Windows File Sharing
631 is printer I believe

By default I believe all ports should be closed, so those that are open are due to installing programs after. You can either find and disable the services behind them, For example disable samba for the file sharing , and cups for the printer port. Or install firestarter and configure the iptables firewall to block all ports and only open port 80 if needed. After setting firestarter up you can close it and leave it closed, It modifies the built in firewall and doesnt need to be running all the time, Then try another port scan

---

### Post by dbee on 2005-11-04
445 microsoft CIFS
111 portmapper
710 ????


check /etc/services for a list of ports OP

---

### Post by Biased turkey on 2005-11-09
[QUOTE=Dr. Nick]
631 is printer I believe

[/QUOTE]

Yes, cups uses the port 631

---

### Post by guipipia on 2005-11-13
You can find the "official" well know port number assignment here:

[http://www.iana.org/assignments/port-numbers](http://www.iana.org/assignments/port-numbers)

Pura Vida!

---

### Post by rhaurison on 2005-11-15
[QUOTE=zappa86]I know what port 80 is for, but are the other ports a problem. Does anyone know what their used for and how to close them. Thanks.[/QUOTE]

for 710, use netstat -natp |grep 710 OR  "lsof -i tcp |grep LISTEN"  to know what are using this...

---

### Post by jdong on 2005-11-15
[QUOTE=zappa86]
25 smtp
[/quote]
Mail server, for sending mail over the network. Not necessary -- how did you configure this one??? 

> 
80 www

Web server, like Apache. Keep it patched, install secure software on it, and you'll be fine.

> 
111 sunrpc
139 netbios-ssn
445 microsoft-ds

For Samba (Windows File Sharing), having other machines access yours via Windows File sharing.
> 
631 ipp

CUPS, the print server. Use it if you need to print to this machine remotely over the network.
> 
710 unknown

Umm, no idea!


Is this system over a LAN (i.e. behind a router)? Is it directly hooked up to the Internet?

---

