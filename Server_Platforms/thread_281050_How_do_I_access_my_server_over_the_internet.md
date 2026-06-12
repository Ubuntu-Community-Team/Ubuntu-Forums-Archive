---
title: "How do I access my server over the internet?"
date: 2006-10-20
forum: Server Platforms
---

### Post by mike41 on 2006-10-20
Hello.

I set up LAMP, and I can access the server using [http://localhost](http://localhost)

But I dont understand how to access the server from the internet ie. from someone else's computer, not in my LAN. Do I have to simply set up a static IP address, or do I have to buy an IP address from some organization like arin?
I'm really confused with how the whole IP address system works.

Thanks,
Mike

---

### Post by RaZer0r on 2006-10-20
let me explain you a bit about IP adressing first.
1. There are differences between them ex. 192.168.0.1 =! 81.83.57.42

The first adres is an adres used in an Local! Area Network the other one is an example of an external (or ip adres for the world to see.)
When surfing on the internet you alway's have an extenal ip, wich varies county by country (belgium in my case starts almost all the time within range 81 - 85.

A router splits the external ip adres you get from your isp as soon as you connect to the intenet. So your router would be connecting to 81.xx.xx.xx and then splitting that ip up into the local area network. This means: the router has 2 ip adresses: 1: the external ip en and 2: the internal local ip.
the computers connected to the router are all getting an local adres from the router (that is if the router has an DHCP function).

A hub has another way to approach things. It never has an DHCP function or split function. the only thing it can do is get the external ip and (this is why a hub isn't that much used anymore) and splitting it up into 2 external ip adresses (this is ofcourse only if your isp (internet service provider) supports multiple ip adresses.)
So the only thing it can do is take the incomming line, and split that line so that 2 (or more) computers get online with different ip adresses.

A switch is something like a hub, but a bit newer. The switch can see the difference between "crossed over UTP (unshielded twisted pair) cables" and "straight to straight UTP cables". The switch is in most cases used by companies and large networking usaging.

To get back to your problem: if you have your webserver running behind a router, you need to configure the router so that the external ip gets forwarded to the server's internal ip. Read your manual on how to do that :)

If your webserver does not have an internal, but an external ip: just type: [http://the-ip-of-your-server(:the-port-you-use](http://the-ip-of-your-server(:the-port-you-use))

---

### Post by mike41 on 2006-10-20
Thanks for the answer! I've still got a few questions though, if you don't mind.

With regards to internal vs external IP, the are both the external and internal IP's globally unique? So if my internal IP is 123.123.123.123, does that mean that no other computer/router/whatever can have that IP as either internal and external?

When you say that the computers in the LAN are getting the IPs from the router, do you mean that the router connects to some sort of IP-making server which will tell the router which unique IPs are available?

And so if my router lets say has password for its config utility, and nothing like that, and its external IP address was 123.123.132.123, then if I typed that IP into my browswer, I should be able to access my router from any computer on the internet? And if the router assigned me an internal IP, then if someone requests to communicate with that IP, then the router will block their traffic.

sorry for all the questions, I just really wanna understand this! :D

---

### Post by ixus_123 on 2006-10-20
Your internal (LAN) Ip is only for your internal network - it will usually be something like 192.168.1.1 to 255 for example.  Someone on another LAN (local area network) may have the same local ip adress but it wouldn't matter as they are closed off from each other.

When you are on the internet though you ip adress is unique to you.  To serve up web pages you will nee a static ip address.  Some ISPs change users ip adress which is bad as a viewer will not be able to find you.  (you can work aroudn this if you don't have a static IP with dynamicdns.org (I think)

You will also need to log into your router (usually 192.168.0.1 or 192.168.1.1 or similar) & set it up to allow port forwarding port 80 usually for http.  While your in the router admin make sure you change the defualt passowrd to something more secure.

I'm pretty new to all this myself & don't know how to access my router from outside my home but I do know it has a firewall & it the first line of defence so leaving the defualt password on it would be a big mistake.

---

### Post by FastZ on 2006-10-20
> **mike41 said:**
> Thanks for the answer! I've still got a few questions though, if you don't mind.

With regards to internal vs external IP, the are both the external and internal IP's globally unique? So if my internal IP is 123.123.123.123, does that mean that no other computer/router/whatever can have that IP as either internal and external?

When you say that the computers in the LAN are getting the IPs from the router, do you mean that the router connects to some sort of IP-making server which will tell the router which unique IPs are available?

And so if my router lets say has password for its config utility, and nothing like that, and its external IP address was 123.123.132.123, then if I typed that IP into my browswer, I should be able to access my router from any computer on the internet? And if the router assigned me an internal IP, then if someone requests to communicate with that IP, then the router will block their traffic.

sorry for all the questions, I just really wanna understand this! :D

Let's see if I can explain this any better than the other guys.

An external IP address...the one your ISP gives you is unique to you and you alone.  Nobody else has that IP address and wont ever have that IP address for as long as you have it.  Now, an internal IP address, usually between 192.168.0.0 and 192.168.255.255, is an address that is unique to your home network.  However, say your have a computer on your home network that has pulled an IP address of 192.168.1.102, it is not unlikely that your neighbor, who also uses a home router, will have a computer with that same IP address on his home network.  The 192.168.0.0 series of IP address is reserved for personal use, basically set aside for people like yourself and me and probably the bigger majority of the members on this forum, to use on our home networks for free.
Now, your router, I'm pretty sure itll have a DHCP (dynamic host configuration protocol) function on it by default.  DHCP is a protocol that hands out available IP addresses to computers or other equipment that is asking for an IP address.  
Your router uses NAT, or Network Address Translation.  This is what converts your external IP address into your internal addresses.

Here are some links to help you better understand each thing...
[http://en.wikipedia.org/wiki/Ip_address](http://en.wikipedia.org/wiki/Ip_address)
[http://en.wikipedia.org/wiki/DHCP](http://en.wikipedia.org/wiki/DHCP)
[http://en.wikipedia.org/wiki/Network_address_translation](http://en.wikipedia.org/wiki/Network_address_translation)
[http://en.wikipedia.org/wiki/Domain_name_system](http://en.wikipedia.org/wiki/Domain_name_system)
[http://en.wikipedia.org/wiki/Local_area_network](http://en.wikipedia.org/wiki/Local_area_network)
[http://tools.ietf.org/html/rfc1918](http://tools.ietf.org/html/rfc1918)

---

### Post by mike41 on 2006-10-21
Wow thanks for all the answers. This all makes sense to me now! So (basically),  I have to configure my router to forward incoming HTTP requests   arriving at the external IP (which is the router) to my system, identified by the internal IP. And if I want to have an english address such as [www.whatever.com](www.whatever.com), I would register my external IP with a DNS name vendor. 

Now one more question. Assuming that what ive said at the top was correct, how could I run two servers in my private network, if all requests get forwarded to this system? Is that where ports come in?

---

### Post by Yoguess on 2006-10-21
yes, so far you are correct
as far as 2 websites on 1 system, im not sure how in linux, i have not got that deep yet

but in windows you can add website in another folder, create another static ip address and map it to new site
I would think it will be same in linux

if anyone can answer i would like to know this for sure

---

### Post by Soarer on 2006-10-21
You can have several urls pointing to a single external IP. The Apache server on your Ubuntu box gets all the traffic for that external IP (if your router is configured as mentioned above) and knows which url is being requested.

If you think about it, it HAS to do this for even one web site, since it needs to know which page (each of which which have a separate url) is being requested, and all requests go to the same external IP.

So, if you have 81.82.83.84 as your external IP, for example, you can have [www.site1.com](www.site1.com) and [www.site2.com](www.site2.com) directed to that IP. The router passes those requests from the Internet outside your LAN through to Apache, which directs [www.site1.com](www.site1.com) to virtual web site site1 on your server, and [www.site2.com](www.site2.com) to virtual web site site2 on your server.

You could use port redirecting, but then you would have to use [www.site1.com:81](www.site1.com:81) (if you are using port 81) to get to that site, and you would have to configure port redirect in the router, which isn't always easy.

---

### Post by Yoguess on 2006-10-22
i remember this now
thank you :mrgreen:

---

### Post by MJN on 2006-10-23
> **Soarer said:**
> You can have several urls pointing to a single external IP. The Apache server on your Ubuntu box gets all the traffic for that external IP (if your router is configured as mentioned above) and knows which url is being requested.
 
If you think about it, **it HAS to do this for even one web site**, since it needs to know which page (each of which which have a separate url) is being requested, and all requests go to the same external IP.
 
If you'll forgive the pedantry the above (bolded by me) is not strictly true as the actual page the client is after is dictated by the GET request whereas the particular site (be that name or IP) is specified in the HOST header field. Hence, for a single website only the information in the GET field is relevant.
 
Mathew :)

---

### Post by Soarer on 2006-10-23
Additional accuracy is always welcome :)

---

