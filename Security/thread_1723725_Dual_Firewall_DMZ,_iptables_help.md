---
title: "Dual Firewall DMZ, iptables help"
date: 2011-04-07
forum: Security
---

### Post by red812 on 2011-04-07
Hi guys, I'm new to this forum, and after reading through the security section for ubuntu, i've gained quite a bit of insight about iptables.

Although i still have a few questions

	                [http://www.cnux.ca/sqlserver_ws_providers_productpage_files/image008.jpg](http://www.cnux.ca/sqlserver_ws_providers_productpage_files/image008.jpg)


Above(not my diagram, author not known) is the general design of my network.
i have configured a default DROP all Policy, 

My questions are, i want anyone trying to access my public website to be directed to the web server in the DMZ, and anyone trying to access my WIKI server, i want to forward them to my wiki.

a) How do i differentiate, between both kinds of traffic?

b) If i configure my FORWARD policy to be DROP, i can no longer access my public websites, how to i allow for that?

c) Do i have to configure the FORWARD rules as well? or will allowing INPUT/OUTPUT of legitimate responses from the firewall suffice for the purpose.

d) route command no longer shows my routes on the firewall? why is that?

e) I want to make my network as secure as possible, any more things that i need to take note of. I will only be allowing for required ports and services, DROP all otherwise

This is what i have got so far( still ongoing, feedback 

#Default Policy
iptables -P INPUT DROP
iptables -P OUTPUT DROP
iptables -P FORWARD DROP

#loopback access
iptables -A INPUT -i lo -p all -j ACCEPT
iptables -A OUPUT -i lo -p all -j ACCEPT

#established connections access to the firewall
iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A OUTPUT -m state --state ESTABLISHED,RELATED -j ACCEPT

#Firewall Access to the internet
iptables -A INPUT -p tcp --dport 80 -m state --state NEW -j ACCEPT
iptables -A INPUT -p tcp --dport 443 -m state --state NEW -j ACCEPT

#Allow ICMP requests/responses
iptables -A INPUT -p icmp -j ACCEPT
iptables -A OUTPUT -p icmp -j ACCEPT

#SMTP Traffic- to server
iptables -t nat -I PREROUTING 1 -p tcp -d xx.xx.xx.xx --dport 25 -j DNAT --to-destination xx.xx.xx.xx


#DNS Traffic for DNS resolution
iptables -A OUTPUT -p udp -o eth0 --dport 53 --sport 1024:65535 -j ACCEPT
iptables -A INPUT -p udp -i eth0 --sport 53 --dport 1024:65535 -j ACCEPT

I will be allowing port 25,110,143,22
I dont want the LAN clients access to any of the servers, but still want the traffic to flow.

What role should the interior firewall have in my network, still confused about it.

---

### Post by bodhi.zazen on 2011-04-07
/off topic

use multiport 

-p tcp -m multiport --dports 20,21,22,25,80,110,143,443

(I added ftp as it is common enough).

you might want to rate limit ping =)

> I dont want the LAN clients access to any of the servers, but still want the traffic to flow.

What role should the interior firewall have in my network, still confused about it. 

You answered your own question I think ?

You could of course firewall your servers


# Allowed LAN traffic here
RULE 1 (ntp, nfs, samba, DNS, DHCP)
RULE 2 (additional LAN trafic)

# Reject everything else.
-A INPUT -s 192.168.0.0/24 -j REJECT
-A OUTPUT -d 192.168.0.0/24 -j REJECT

---

### Post by red812 on 2011-04-08
Thanks for the help, also i would like to know, should i forward traffic from my server farm to the LAN?

If you could explain me, what role should i put the interior firewall to? I think it will only be forwarding traffic, as most of the heavy lifting is done by the exterior firewall.

---

### Post by bodhi.zazen on 2011-04-08
I do not understand what you are asking or your goals.

Do you want to keep boxes on a LAN separate from a server farm ?
Are they public servers ? Or private servers ?

What are you trying to accomplish exactly with your firewall? What traffic do you want to allow and what traffic do you want to restrict ?

Once you answer those questions your firewall rules will fall into place.

---

### Post by red812 on 2011-04-09
> **bodhi.zazen said:**
> I do not understand what you are asking or your goals.

Sorry for being vague, what i want to accomplish with the setup is maximum security.

> **bodhi.zazen said:**
> Do you want to keep boxes on a LAN separate from a server farm ?
Are they public servers ? Or private servers ?

Yes i want to keep the LAN boxes separate from the DMZ and the server farm(which are in different subnets). The servers that i have are
DMZ- Mail,DNS,WEB,WIKI,IDS
Server Farm- IDS, Mail Store
I would like the lan clients access to the services but disallow any other ports/traffic from them


> **bodhi.zazen said:**
> What are you trying to accomplish exactly with your firewall? What traffic do you want to allow and what traffic do you want to restrict ?

With this setup i have separated DMZ,Server Farm, LAN clients, and dual firewalls for maximum possible security, all this is in a virtual environment for a subject. UBUNTU

I hope i'm clear, iptables is quite a task when you are confused about things

---

### Post by handy on 2011-04-09
Find an old PII or PIII that has 256MB or more of RAM & at least a 2GB HDD, these machines cost nothing ($5- at the garbage dump) stick a 2nd NIC into it (preferably a different chip-set than the other as it makes it easier during set-up) Then download & install IPCop.

It will allow you to do most all that you want to do in such an easy fashion. Once it is setup, take screen shots of your setup (client side browser interface) so that if you lose the drive or whatever you don't have to reinvent the wheel.

You could even use Clonezilla to make an image of the drive, which makes it so easy if you have to replace the drive on that machine.

I have a 2nd (Athlon 700) already setup, so that if my PIII dies, I can just plug in the backup system.

I checked the power consumption of my PIII. @ 19.2 cents/kW it costs me about $53-/year in electricity (running 24/7 headless).

[http://www.ipcop.org/](http://www.ipcop.org/)

[http://www.ipcop.org/1.4.0/en/install/html/index.html](http://www.ipcop.org/1.4.0/en/install/html/index.html)

---

