---
title: "Squid / Access Control"
date: 2006-10-11
forum: Server Platforms
---

### Post by twistedtwig on 2006-10-11
Hi all,

I have NO idea if this is possible.  I have squid installed, although i dont know how to configure it yet to stop certain pages from being viewed.  But what i just thought was can you make it so certain users can not view anything between certain times?

the way my thinking had evolved is stopping the kids logging on at silly oclock in the morning.  I am JUST setting up a sbs2003 server and going to use domains to control access times.. but they could aviod that by just logging into the local computer (not that they will know that straight off) which would give them access to the net etc.

Cheers

Twiggy

---

### Post by kidders on 2006-10-11
Hi there,

What you described is possible alright :-)

I did a quick web search and found pages like this ... [http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch32_:_Controlling_Web_Access_with_Squid#Restricting_Web_Access_By_Time](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch32_:_Controlling_Web_Access_with_Squid#Restricting_Web_Access_By_Time)

Assuming you haven't done so already, have a read about transparent proxying. The idea is that using your proxy wouldn't require any client-side configuration (your kids' browsers wouldn't even necessarily *know* their connections were being proxied), so it would be impossible (well ... hard!) to circumvent. You would use a firewall like iptables to hard-wire your network to direct all traffic destined for the internet through your proxy.

In addition to your time restrictions, you might also be interested in extensions like DansGuardian, that would allow you to filter content.

I hope that helps.

---

### Post by twistedtwig on 2006-10-11
Thats very cool,

so I would need to set the boys machines to a certain ip range and the adult machines to a different range to allow different access time rights.

Shame you cant do it on user its self but they dont and wont know passwords to the adult machines anyway.  only issue would be those machines would not be fixable out of hours so to speak.  but then again i wont be up at those hours ;)... darn kids 5am is not a fun time.

THANKS SO MUCH!!!

---

### Post by kidders on 2006-10-11
Hey again,

> **twistedtwig said:**
> so I would need to set the boys machines to a certain ip range and the adult machines to a different range
Yep, that would be the hassle-free way of doing it, because you could forget about authentication, etc. You would use DHCP to assign fixed addressess to your machines, based on their MAC addresses, and allow unrestricted access only to a small number if IPs.

> **twistedtwig said:**
> Shame you cant do it on user its self
In theory you can, but the idea isn't consistent with proxying transparently, and it's a bit of a headache to get working, sometimes. Many content filters support the idea of a "manager mode", that would let _you_ side-step restrictions at will, though.

> **twistedtwig said:**
> those machines would not be fixable out of hours so to speak.
I'm not quite sure what you mean by this. You could, for instance, whitelist a set of sites, such as Ubuntu's/Microsoft's package repositories, to allow overnight updates.

---

### Post by twistedtwig on 2006-10-11
whitelisting those sort of sites is a great idea, would lock down 99% of all the stuff.  only thing would be that they could skip the domain side of things (log into local account on computer) and play games on there without net.

I tried to not have local accounts on the computer and it all load from the server (which is an old comp) but it ran SO slowly, took a couple of minutes to load personal settings.

Thanks thats been REALLY helpful :D:D:D

Twiggy

---

### Post by kidders on 2006-10-11
No problem :-) Glad I could help.

---

