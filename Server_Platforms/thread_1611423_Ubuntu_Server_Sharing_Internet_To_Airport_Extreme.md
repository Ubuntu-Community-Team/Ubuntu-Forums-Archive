---
title: "Ubuntu Server Sharing Internet To Airport Extreme"
date: 2010-11-01
forum: Server Platforms
---

### Post by garryconn on 2010-11-01
I have spent some time reading previous threads and articles found on the docs site, but can't seem to find any documentation on what I am trying to do. If anyone would be willing to lend a hand, I would greatly appreciate it. Here's what I am looking to do.

I have high speed cable Internet access. The IP isn't static, but it hardly ever changes... and when it does, I can manually make the changes... no big deal. 

What I want to do is connect my ubuntu server direct to the cable modem via eth0. From there, I want to connect my airport extreme to eth1 and allow Internet sharing. 

There's plenty of guides walking me thru cable modem to router and router to server... But what I want to do is cable modem to server and server to router and router to distribute wireless throughout the house. 

Part of the reason why I want to do a direct connect to the server is because of the airport extreme itself. The functions aren't really conducive towards running a web server. I'd rather have the main connection into the server, and then allow the server to control sharing the Internet to my airport extreme. 

I know it may seem backwards, but it's what I want to do, and I'm having trouble doing it. Granted, I would be able to figure it out in a snap if I had a GUI installed on the server, BUT... I do not want to do that. I want to keep the server running as clean as possible. 

Again, it's a web server, nothing more ... nothing less... minus that I need to add Internet sharing to my airport extreme. Can anyone offer some tips on that?

Running ubuntu x64 server 10.10

---

### Post by e79 on 2010-11-01
If I understand correctly your case, your Ubuntu Server would have to act as a 'Primary Router' for your whole network and would act as the 'Default Gateway' as well since it would have the direct connexion with your modem.

So if you really want to keep your server connected straight to your Modem , you will have to configure it as a Router and a DHCP server and have your Airport Extreme (having a static IP address) servicing the Wireless part, or having the DHCP service handle by your Airport Extreme.

In any ways, though Linux is known to be more secure than Windows, I would not recommend having a 'Internet Facing' web server, unless you really know what it implies (security speaking). 

You can find more help to configure your server as a Router below and in case, here's a link as well for the DHCP service under Ubuntu :

