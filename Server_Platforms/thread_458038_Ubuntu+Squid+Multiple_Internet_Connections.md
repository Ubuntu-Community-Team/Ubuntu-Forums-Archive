---
title: "Ubuntu+Squid+Multiple Internet Connections"
date: 2007-05-29
forum: Server Platforms
---

### Post by nhd on 2007-05-29
I have a couple questions related to Squid+Ubuntu+Networking(My black box). Here is the scenario so far. I have about 40 clients who want to connect to the internet and sometimes there is just 4 clients so i dont want it to be a static setup. I have a nice machine which can be configured as a Squid server running on Ubuntu with no issues. I have 4 identical DSL accounts each pointing to a different ISP which i would like to share using round-robin for example so that all my clients can utilize the available resources.

 My idea is to setup 2 different local networks and my ubuntu box would have 2 NICs. 1 would be connected to a switch that also hosts all 4 DSL modems and using squid.conf i set each of the four different ISP proxys as a parent proxy running a round-robin scheme. The other NIC is connected to another switch that physically connects all 40 clients to the Ubuntu box. So in theory i should just setup the proxy settings on each of there browsers and squid would be there gateway to the internet.

 My questions are the following.
- Is this the best approach to my situation?
- What about DNS for the clients? Would squid be querueing the right ISP dns with the connection or would there be conflicts?
- Would other services like messengers and p2p and voice chat work through squid?

Thanks in advance for the help :-)

---

### Post by craigp84 on 2007-05-29
Hi nhd,

> Is this the best approach to my situation?

How long is a piece of string? :) It's not the most common method of solving this type of issue, but whether it works best i'll leave to you; if economics weren't an issue, you'd buy a proper router to do this.

I'm assuming you're going to go down the IPMP (IP Multi Pathing) coupled with some traffic shaping route - in which case there's quite a few docs on this.

To be honest though, it's probably better just to do this properly. Get a brand name router in there, you can get some cracking deals on ebay. If you're going cisco just watch out for the licencing issues - it can be quite difficult to stay above board with second hand cisco kit - even if you want to.

Your approach should work though. Consider that it's more effective to traffic shape over 4 x usb adsl modems than it is to try and traffic shape through an ethernet adsl modem (due to pretty hefty buffers these things can employ).

> What about DNS for the clients? Would squid be querueing the right ISP dns with the connection or would there be conflicts?

I'll take the pragmatist's view - it doesn't matter :)

> Would other services like messengers and p2p and voice chat work through squid?

Yes, for the most part.

Just make sure you don't try to do crazy things like round robin each HTTP connection from one client to a specific site - that is, you should ensure HTTP connections are "sticky" - loads of websites break otherwise :(

You're on a workable track.

Hope this helps,

-c

---

### Post by nhd on 2007-05-29
> **craigp84 said:**
> 

if economics weren't an issue, you'd buy a proper router to do this.



 You are 100% correct and i already went through a hassle with cisco and finding support would also cause me more overhead.

> **craigp84 said:**
> 


I'm assuming you're going to go down the IPMP (IP Multi Pathing) coupled with some traffic shaping route - in which case there's quite a few docs on this.


 I understand id need traffic routing just on the Ubuntu box between the 2 different subnets. Is there any other need for IPMP other then redundant interfaces using the same IP?(Im going low cost so i wont setup 4 NICs on the server)

> **craigp84 said:**
> 
Your approach should work though. Consider that it's more effective to traffic shape over 4 x usb adsl modems than it is to try and traffic shape through an ethernet adsl modem (due to pretty hefty buffers these things can employ).


 I choose 4 ethernet modems so i wouldnt have to have more PC's im trying to use a minimum amount of equipment. Can you explain more the hefty buffers issue related to ethernet modems?

> **craigp84 said:**
> 
Just make sure you don't try to do crazy things like round robin each HTTP connection from one client to a specific site - that is, you should ensure HTTP connections are "sticky" - loads of websites break otherwise :(


 Im doing round robin via squid so its on a session level i think :| im sure this can be configured via squid someway or the other.

 Thanks for the help and I see this forum still amazes me with the level of skills offered and friendlyness in responses. Keep up :)

---

### Post by honeydew on 2007-06-06
I dont know if load balancing over 3 different connections can done easily in ubuntu.  However... openbsd provides great functionality with the pf firewall.. Also worth checking out is pfsense.  I know they have good abilities with load balancing .  [http://www.pfsense.com/](http://www.pfsense.com/)

---

