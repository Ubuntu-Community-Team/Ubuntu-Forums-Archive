---
title: "DMZ or port forward?"
date: 2011-07-11
forum: Server Platforms
---

### Post by rileyb76 on 2011-07-11
Guys,
Setup a box with Ubuntu Server (fully patched) on it and was curious as to which method would be "best" for my use.  My buddy and I are wanting to do some web development, and access this server from my house and also his house.  Would also like to host a simple site just for our use and to play around with.    

As far as security which one is better?  

My concern was if I setup port forwarding on my Linksys and the box was comprised somehow, then the hacker could sniff traffic etc and be on my LAN (if this is even possible).  

A buddy at work said to setup on a DMZ but make sure the pwd is very strong and its fully patched.  

Which way would be most secure and efficient?

Btw, my ISP is Charter and so far port 80 has been allowed.

Thanks for any advice.

---

### Post by godjil on 2011-07-11
Show You ip configuration.

like this:
ISP(WAN)1.2.3.5/24
lan192.168.0.1/24
Ubuntu-host 192.168.0.2/24

---

### Post by Dangertux on 2011-07-11
As far as the concern of sniffing traffic it makes no difference if the machine is dmz'ed or port forwarded. If the machine is compromised and shares a local interface with the rest of the network it will be able to access the network. 

You could attempt to make the network unroutable from the server, however depending on the type of router you have this may not be supported.

---

### Post by godjil on 2011-07-11
Yep!

---

### Post by hawkmage on 2011-07-11
Why is DMZd and port forwarded separate?  Unless you have a routable IP in your DMZ you would still need to use port forwarding.  

With that being said I would highly suggest that any system that has services available to the Internet to be in a separate zone, a DMZ, from your normal network.

The issue I have with just port forwarding to a box in you normal network is that if it does get compromised then the attacker has free access to all of the systems on your "internal" network.

---

### Post by Dangertux on 2011-07-11
> **hawkmage said:**
> Why is DMZd and port forwarded separate?  Unless you have a routable IP in your DMZ you would still need to use port forwarding.  

With that being said I would highly suggest that any system that has services available to the Internet to be in a separate zone, a DMZ, from your normal network.

The issue I have with just port forwarding to a box in you normal network is that if it does get compromised then the attacker has free access to all of the systems on your "internal" network.

The reason port forwarding and DMZ are considered as two separate entities in this case is the nature of SOHO routers.  

Even then, it is still technically possible to get to an unroutable machine on the internal network, albeit considerably more difficult and time consuming. If it's really that much of a concern consider a separate line.

---

### Post by hawkmage on 2011-07-11
Even with a non-routeable IP address as long as you allow access to a service through port forwarding you are exposing any vulnerabilities in that service to the internet.  A non-routeable IP is no more secure than a routable IP address if you allow access to it.

DMZ configurations have become fairly common on even SOHO routers/firewalls.  This separates internal and DMZ traffic and keeps DMZ systems form initiating connections to the internal network but allowing the reverse.  this allows you to manage/update the DMZ systems from the internal network but hindering access from the DMZ.  

Yes a separate network connection would completly isolate the DMZ form the internal network but is overkill for most except for the most stringent security requirements.  SOHO DMZ configurations or separate networks preventing access into the internal network are much more secure than port forwarding into the internal network.

---

### Post by Dangertux on 2011-07-11
> **hawkmage said:**
>   A non-routeable IP is no more secure than a routable IP address if you allow access to it.

DMZ configurations have become fairly common on even SOHO routers/firewalls.  This separates internal and DMZ traffic and keeps DMZ systems form initiating connections to the internal network but allowing the reverse.  this allows you to manage/update the DMZ systems from the internal network but hindering access from the DMZ.  


I think you need to test those theories and reconsider your position.

You are not incorrect in terms of the proper implementation of a perimeter network. However, the fact that most SOHO routers fail to properly implement Data Management Zones make your stance on this incorrect.

The REASON that a properly implemented DMZ works is BECAUSE the internal network is not routable. However when you have a Linksys desk-warmer router it is going to stick everything in one subnet without an additional firewall, making the DMZ nothing more than extravagant port forwarding.

On a complete sidenote : This behavior could be emulated with iptables on the server, however since the stipulation is the server would be compromised any host based firewalling would be irrelevant.

---

### Post by jmoorse on 2011-07-12
Use port forwarding, that will meet your needs.  I also recommend dynamic dns in the event your WAN IP changes.

---

### Post by hawkmage on 2011-07-12
If you allow access to a service on a system that has an non-routeable ip address how is that any more secure than a system that has a routable IP.  If some one who is external to the network can make a connection and communicate with it they can exploit a vulnerability on it.  If the server can reply back to the external client it is able to make connections to external resources.  So how is this any more secure than a routeable IP?   

How is the world is having an internet accessible server on a network segment that is not allowed to access your internal network not more secure than placing it in your internal network.

