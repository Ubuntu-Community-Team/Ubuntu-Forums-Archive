---
title: "What is your firewall of choise?"
date: 2008-07-01
forum: Security
---

### Post by MidnightJulia on 2008-07-01
Hi! 

I've been looking for a good firewall but I really havn't found one I like. Firestarter seems ok but I don't really like it the way I liked e g Zone Alarm for PC. So I'm on the market for another firewall. 

My question is:
* What firewall do you use?
* What are the strengths?
* What are the cons?  
* Any good tutorial for it?

/MJ

---

### Post by dje on 2008-07-01
Linux has a firewall built in called iptables, firestarter is just a frontend to configure iptables. I use UFW (Uncompilcated Firewall) which is preinstalled in Ubuntu Hardy, for a guide take a look [here]("http://www.ubuntugeek.com/ufw-uncomplicated-firewall-for-ubuntu-hardy.html"). Configuring the firewall is not necessary unless you have installed software such as OpenSSH Server and wish to restrict access of it to certain people/computers (for example)

hope that helps,
dje

---

### Post by moore.bryan on 2008-07-01
> * What firewall do you use?
[rob pectol's ubuntu-firewall]("http://rob.pectol.com/content/view/2/1/")
> * What are the strengths?
simple, straight-forward, human-readable configuration file; iptables rules can be a pain.
> * What are the cons?
for some, the lack of a gui would be a con.
> * Any good tutorial for it?
the man page and the link above are pretty extensive; it's rather simple, so there's not much to tutor.

---

### Post by hyper_ch on 2008-07-01
> **MidnightJulia said:**
> * What firewall do you use?
iptables but I leave it with no rules (so everything gets through)

> **MidnightJulia said:**
> * What are the strengths?
It's built directly into the kernel

> **MidnightJulia said:**
> * What are the cons?
don't know any cons

> **MidnightJulia said:**
> * Any good tutorial for it?
[http://www.linuxtopia.org/Linux_Firewall_iptables/](http://www.linuxtopia.org/Linux_Firewall_iptables/)

[size=5]however[/size]
I don't think you need to bother about altering the default iptables configuration.

---

### Post by Biochem on 2008-07-01
My favorite front end for iptables is shorewall ([http://www.shorewall.net/](http://www.shorewall.net/))

pros:
[LIST]
[*]Easy to use human readable config file
[*]Also configure internet sharing
[*]Capabilities to support multiple network (1 wan, 1 lan and 3 vpn)
[*]Simple to use yet very powerfull
[*]Good documentation on the website
[/LIST]

Cons:
[LIST]
[*]None in my perspective
[/LIST]

It doesn't look like Zone Alarm though. But that is more a question of personnal taste.

---

### Post by kevdog on 2008-07-01
It really depends how complex you want your firewall to be.  If hosting only a handful of services, then ufw is easy, as is firestarter. For more complicated setup, more feature rich filtering/forwarding, then working with iptables is the only way to go.  Be forewarned however that if you want to use iptables -- its very powerful but very easy to screw up.  It does take a fair amount of committment and reading to configure properly but its a great tool. I'm not sure if you can ever master iptables, however its really fun to play with.

If it was easy to master iptables -- there wouldn't be so many other programs -- ufw, firestarter, shorewall, etc that act as frontends to the program!

---

### Post by brian_p on 2008-07-01
> **MidnightJulia said:**
> * What firewall do you use?

I (and many others) use UNDIROK (Ubuntu Netfilter Default Install Rules OK)

> * What are the strengths?

No configuration required. Regular, high quality updates. Guaranteed to provide complete safety for incoming and outgoing connections. Unobtrusive.

> * What are the cons? 

There are not known to be any. Some people think that having nothing to tinker with is a disadvantage and quite a few Windows users are so shocked at how easy it is to have a secure computer that they refuse to believe it.


> * Any good tutorial for it?

There is. It is a one-liner: Keep your software up to date.

---

### Post by MidnightJulia on 2008-07-01
> **brian_p said:**
> There are not known to be any. Some people think that having nothing to tinker with is a disadvantage and quite a few Windows users are so shocked at how easy it is to have a secure computer that they refuse to believe it.


So what your saying is that Ubuntu per default is so safe that it doesn't need a firewall? 

I'm not sure I agree with you on that one. Not because Ubuntu is unsafe but because I'm new to Linux. Since I'm not sure how the inner operating system works I have much less control over it. Just today I've opened a port on the computer and I haven't got a clue how to close it. So I'd prefer another firewall (not counting my hardware firewall). 

My point is: being a curios noob is not safe.

---

### Post by hyper_ch on 2008-07-01
> **MidnightJulia said:**
> So what your saying is that Ubuntu per default is so safe that it doesn't need a firewall?
Yes

> **MidnightJulia said:**
> I'm not sure I agree with you on that one. Not because Ubuntu is unsafe but because I'm new to Linux. Since I'm not sure how the inner operating system works I have much less control over it. Just today I've opened a port on the computer and I haven't got a clue how to close it. So I'd prefer another firewall (not counting my hardware firewall). 
You don't have any services running by default... only when you start installing services...
And besides, the reason windows also needs an outgoing firewall is because of all that spy/crapware gets added - a lot of programs that you get from shady sources and even retail stuff "phones" home....

On linux you don't have that crapware integrated... so there's by default no need for a firewall.

and if you have a firewall in your router, you're better of configuring that one for the benefit of your whole network.

---

### Post by MidnightJulia on 2008-07-01
> **dje said:**
> Linux has a firewall built in called iptables, firestarter is just a frontend to configure iptables. I use UFW (Uncompilcated Firewall) which is preinstalled in Ubuntu Hardy, for a guide take a look [here]("http://www.ubuntugeek.com/ufw-uncomplicated-firewall-for-ubuntu-hardy.html"). Configuring the firewall is not necessary unless you have installed software such as OpenSSH Server and wish to restrict access of it to certain people/computers (for example)

hope that helps,
dje

I really liked UFW acutely - very straight forward. Thanks :)

---

### Post by MidnightJulia on 2008-07-01
> **hyper_ch said:**
> Yes


You don't have any services running by default... only when you start installing services...
And besides, the reason windows also needs an outgoing firewall is because of all that spy/crapware gets added - a lot of programs that you get from shady sources and even retail stuff "phones" home....

My system isn't a default system. I am constantly installing and running new applications just for the sake of learning. And now and then I open a port or something that I shouldn't. Since I'm new I'm not always able to repair the damage. So Ubuntu might not need a firewall - but I do. 

Another thread: Isn't the point of running a firewall more about keeping crackers out than protecting against windowsware? 

> **hyper_ch said:**
> and if you have a firewall in your router, you're better of configuring that one for the benefit of your whole network.

It is configured. But that doesn't mean I can't use a software firewall also :)

---

### Post by hyper_ch on 2008-07-01
what will iptables help you if you have a configure firewall?

well, in windows you have to block outgoing connections as often as incoming ones ;) hence in windows a firewall has other purposes than here.

---

### Post by brian_p on 2008-07-01
> **MidnightJulia said:**
> My system isn't a default system. I am constantly installing and running new applications just for the sake of learning. And now and then I open a port or something that I shouldn't.

That's good. Explore all you want. You can do no harm if you don't alter the default configurations of services and you familiarise yourself with the basic documentation if you do make changes.

> Since I'm new I'm not always able to repair the damage.

There is no damage done by opening a port.

> So Ubuntu might not need a firewall - but I do.

So, it's not the OS which needs fixing then.

---

### Post by Chayak on 2008-07-02
Cisco ASA5505 Sec +

Upside is that it's a very powerful and feature filled device that can do everything from DMZs with varying security levels to point-to-point vpn tunnels and act as a VPN server.

Downside is it's expensive and compicated.  I work with ASAs quite a bit and I still find myself cracking open a book from time to time.  ASDM makes it a bit easier but you still have to know how cisco does things to configure it properly.

---

### Post by vishzilla on 2008-07-02
i personally use ufw, really simple cli tool

---

### Post by MidnightJulia on 2008-07-02
> **brian_p said:**
> That's good. Explore all you want. You can do no harm if you don't alter the default configurations of services and you familiarise yourself with the basic documentation if you do make changes.

Ubuntu is acutely the first operating system I feel is really interesting to work with. I've used Windows since 3.1 untill Vista & Mac OS since 7.1 until Leopard but I've never felt the interest to dig deeper into their inner workings. So I really like Ubuntu even if I don't understand half of what I'm doing right now. :D


> There is no damage done by opening a port.

Still open ports are (if I'm not mistaken) an invite for crackers? Isn't it better to have the computer just drop the packages?

> So, it's not the OS which needs fixing then.

Maybe not :)

---

### Post by brian_p on 2008-07-02
> **MidnightJulia said:**
> Still open ports are (if I'm not mistaken) an invite for crackers? Isn't it better to have the computer just drop the packages?

Your software is up to date? It doesn't matter if the packets are accepted, rejected or dropped, a cracker can do nothing. The vast majority of intrusions attempts are automated anyway and easily countered with Ubuntu default daemon configurations. There is nothing to fear.

You would have to really go out of your way to make a default configuration unsafe. Taking exim4 as an example you could have it relay mail for anyone on the internet, but that would imply ignoring all the warnings about how unwise it would be or not bothering to read them. Having made that choice the firewall would be unable to provide any protection.

---

### Post by MidnightJulia on 2008-07-02
> **brian_p said:**
> Your software is up to date? It doesn't matter if the packets are accepted, rejected or dropped, a cracker can do nothing. The vast majority of intrusions attempts are automated anyway and easily countered with Ubuntu default daemon configurations. There is nothing to fear.

I always update my software. Every time I boot up I check for updates to be honest :)

Interesting! This is completely new for me. But isn't it to prefer that packets are silently dropped rather than the computer answers that the port is open? If the cracker has a 0 day exploit and there isn't a patch it seems to me like you've got a problem.

---

### Post by MidnightJulia on 2008-07-02
> **Chayak said:**
> Cisco ASA5505 Sec +

Upside is that it's a very powerful and feature filled device that can do everything from DMZs with varying security levels to point-to-point vpn tunnels and act as a VPN server.

Downside is it's expensive and compicated.  I work with ASAs quite a bit and I still find myself cracking open a book from time to time.  ASDM makes it a bit easier but you still have to know how cisco does things to configure it properly.

Hardware firewalls are truly the best: hardend bests that seem to work  much better than their software counterparts. Our network is protected by something like your Cisco and it's really great. More or less everything is stopped before it even get into the network. 

I'd think they're quite hard to configure correctly. But I really don't know since I don't own the firewall so I've never needed to configure it ;) No but seriously -  it quite cool, so I'd love to learn.

---

### Post by jerome1232 on 2008-08-08
Sitting behind my router, except it doesn't log rejected packets; UFW/iptables does. So I put my little server in dmz mode and use UFW for my simple firewall needs.

---

### Post by cariboo on 2008-08-08
I have a Linksys wrt54gs, that's my firewall. If it weren't for the router I would use [Arno's Iptables Firewall]("http://rocky.eld.leidenuniv.nl/")

This is really just an iptables script, but it is really comprehensive. It is available in the repositories.

Jim

---

