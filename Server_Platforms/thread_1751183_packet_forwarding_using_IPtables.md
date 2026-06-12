---
title: "packet forwarding using IPtables"
date: 2011-05-06
forum: Server Platforms
---

### Post by turki_00 on 2011-05-06
Hi,
I have 2 Ubuntu boxes sitting in the same subnet; server 1 [130.15.6.68] and server 2 [130.15.6.69]
What I am trying to achieve here is the following:

Internet -> server 1 (130.15.6.68) -> server 2 (130.15.6.69)

server 1 is  exposed to the Internet and all traffic (www, ftp, telnet) to server 2 should go though it  (i hope!).

server 2 act as application server and I don't want a direct access to  it from the Internet. I want all the inbound traffic comes through  server 1.

for testing purposes, i am testing the port forward from server 1 to server 2 on port 80:

in server 1, i have done the following settings:
iptables -t nat -A PREROUTING -p tcp -i eth0 -d 130.15.6.68 --dport 80 -j DNAT --to 130.15.6.69:80
iptables -A FORWARD -p tcp -i eth0 -d 130.15.6.69 --dport 80 -j ACCEPT

Also,
In server 1, I've edited the value of net.ipv4.ip_forward to equal 1 (uncomment that line in /etc/sysctl.conf)

Currently, both server 1 and server 2 has its own apache2 servers with different index.html files.

the problem is, when i point the browser to server 1 ip, I am still seeing its index  page rather than being forwarded to server 2 and seeing the index page of server 2.

how can i achieve the traffic forwarding from server 1 to server 2 when my browser pointing to server 1?


Thank you in advance

---