BTW: I have been dealing with computer for 20+ years and I design and implement enterprise systems for a living.  I have put the so called theories in practice many times and they have even been penetration tested by security firms and no issues.

---

### Post by Dangertux on 2011-07-12
> **hawkmage said:**
> If you allow access to a service on a system that has an non-routeable ip address how is that any more secure than a system that has a routable IP.  If some one who is external to the network can make a connection and communicate with it they can exploit a vulnerability on it.  If the server can reply back to the external client it is able to make connections to external resources.  So how is this any more secure than a routeable IP?   

**How is the world is having an internet accessible server on a network segment that is not allowed to access your internal network not more secure than placing it in your internal network.**

BTW: I have been dealing with computer for 20+ years and I design and implement enterprise systems for a living.  I have put the so called theories in practice many times and they have even been penetration tested by security firms and no issues.

OK You're missing my point , IT IS more secure.

However, what I am trying to explain here is; that's an actual DMZ. You know, a properly set up perimeter network is exactly as you say it is. 

My point is if you read the piece of equipment the TS is referring to you will see that this is NOT what will happen. 

Like I said, since I'm obviously having trouble communicating this clearly. IF a PROPER DMZ is created (I'm assuming since you do this for a living you understand the difference if not I can elaborate) then yes you would be correct.

However, in THIS case an ACTUAL DMZ will not be created, instead what will be created is a system that is completely exposed to the Internet. (IE : extravagant port forwarding).

So, if you read my initial response to this thread, you will note I made the point that there is NO difference between port forwarding in this case and a DMZ. Since the DMZ will not ACTUALLY separate traffic. Do you see where I'm going now?

As for routed vs non routed -- that condition can not occur in the TS' situation without additional equipment so it is really not relevant. I was also never debating that if you put a system out on the net it can be exploited, I think that's pretty common knowledge.

Hopefully this helps you understand.  As far as your resume` goes it wasn't needed. As far as penetration testing goes -- if you have worked in the industry as long as you claim you know there are a variety of security firms. Those that charge you for Nessus results, and those that actually know what they're doing as well as everything in between.  So those statistics in and of themselves mean nothing. 

So bottom line in this case, and you can argue this until you're blue in the face if you'd like, however my next post on the subject will contain only a link to Google. Neither port forwarding nor DMZ is more secure in this situation. The reason being, the DMZ created by a Linksys home router is not a true DMZ.

---

### Post by hawkmage on 2011-07-12
The only reason I mentioned my resume as you called it is that you said "I think you need to test those theories and reconsider your position."  It was to illustrate that I have tested those theories.  

Yes, many security companies just use Nessus and leave it at that.  We actually have Nessus in house as well as a couple of other tools.  But depending on the requirements of a system being implemented we have had thorough penetration tests that go well past a scan. 

If what you are saying is correct and the "DMZ" config is not actually isolated from the "internal" network it is has no benefit.  This is actually frightening in that if it does do a blanket forwarding to a internal host this is actually much worse than a simple port forwarding.  I guess I am out of touch with the home router/firewall market. I really hate it when marketing departments take terms and redefine them to sell products.

---

### Post by capscrew on 2011-07-12
> **hawkmage said:**
> ... I really hate it when marketing departments take terms and redefine them to sell products.

It's worse than that.  Some non-tech folks at on this forum also make up their own definition of a term based on what they *think * it means.

To paraphrase George Bernard Shaw: *sometimes we are separated by a common language.*  :-(

---

### Post by Dangertux on 2011-07-12
Yeah it's really annoying that marketing does that. The truth of the matter is a home router is a great solution for the average end user. Unfortunately if you want to do more than basic tasks you really either need a high end SOHO router, or a more versatile solution. Which doesn't really come cheap. 

Honestly if the TS is really serious about it I would recommend build a home router something like the smooth router project would be good. Should be pretty cheap. I built one for less than 50 bucks using a returbed computer from eBay and added two extra NICS. 5 bucks a piece also on eBay   

Much more versatile then any SOHO router you will be able to buy at a big box store. Cheaper too. 

That's just my opinion. Also to hawkmage. I apologize about the resume comment it was a little brash. I was frustrated because I was having difficulty communicating my point. Something that is not your fault. So yeah I am sorry.

---

### Post by hawkmage on 2011-07-12
> **Dangertux said:**
> That's just my opinion. Also to hawkmage. I apologize about the resume comment it was a little brash. I was frustrated because I was having difficulty communicating my point. Something that is not your fault. So yeah I am sorry.
No big deal, it is easy to go off on someone when they hit a nerve.  After the first couple of posts I was ending up not reading your entire posts either.

---

### Post by Dangertux on 2011-07-12
> **hawkmage said:**
> No big deal, it is easy to go off on someone when they hit a nerve.  After the first couple of posts I was ending up not reading your entire posts either.

All good :-)

---

