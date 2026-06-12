---
title: "Open port on Ubuntu server 10.04 - Help"
date: 2011-04-22
forum: Server Platforms
---

### Post by Gasoile on 2011-04-22
Hi,

I have a Internet and FTP server running Zentyal configured with 2 ethernet adapters. The eth0 connects to a ADSL modem in bridge mode, using pppoe.
This server is running aMule as a service, but I got low ID. I need help to open the needed ports. I already tried to append rules on the iptables, but it didn't work :S

Thanks,
Gasoile

---

### Post by ruffEdgz on 2011-04-22
Remember, iptables doesn't open ports, it only allows or denies access to ports from a certain server.

I don't know much about Zentyal but depending on the FTP server its using, you should be able to change or open up other ports from the configuration files. Do you have access to the configuration web page for this Zentyal and can you change anything on the FTP side of thing? Does that FTP config page give you an option to open up additional ports?

Hit us up with more information if you can. Even though its based on Ubuntu 10.04, it would probably be better to ask the guys from Zentyal more about their product.

---

### Post by Gasoile on 2011-04-22
I have a web interface to control the zentyal and the port forwarding looks like the next image. If I want to run aMule in other computer, it's easy, just have to specify the port and the IP of the machine running it. The problem is that the aMule is runing inside the server and I don't know what to put in the destination IP. The ftp is vsftpd, but I don't know how that can be important to solve my problem... What kind of information should i give?

[IMG]http://img132.imageshack.us/img132/3231/screenshotnfx.png[/IMG]

---

### Post by bmathis on 2011-04-22
Destination IP will be the IP of the server on your network or 127.0.0.1 for localhost.

---

### Post by Gasoile on 2011-04-22
> **bmathis said:**
> Destination IP will be the IP of the server on your network or 127.0.0.1 for localhost.

I'v tried that too and nothing...
On the firewall log, I can see that all packets are dropped on aMule ports.

EDIT:

I think the destination IP should be the ppp0 IP that is the IP given from my ISP, but the problem is that it isn't static...
Maybe the problem is not from the port forwarding, because I can't access AMuleWeb from computers inside the local network, but it works on the server ([http://127.0.0.1:4711](http://127.0.0.1:4711)).

---

### Post by Gasoile on 2011-04-22
I found out that if I add the rule "ACCEPT any TCP and any UDP" on the Packet Filter (External networks -> Zentyal), it works, the problem is that all TCP and UDP ports are opened from the external network to my server :S.
Anny idea how to solve this without compromising the server's security?

---

### Post by ruffEdgz on 2011-04-25
Well that is good that you were able to just open up all the ports on your box but what you want to do it close all except port 21 (ftp port) and maybe 22 (ssh port). 

If you have the option to place in many Firewall rules, then it should be something like this:
> 
ACCEPT port 21 NEW TCP and port 22 NEW TCP
DROP any TCP and any UDP

Remember, this is sudo-code since I don't know exactly what Zentyal looks like but I hope that helps you move forward.

---