[https://help.ubuntu.com/community/Router](https://help.ubuntu.com/community/Router)

[https://help.ubuntu.com/10.04/serverguide/C/dhcp.html](https://help.ubuntu.com/10.04/serverguide/C/dhcp.html)

Hope this helps

---

### Post by garryconn on 2010-11-01
Thanks for the quick response, and for your help. You do understand me correctly. But maybe I should explain in more detail, just in case. 

As advised on this page ([https://help.ubuntu.com/community/ServerGUI]("https://help.ubuntu.com/community/ServerGUI")) I want my machine to be as close to a production server as possible. Meaning, I do not want to install a GUI or ANY unnecessary software. The only thing I will add will be a web based administration. Earlier this afternoon I installed Webmin, and did like it... but I understand that it is no longer supported. Since then, I reinstalled Ubuntu Server, and I am researching eBox. 

At any rate, what I want to do is fairly simple in theory, it's just challenge to configure it. The Ubuntu Server has a direct connection to the cable modem via eth0. Everything works great, and I am experienced enough to configure the web server completely from command-line. But, I lack in experience with telling the server to share the Internet connection via eth1 to the Airport Extreme. That's really the only issue I have. 

I know I could be done with all this in about 15 minutes, if I would stop being difficult and just connect the cable modem to the router and then connect all my other devices (server included) to the router. But, I really don't want to do that. When I access the server via ssh or through a web based administrator, it's IP address is an internal one. I want the server to have the main external IP address. 

So really, is that advisable? Should I just stop trying to make things difficult? I mean the way my thoughts are is that a web server SHOULD have a direct connection to the Internet. Is that not it works with big web hosting companies? If, I am wrong in my thinking, someone do tell me... I would appreciate it. 

What bothers me about connecting the cable modem to the Airport Extreme and then connecting the server to the Airport Extreme is that this particular router isn't optimal to be used with a web server. I don't have much control over things like NAT or QoS. But again, if this what I am trying to do by connecting the server direct to the cable modem and then connecting the airport extreme to the server eth1 is stupid, just let me know. lol

---

### Post by nlsthzn on 2010-11-01
I am currently running a Laptop with Ubuntu 10.04 in a similar fashion... eth0 to the broadband device and wlan0 to a AP and the rest of the network... with GUI it is very simple to set up (which is the reason I decided not to use Sever but Desktop Edition)... hope you get a solution...

---

### Post by e79 on 2010-11-01
> But, I lack in experience with telling the server to share the Internet  connection via eth1 to the Airport Extreme. That's really the only issue  I haveThis would involve learning to set up something as 'iptables' with 'dnsmasq'+ 'dhcp3-server' on your Ubuntu server so all the other machines in your network could have internet access as well as dns resolution and port forwarding for the service you want. The DHCP service should be given by either the server or your AirPort Extreme.

> I know I could be done with all this in about 15 minutes, if I would  stop being difficult and just connect the cable modem to the router and  then connect all my other devices (server included) to the router..But, I really don't want to do that. When I access the server via ssh or  through a web based administrator, it's IP address is an internal one. I  want the server to have the main external IP address.Why is that ? All you would have to do is create a rule to forward incoming queries for ssh to your Ubuntu Server in your router administration panel(you could even change the external port, forwarding to the real one internally).
simple example:
SSH
Action                    Protocol/port    Source        Destination        Protocol/port
allow-and-forward   22                   Any            192.168.1.x        22
or
allow-and-forward   62845              Any            192.168.1.x        22

Web Browser Administration (example with random port)
Action                    Protocol/port    Source        Destination        Protocol/port
allow-and-forward   59374              WAN           192.168.1.x        8081
 
> So really, is that advisable? Should I just stop trying to make things  difficult? I mean the way my thoughts are is that a web server SHOULD  have a direct connection to the Internet. Is that not it works with big  web hosting companies? If, I am wrong in my thinking, someone do tell  me... I would appreciate it.
What bothers me about connecting the cable modem to the Airport Extreme  and then connecting the server to the Airport Extreme is that this  particular router isn't optimal to be used with a web server. I don't  have much control over things like NAT or QoS. But again, if this what I  am trying to do by connecting the server direct to the cable modem and  then connecting the airport extreme to the server eth1 is stupid, just  let me know. lolThis is only my opinion and based on what I know - I could be wrong, someone correct me please if so :

1. Basically, Web hosting companies use what we call 'front-end' servers. These are web servers that take all the 'hits' from the web and forward them to the internal 'back-end' web servers. They do not have a copy of the real web site, they only relay valid web transactions to the web servers behind them. In this scenario, they also get hit by all the attacks and various port scans (and else) that scourges the web, reducing the load and security risk on the real web servers. Saying that, I would never put a web server facing the Internet without proper firewall protection and other security layers.

2. The web server does not need a direct connection to the Internet; for a simple web server, a forwarding rule from your router to the port 80 on your server does the job. Hoping that your AirPort Extreme allows it (I'd hope so lol since its a router after all...). For the QOS, I can't say for your model but basic 50$ router offers this features usually.

3. The Airport Extreme is probably easier to configure using your GUI, though learning to set up and configure 'iptables' and 'dhcp3 server' with 'dnsmasq' and port-forwarding all in CLI would be nice knowledge and would give you much more flexibility ...

Hope this helps  :P

---

### Post by garryconn on 2010-11-02
Everything you said makes perfect sense. Thank you. And actually, the more I think about it, it might be better to actually setup a machine just to act as a firewall and to share Internet connection. I have a Dell Dimension E510 that would be perfect for this. 

Cable modem:
 -->> eth0 ubuntu-box-1: This machine has firewall and dhcp.

Ubuntu-box-1:
-- >> eth1 ubuntu-box-2: This machine is my LAMP. Has static IP assigned by ubuntu-box-1.
-- >> eth2 airport-extreme-base-station: This is the router that distributes Internet via internal dhcp.

I don't know,  it seems like it might not even be safe to connect the cable modem to the airport extreme directly. I think I would much rather build a box strictly for the purpose of securing my web server and home network via the airport extreme. 

What are you thoughts on this setup?

---

### Post by e79 on 2010-11-02
> And actually, the more I think about it, it might be better to actually  setup a machine just to act as a firewall and to share Internet  connection.If you can afford to dedicate an old box (as I do) for that sole purpose, it would be the best solution above all for every aspects. The link in my first post about router on Ubuntu would be a start, and also, many free Linux distribution out there can achieve what you want (Firewall, DHCP, DNS, Intrusion Detection ect), link here: [http://en.wikipedia.org/wiki/List_of_router_or_firewall_distributions](http://en.wikipedia.org/wiki/List_of_router_or_firewall_distributions)

> I don't know,  it seems like it might not even be safe to connect the cable modem to the airport extreme directly.This device has a built-in firewall so this should not be not be a concern (though less flexible than what you could achieve).

> What are you thoughts on this setup?     But if you really ask me (from top to bottom lol)...

World Wicked Web
.
(eth0) --> Interface facing the Web
.
[COLOR=Red]Linux FireWall box[/COLOR] (FW, IDS, DNS and DHCP fo LAN and DMZ, SQUID maybe for caching and else)
.
(eth1) --> [COLOR=DarkOrange]DMZ(Demilitarized Zone)[/COLOR] for your Web Server
.
(eth2) --> [COLOR=Lime]Switch for your LAN[/COLOR] (home PC + wireless)

- Hook up your AirPort Extreme to the switch on the LAN side (eth2), disable DHCP (and possibly NAT - not sure on this one) as your Linux Firewall would already service it, add WPA2 security and MAC address filtering.
Or you could plug the eth2  straight into the Airport Extreme that would service the rest of the LAN, but make sure to disable the service(s) here as well. 

Of course this is just me and I could be wrong and someone could correct me...:)

---

