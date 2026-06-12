---
title: "iptables -  MASQUERADE = anonymous?"
date: 2008-05-21
forum: Security
---

### Post by Anus Willcrap on 2008-05-21
Can this option alone give anonymous surfing?

[http://www.christianschenk.org/blog/enhancing-your-privacy-using-squid-and-privoxy/](http://www.christianschenk.org/blog/enhancing-your-privacy-using-squid-and-privoxy/)

This site above suggests you need squid and privoxy.

I don't want to use one of those proxy sites.

Is anonymous surfing really possible?

I am  windowsXP user, but  I am about to install ubuntu 6.10
from a PC Mag CD, as squid looks a nightmare to install on
windows, plus I have a security book that goes into great
detail on setting up the Linux firewall and secure kernal
set up.

---

### Post by Monicker on 2008-05-21
In my opinion, anonymous surfing is a largely a myth.  Someone will always know your origination ip address, it just might not be the final destination you intend to reach..

User -> proxy -> Web site


Simple case, but guess what, the guy running the proxy still knows what ip address you came from.  Do you know who runs this proxy? Do you know how long they might keep a record of your ip address or if they are sniffing any of the traffic you send through them?

You can use a system like Tor, where the connection actually passes through 3 other machines, via encrypted links between the Tor nodes, but now you have the problem of the final Tor node must decrypt your traffic to communicate to a web site, so they still know where you visited; if they are sniffing the traffic they can see anything which is cleartext.  Depending on the final destination, you can encrypt your data before it evens enters the Tor network, but the final destination must be able to decrypt it own its own. Also, if you are not careful with Tor, information can still be leaked about who you are.

You can make it harder to a destination to know where you really came from, but there are several potential ways for disclosure of information which gives away where you really came from.

Proxies and Tor have their uses, but I would never fool myself into thinking they gave me 100% anonymity on the Internet.

---

### Post by Anus Willcrap on 2008-05-21
But to my limited knowledge (still reading),
The iptables  MASQUERADE option, allowes you to change
your out outgoing IP Address to any thing you want, so 
that no one knows who you are. ie. MASQUERADE!!!!!!!!

I'm sure someone here will point out how naive this conclusion
is.

Also, using squid and privoxy, as that site suggests,
is not going through a proxy site.

---

### Post by Monicker on 2008-05-21
ip masquerading is a bit more involved than that.  Masquerading is a form of NAT, used commonly when you have multiple machines on a LAN with private ip addresses which are not routable over the internet or simply because you don't want them all to have their actual ip address seen on the outside.  The ip addresses for the lan segment are masqueraded to that of a gateway device.

192.168.1.100 -> masquerading gateway -> public ip address -> destination


Usually the gateway device is the same one with the public ip address, but this does not have to be the case.  When traffic from 192.168.1.100 goes to the internet, the destination will see it as from the public ip address.  The masquerading device keeps a table which lets it send traffic back to the proper internal machine.  You **can't** just masquerade your ip to anything you want and expect to be able to get a response back from your destination.  Return traffic **must** be able to come back to the masquerading gateway, which means an internet routable ip address.

In the above case the final destination will not know exactly which machine from the lan is connecting to them, but they still know the gateway.  If there are problems with abuse or other unsavory activities, you can be sure that whoever is assigned that public ip address will be contacted about it.  If the destination decides to block that gateway ip, then many many masqueraded hosts could be denied access.

---

### Post by mondayrocks on 2008-05-21
> **Anus Willcrap said:**
> Can this option alone give anonymous surfing?

[http://www.christianschenk.org/blog/](http://www.christianschenk.org/blog/)
enhancing-your-privacy-using-squid-and-privoxy/

This site above suggests you need squid and privoxy.

I don't want to use one of those proxy sites.

Is anonymous surfing really possible?

I am  windowsXP user, but  I am about to install ubuntu 6.10
from a PC Mag CD, as squid looks a nightmare to install on
windows, plus I have a security book that goes into great
detail on setting up the Linux firewall and secure kernal
set up.

Also. You shouldn't install 6.10. 8.10 is out.

---

