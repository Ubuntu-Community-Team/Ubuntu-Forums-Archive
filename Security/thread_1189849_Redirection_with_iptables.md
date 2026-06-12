---
title: "Redirection with iptables"
date: 2009-06-17
forum: Security
---

### Post by hotuna on 2009-06-17
hello people,

I need some assistance in doing redirection using iptables. Well my set up is pretty simple,i have a Adsl router\firewall which runs on linux and which also does natting for inbound as well as outbound traffic. I Have set up a webserver inside my network on ( 192.168.1.2) and have written the following iptable rule on the firewall.

> iptables -t nat -A PREROUTING -p tcp -s 0/0 -d 59.0.0.0/8 --dport 56000 -j DNAT --to-destination  192.168.1.2:80This will redirect any traffic that comes on my wan interface with 56000 port to my internal webserver.

But this time i wish to write another rule with port 60,000 and redirect it to a webserver that is outside my network ( say canonical.com). I wrote the above same rule and changed the destination ip to that of the ubuntu forums and the port to port 80,but that doesnt seems to be working. 

> iptables -t nat -A PREROUTING -p tcp -s 0/0 -d 59.0.0.0/8 --dport 20000 -j DNAT --to-destination  91.189.94.12:80

How do i redirect to  an incoming http request on a particular port to a web-server that is outside my network??

Am i doing anything wrong? I'm pretty new to iptables. Thanks advance.

---

### Post by hotuna on 2009-06-18
Any help??:popcorn:

---

### Post by HermanAB on 2009-06-18
Hmm, rather use 'socat' for that kind of redirection.

---

### Post by hictio on 2009-06-19
Another option might be [redir](http://packages.ubuntu.com/ca/jaunty/net/redir)

---

### Post by idef1x on 2009-06-19
I don't think iptables is able to do it at all what you want. iptables is implemented with routing (through the box) in mind and since you're trying to redirect to the same interface (for outgoing) as the packet is comming from, the packet doesn't go though the box.

I think the best option would be to do the redir in your webserver instead.

---

### Post by hotuna on 2009-06-19
Thanks all for your replies. 


Anyways iptables can redirect the incoming request to an external web-server ,i tested it today,but there still is some problem.  I have 2 ISPs at my place so i installed another webserver ( entirely on different public ip)  on it and tested ,the iptables firewall is able to forward the incoming requests to the the external webserver. 

But the problem is when A is sending an http request to B ( the iptables firewall ) , B is forwarding it to C and inturn C is sending the http reply to A, since there is mis-match in  destination ip  A is dropping the packets.

---

### Post by bodhi.zazen on 2009-06-19
It sound as if you are wanting a proxy server, or more specific a reverse proxy.

Recently I found nginx is good for this, another option is pound.

If you are not wanting to  proxy a (web) server, you would need additional routing options.

iptables -t nat -A PREROUTING -p tcp -s  91.189.94.12 <additional options> -j DNAT --to-destination  where are you going ?

Basically you are wanting to NAT, so you need to either masquerade or make a rule for the return traffic.

See : [http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch14_:_Linux_Firewalls_Using_iptables#Allow_Your_Home_Network_To_Access_The_Firewall](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch14_:_Linux_Firewalls_Using_iptables#Allow_Your_Home_Network_To_Access_The_Firewall)

Not sure exactly what you are donig, but I hope this points you in the right direction.

---

