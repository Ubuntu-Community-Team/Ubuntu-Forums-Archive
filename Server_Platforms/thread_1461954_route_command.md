---
title: "route command"
date: 2010-04-24
forum: Server Platforms
---

### Post by expatCM on 2010-04-24
I do not understand this command well.  Yes, I have looked at man route and that whilst that gives lots of information about the switches I cannot see it in context.

I have a server with two nics.  One to the Internet (eth1) and one to the lan (eth0).  I use pppoe and when it is running I get a virtual adapter appear in ifconfic called ppp0 which shows the public DNS and ISP session IP.

I entered the command 

> route add -host (gateway IP) dev eth1

and get the Internet to appear on the server.

However, I do not get the Internet to the clients.

What did I miss?

I have turned off the firewall to be sure that this is not the problem.

---

### Post by windependence on 2010-04-24
Are you using the server as a gateway for the clients?

-Tim

---

### Post by expatCM on 2010-04-25
Yes.

Clients run to a switch connected to eth0.  eth0 / clients are managed by the server with dhcp on the server.

eth1 faces the wan only and basically is used only to manage the Internet connection.

---

### Post by Cosma on 2010-04-25
first you have to enabled ip forwarding on your server
```
echo 1 > /proc/sys/net/ipv4/ip_forward
```after that you just have to enable nat on your wan interface (this command is for dynamic ip's)
```
iptables -t nat -A POSTROUTING -o ppp0 -j MASQUERADE
```if you have static ip's, then you might want to use snat instead
```
iptables -t nat -A POSTROUTING -o ppp0 -j SNAT --to-source 1.2.3.4
```

---

### Post by expatCM on 2010-04-25
Thank you for your post Cosma.  So that I can go in nice easy steps I have taken down the firewall, when things work then I will put it up again (less opportunity for unknown problems that way)...

The first line is all that I need to use at this point I guess.  In simple terms all this line is saying is allow traffic from ppp0 to the rest of the network?

When I enter this at a command prompt does this make an entry in the system or do I need to edit a file to make this setting permanent?

---

### Post by Cosma on 2010-04-25
> **expatCM said:**
> 
The first line is all that I need to use at this point I guess.  In simple terms all this line is saying is allow traffic from ppp0 to the rest of the network?

the first line
```
echo 1 > /proc/sys/net/ipv4/ip_forward
```will enable routing on your server but you also need the next line
```
iptables -t nat -A POSTROUTING -o ppp0 -j MASQUERADE
```to enable internet access on your clients. because routing alone won't do it since your local network can't be routed to the internet. this is why you translate your local ip's to your external ip.

> **expatCM said:**
> 
When I enter this at a command prompt does this make an entry in the system or do I need to edit a file to make this setting permanent?
none of the commands will be permanent. this means you have to make a script and run it each time your server starts.

---

### Post by expatCM on 2010-04-26
This certainly is helpful.  Thank you for the postings.  I am not there yet, I think there are possible problems with the firewall settings but this information certainly helps me look ..........

---

### Post by windependence on 2010-04-26
It would be a lot easier to use something like pf sense to do what you are wanting to do. It will even handle the ppoe connection for you. It's also small enough to run from a CF card or memory stick.

If you are doing this just to learn routing, then I understand, but if not you don't need to reinvent the wheel. 

[http://www.pfsense.org](http://www.pfsense.org)


Hope this helps.

-Tim

---

### Post by expatCM on 2010-04-26
Thank you for telling me about pfsense.  Not heard of it before.

What I am doing is setting up a new server.  I have been following the Woodel guide which is found at this link.
[http://woodel.com/](http://woodel.com/)

I have found this to be quite good and I want to stay with this until the conclusion.  I have just run into a problem in that the guide does not use adsl / pppoe but I need to which in turn means that I have been having to find out how to solve the various problems which seems to include routing and iptables .....  I am on a sort of steep learning curve.

---

