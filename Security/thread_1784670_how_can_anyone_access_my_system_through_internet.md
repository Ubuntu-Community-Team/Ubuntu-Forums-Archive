---
title: "how can anyone access my system through internet?"
date: 2011-06-17
forum: Security
---

### Post by starbala2008 on 2011-06-17
How can anyone access my system (say, cracker)? What are the details a cracker needs to know to access data from my system?

---

### Post by chinnappan on 2011-06-17
just enable in your router or modem DMZ put in your system ip address like 192.168.1.2 , so any one access through Internet with Ur credential ,user name and password, or through  RDesktop  VNC

-vc

---

### Post by Lars Noodén on 2011-06-17
> **starbala2008 said:**
> How can anyone access my system (say, cracker)? What are the details a cracker needs to know to access data from my system?

Connecting it to the net is enough.  From there it will show up on a scan.  Then, depending on which services you have enabled, there is the possibility of finding one with a remote exploit.  Fortunately, this is a very small chance: Ubuntu has no services on by default and those that are have rather good track records.

---

### Post by bodhi.zazen on 2011-06-17
> **starbala2008 said:**
> How can anyone access my system (say, cracker)? What are the details a cracker needs to know to access data from my system?

A cracker would leverage a vulnerability, known or unknown.

See [http://www.ubuntu.com/usn](http://www.ubuntu.com/usn)

Search that page for application you have installed , such as firefox.

A vunerability it a potential problem, an exploit would be the methods to exploit the vulnerability.

HTH

---

### Post by pricetech on 2011-06-17
If I'm reading your post right, you don't want them to.

If you're behind a router with a decent firewall, and you haven't opened any ports, you should be good.

If you haven't installed any services on your computer, again you should be good.

---

### Post by 67GTA on 2011-06-17
Install zenmap with the package manager and scan your IP address. It will show any open ports, and what services are using them. From there you can decide if you need any extra hardening. I have a Linksys router with dd-wrt firmware, and the ufw firewall that comes default with Ubuntu. The only open port I broadcast is 631 because I share my printer with the kids. I have told ufw to only allow traffic in through port 631 from specific IP's from the kids computers. The only other weak spot is through my browser as was mentioned above.

---

### Post by crispy_420 on 2011-06-18
A NAT firewall with no forwarded ports should be adequate for most needs. So basically most any consumer grade router should work for this purpose. Just don't go direct modem to PC.

---

### Post by Lars Noodén on 2011-06-18
> **crispy_420 said:**
> A NAT firewall with no forwarded ports should be adequate for most needs. So basically most any consumer grade router should work for this purpose. Just don't go direct modem to PC.
Just a fine point: NAT is about addressing and has nothing to do with security.  
Maybe you mean a regular firewall.

---

### Post by crispy_420 on 2011-06-18
But it does mask all addresses behind it and makes them generally inaccessible unless the ports are forwarded to the specific system...

These articles refer to NAT as a "passive" or "natural" firewall. It is a cheap and relatively effective means of securing traffic from external threats.

[http://www.networkclue.com/routing/firewalls/nat.aspx](http://www.networkclue.com/routing/firewalls/nat.aspx)

[http://www.vicomsoft.com/learning-center/network-address-translation/#2](http://www.vicomsoft.com/learning-center/network-address-translation/#2)

---

### Post by sammiev on 2011-06-18
> **crispy_420 said:**
> But it does mask all addresses behind it and makes them generally inaccessible unless the ports are forwarded to the specific system...

These articles refer to NAT as a "passive" or "natural" firewall. It is a cheap and relatively effective means of securing traffic from external threats.

[http://www.networkclue.com/routing/firewalls/nat.aspx](http://www.networkclue.com/routing/firewalls/nat.aspx)

[http://www.vicomsoft.com/learning-center/network-address-translation/#2](http://www.vicomsoft.com/learning-center/network-address-translation/#2)

Thanks for the links. Great read. :)

---

### Post by jerome1232 on 2011-06-18
> **Lars Noodén said:**
> Just a fine point: NAT is about addressing and has nothing to do with security.  
Maybe you mean a regular firewall.

A very fine point. The gist of his post is that a router is an effective firewall, and they are.

---

### Post by Kinstonian on 2011-06-18
> **Lars Noodén said:**
> Just a fine point: NAT is about addressing and has nothing to do with security.  
Maybe you mean a regular firewall.

NAT was created resolve addressing problems, but has also over the years helped prevent a very large number of computers from being compromised by filtering traffic; which is the core of any firewall.  I'd say that has to do with security, it's just not the original goal of NAT.

---

### Post by crispy_420 on 2011-06-18
Although it was intended for this purpose doesn't mean it is not effective.  It is like a poor man's firewall, it works and it is a cheap method of doing it. Look a low end router with only NAT costs $10 while a low end firewall will be $100. 

Hey sildenafil and minoxidil were intended to treat hypertension after all. They have worked out well off the original intended use. (Sorry for obscure pharmacy references)

---

