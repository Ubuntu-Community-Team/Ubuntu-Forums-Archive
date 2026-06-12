---
title: "SAMBA - Netbios - security level"
date: 2017-03-20
forum: Security
---

### Post by jambyc on 2017-03-20
Hi,

I have installed SAMBA to transfer files within my local network as it faster by simply drag and drop to specify server folder.
My ISP keep sending me letters that Netbios is insecure etc...
This lead me to thinking that someone really can get access to my server as its resolved by domain name.

Is there any way I can secure/lock any possible attempt to access my local network from outside?
All local network folders are secured with user name an password. Is it enough?

---

### Post by TheFu on 2017-03-20
A password is not enough. SMB/CIFS security is like posting a sign asking for crooks not to enter.
If you have a router and use NAT, then just make certain the CIFS ports aren't passed through to your system.
If you don't have a router - get one. Routers are designed to provide a minimal amount of security for people who are not network savvy.

If you elect NOT to get a router.  You'll want to do many things, if you insist on using CIFS/Samba, including running a firewall on your system that blocks all traffic from outside your LAN and configuring samba to only listen on a network adapter connected to your LAN.

If any of this sounds hard - just get a router.  Even a bad, cheap, hackable, router will block most of this stuff.

In my part of the world, CIFS ports are blocked by residential ISPs, since nobody in their right mind would allow it on the internet.

---

### Post by jambyc on 2017-03-20
I didn't think to mention that I am using router. Yes, I do!
By your post I understand that Router and ISP will secure most of it...?

Currently server is set to DMZ with specific local IP and UPnP is enabled.
The more I am into it the more I am confused.

I dont see any NAT services on my router. Should I contact my IPS regarding this?

Other question.
Who in the world my ISP know that I am using Netbios? This is a bit complicated to my little brain :)

---

### Post by TheFu on 2017-03-20
Anyone can scan all the ports on the internet, including your ISP.  You can scan ports too. There are free services that you can use to scan your own IP to see what seems open and what seems closed at that instance.  Google for "shields up" - it is reputable.

I cannot say whether your ISP filters/blocks samba on the WAN side or not. Here in Squidbilly-land, they do. The scan service will see that too.

Most home routers block all inbound requests and allow all outbound requests by default. That is usually sufficient, provided UPnP hasn't been enabled and isn't enabled by default (usually it is) or don't have a gaming system that opens ports as a convenience. Some IoT devices (network storage, gaming, video players, etc) might do the same thing - open ports via UPnP, if you haven't specifically disabled UPnP on the router.  As usual, things that are more convenient are also bad for security.

More and more, we all need to be aware of networking and take "appropriate steps" to protect ourselves.

---

### Post by jambyc on 2017-03-20
Thank you for all your constructive support. As some say no pain no gain. Through my journeyer with Ubuntu server I have done countless number of installations due to my lack of knowledge and unappropriated steps.

I will try to block all in/otbound ports to secure this service.

Thanks again

---

