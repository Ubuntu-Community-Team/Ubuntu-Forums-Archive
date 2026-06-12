---
title: "FTP and iptables"
date: 2016-08-02
forum: Security
---

### Post by Renaissance2011 on 2016-08-02
Hello buddies,

I have one question about ftp and iptables. I'm in trouble with my home server where i use Vsftpd software. Vsftpd uses standard ports 21 and 20. In iptables firewall i want to keep open ports 80, 443, 22, 21,20, 3306, 10000, 139, 11925, 445. All other ports are closed.

:INPUT ACCEPT [0:0]
:FORWARD DROP [0:0]
:OUTPUT ACCEPT [35431:98858756]
-A INPUT -m conntrack --ctstate RELATED,ESTABLISHED -j ACCEPT
-A INPUT -p tcp -m tcp --dport 80 -j ACCEPT
-A INPUT -p tcp -m tcp --dport 443 -j ACCEPT
-A INPUT -p tcp -m tcp --dport 22 -j ACCEPT
-A INPUT -p tcp -m tcp --dport 20 -j ACCEPT
-A INPUT -p tcp -m tcp --dport 21 -j ACCEPT
-A INPUT -p tcp -m tcp --dport 3306 -j ACCEPT
-A INPUT -p tcp -m tcp --dport 10000 -j ACCEPT
-A INPUT -p tcp -m tcp --dport 139 -j ACCEPT
-A INPUT -p udp -m udp --dport 139 -j ACCEPT
-A INPUT -p tcp -m tcp --dport 11925 -j ACCEPT
-A INPUT -p tcp -m tcp --dport 445 -j ACCEPT
-A INPUT -j LOG
-A INPUT -j DROP
For some reason the firewall will not allow the use ftp. The question is what is wrong ?

---

### Post by Habitual on 2016-08-02
ufw enabled?

---

### Post by HermanAB on 2016-08-07
FTP only uses port 21 to negotiate and establish the connection.  During this process, it negotiates a random high port for the actual data transfer.  Therefore, if you block all the high ports then FTP won't work.

---

### Post by ghb321-gmail on 2016-08-21
FTP use 21 port only in passive mode, in active mode ftp use range of port adresses. So it depends of your proftpd.conf. In file you should have range property that you can change and fit to your iptables.

Acording to:
[https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers)

you should:

[COLOR=#000000]-A INPUT -p tcp -m tcp --dport 20 -j ACCEPT[/COLOR]
[COLOR=#000000]-A INPUT -p tcp -m tcp --dport 21 -j ACCEPT

and:

[/COLOR][COLOR=#000000]-A INPUT -p upd -m udp --dport 20 -j ACCEPT[/COLOR]
[COLOR=#000000]-A INPUT -p [/COLOR][COLOR=#000000]upd[/COLOR][COLOR=#000000] -m udp --dport 21 -j ACCEPT

and change /etc/proftpd/proftpd.conf[/COLOR]

---

### Post by HermanAB on 2016-08-21
Iptables also has a FTP connection tracker that can be used to follow the negotiation and open the required high port automatically.

---

