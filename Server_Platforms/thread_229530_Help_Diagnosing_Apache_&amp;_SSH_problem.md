---
title: "Help Diagnosing Apache &amp; SSH problem"
date: 2006-08-04
forum: Server Platforms
---

### Post by mabase on 2006-08-04
Problem: I am unable to connect to my apache2 server or through SSH from outside my LAN.  I am also unable to isolate where the problem is since I cant tell if its a problem with my router, ubuntu, or apache2/SSH.  Whenever I try to connect my web browser says refused by host (using FireFox).  And when I try to connect via SSH using the command user@ipaddress it says connection refused.

Situation: Trying to connect to the Apache2 server on Latop with Ubuntu.  The laptop is connected to the router via Wireless (with a strong signal strength since its about 5 ft away.)

Things I have done/accomplished:
- I have installed Apache2 and the open ssh server
- I am able to connect locally to the Apache2 server and to the laptop through SSH.
- I have set up my router to forward the ports 22 and 80 to my Laptop's static IP address.
- I have tried setting up the free domain name from no-ip.com and I have installed the software that should update no-ip with my new public IP address provided by verizon.
- I know port forward is working on my router since bittorent will only work with the ports forwarded.  Also, with port 22 forwarded to my laptop, I am only able to connect via SSH from desktop to laptop and not laptop to desktop.
- Both the Laptop and Desktop are connected to the Internet via a router
- I have tried installing Firestarter and opening the ports on the laptop


I would love some help.  And if you don't know what my problem is, I would like it if someone could tell me a way to figure out how far the packets get before they get denied, or how to somehow check to see if my laptop is even recieving the SSH packets.

---

### Post by Kurt` on 2006-08-04
Behind your router, you can connect to machines using their private IPs (e.g. 192.168.0.105:22 instead of using your ISP-assigned address).

# netstat -an | grep LISTEN

will display everything that is listening. e.g.

tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:80            0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:443             0.0.0.0:*               LISTEN

are my SSH and HTTP/HTTPS (apache) daemons.

0.0.0.0 means it's bound to listen on every interface (so it can answer requests locally, and from your LAN).

If your services are listening on the correct interfaces/ports, simply double check that your ports are forwarded to the correct IP (run "ifconfig" and look at eth0's IP).

That's really all there is to it.

---

### Post by mabase on 2006-08-04
I got
tcp6       0      0 :::80                   :::*                    LISTEN
tcp6       0      0 :::22                   :::*                    LISTEN

but I didnt get an HTTPS one 443, could that be a problem?  Also I noticed that it says tcp6, does that mean IPv6?

---

### Post by mabase on 2006-08-04
Ahh I finaly managed to solve my problem!  It was a problem with my router, although I had port forwarding selected correctly, apparently the dns server didn't know to send requests directed to my public address to my private LAN address.  Now everything seems to work.

---

### Post by Sam on 2006-08-05
Although you solved your problem, here is something useful:

[list][*]To test TCP ports of a remote computer:```
$ nmap <ip address>
```
If you don't have nmap:```
$ sudo apt-get install nmap
```

[*]To check your firewall settings:
[https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)
then click "Proceed" then "All service ports"[/list]

---

