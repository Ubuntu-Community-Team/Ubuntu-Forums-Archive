---
title: "What is my firewall doing?"
date: 2006-08-08
forum: Server Platforms
---

### Post by loonsailor on 2006-08-08
I'm trying to connect to an application that requires a few unusual ports and, for some reason, they seem to be blocked.  I am running 6.06, desktop version, and I never intentionally configured a firewall (since I've got a netscreen between my linux box and the world).

Here's what I don't understand.  The firewall seems to be passing everything through:

[INDENT]sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
[/INDENT]
but nmap shows that some ports are closed and/or filtered.  When I run it while the server application is running, I get:
[INDENT]
sudo nmap -sU -sT -p "T:1099,T:7288,U:5353,T:1527,U:2190,T:8081" localhost

Starting Nmap 4.03 ( [http://www.insecure.org/nmap/](http://www.insecure.org/nmap/) ) at 2006-08-08 10:37 PDT
Interesting ports on localhost (127.0.0.1):
PORT     STATE         SERVICE
1099/tcp open          unknown
1527/tcp open          tlisrv
2190/udp open|filtered unknown
5353/udp open|filtered unknown
7288/tcp closed        unknown
8081/tcp closed        blackice-icecap
[/INDENT]

If I run it with the server application stopped, I get:

[INDENT]Starting Nmap 4.03 ( [http://www.insecure.org/nmap/](http://www.insecure.org/nmap/) ) at 2006-08-08 10:57 PDT
Interesting ports on aparicio (192.168.198.211):
PORT     STATE  SERVICE
1099/tcp closed unknown
1527/tcp closed tlisrv
2190/udp closed unknown
5353/udp closed unknown
7288/tcp closed unknown
8081/tcp closed blackice-icecap

Nmap finished: 1 IP address (1 host up) scanned in 0.188 seconds
[/INDENT]

What is happening?  And what is blackice-icecap. Neither synaptic nor "man -k blackice" turns up anything.

I'm running nmap on the machine being tested, and either "localhost" or the external IP address gives the same results.

Thanks for the help.

---

### Post by jkrishnaswamy@comcast.net on 2006-08-11
It is a security program. I am not sure how it came into my computer and I suspect it was originally bundled. It seems to like the 8081 and 8082 ports. I have not tried the other ports. This may very well be linked with VS 2005 failing to create a web reference for the SQL 2005 Server.

---

