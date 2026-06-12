---
title: "Securing Ubuntu Desktop for php development(Xampp based)"
date: 2010-09-23
forum: Security
---

### Post by uuhelp on 2010-09-23
Hi,


     Just installed Ubuntu 10.4 Desktop and installed Xampp over it for php development.


I have a few security questions. Hopefully someone here can help me out with them here.


So, what i've done until now is :

1)Enabled ufw 

2) Set the default to deny all incoming connections (sudo ufw default deny)


Now when i start the Xampp service and run the port scan on my pc (private address 192.168.1.2), it displays the state of following ports as /services as open:

21/ftp
80/www
443/https
3306/mysql

and sometimes some random ports as well but with no service running on them.



My question are:


1) Would these ports/services still be available/open over the internet even if i have set the default value for ufw to deny all incoming connections.

2)On doing a port scan on my adsl router(192.168.1.1) it too shows the ftp/telnet/www ports as open.  Does that mean that adsl router does not have a Firewall configured?  So in that case is my desktop still secure even if the built in hardware firewall in the ADSL is not working but the software firewall(ufw) is.



I am doing both of the above scans from my own pc(over my own internal network running a wireless Lan)... Would a scan from the external network(over the internet) show them as closed.  I have no way of verifying since i don't have another service/connection to the internet.



3)How to keep a Xampp installation secure on my desktop so that none of the services are available over the internet but just to me?


4)Do i really need to deny any outgoing connections/traffic to keep my desktop secure?


All help is much appreciated.

---

### Post by spynappels on 2010-09-23
For a port scan to work, it has to be done from outside your LAN, else it will not take the firewall into account. I'm fairly sure you are fine.

---

### Post by uuhelp on 2010-09-23
Thanks Spynappels, hopefully i'm secure.  Would be nice if someoen addresses the rest of my dbouts providing some explaination for them.

---

### Post by cariboo on 2010-09-23
If you are running behind a router, don't forward any ports, If you have another computer on your network, run a port scan from it. The default iptables rules that are setup when you run:

```
sudo ufw enable
```

are enough for what you are doing.

This is what I get when I scan my netbook with ufw disable:

```
sudo nmap -PN 192.168.1.102

Starting Nmap 5.21 ( http://nmap.org ) at 2010-09-23 09:54 PDT
Nmap scan report for 192.168.1.102
Host is up (0.0012s latency).
Not shown: 999 closed ports
PORT    STATE SERVICE
111/tcp open  rpcbind
MAC Address: 90:4C:E5:41:E4:2F (Hon Hai Precision Ind. Co.)

Nmap done: 1 IP address (1 host up) scanned in 6.98 seconds
```

And this is what I get with ufw enabled:

```
sudo nmap -PN 192.168.1.102

Starting Nmap 5.21 ( http://nmap.org ) at 2010-09-23 09:54 PDT
Nmap scan report for 192.168.1.102
Host is up (0.0023s latency).
All 1000 scanned ports on 192.168.1.102 are filtered
MAC Address: 90:4C:E5:41:E4:2F (Hon Hai Precision Ind. Co.)

Nmap done: 1 IP address (1 host up) scanned in 21.32 seconds

```

---

