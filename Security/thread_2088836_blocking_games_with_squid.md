---
title: "blocking games with squid"
date: 2012-11-27
forum: Security
---

### Post by Leo Matheus on 2012-11-27
i want to block all access to games to a network with squid, but im not sure how do that. Im not sure if there is some thing on squid for block a get that conteins the "game" word, and any kind of applications related with games. Is squid capable of this? or i will have to make that on iptables? if so, how can i do that?

---

### Post by TheFu on 2012-11-27
There is no simple answer for this question.

I've seen that some routers have the ability to block specific protocols, that would be a place to start.  You can block different gaming IP subnets - poerhaps the where the controller is located network-wise, that should help.

I'd start with some research - 
* what games are being played that you want to block, 
* which protocols are used for those games
* can you build/create a rule to block the entire protocol without impacting anything else?

In the end, with hard work and lots of effort, you'll be left with flash-based games still available.  How to block those when they use HTTP, just like normal traffic?  Well, you could block all flash and all HTML5, but that would break much of the web - like youtube. If you can live with that, great. Go for it.

Blocking all "games" and only games is hard. Being 100% with your results will be nearly impossible.

BTW, this is a great question.

---

### Post by Lars Noodén on 2012-11-27
You could try [http://dansguardian.org/](http://dansguardian.org/) over at Sourceforge.

But that kind of filtering is funamentally flawed and cannot work, for too many reasons to go into again.  The short answer is that a social problem like that won't fall into a technical solution.

---

### Post by CharlesA on 2012-11-27
I haven't tried using squid before, but when I set up guest wireless access, I just blocked all ports except port 80 and 443.

That probably doesn't help, but if you are on my guest wifi, you can browse the internet but not do anything else - torrents and the like are blocked.

> **Lars Noodén said:**
> You could try [http://dansguardian.org/](http://dansguardian.org/) over at Sourceforge.

But that kind of filtering is funamentally flawed and cannot work, for too many reasons to go into again.  The short answer is that a social problem like that won't fall into a technical solution.

This too. ;)

---

### Post by Leo Matheus on 2012-11-28
well, i will do some research, just too bad that maybe cant be solved like that. i will follow the thefu tips and i will block the other ports aqs you say charlie, this might resolve a part of the problem.

---

### Post by TheFu on 2012-11-28
> **Leo Matheus said:**
> well, i will do some research, just too bad that maybe cant be solved like that. i will follow the thefu tips and i will block the other ports aqs you say charlie, this might resolve a part of the problem.

A whitelist of external websites is probably the easiest to implement, but also the hardest to live with.  You never said if this was a company or home network. Different issues will happen based on that aspect.

Don't forget that you need to force all DNS to be blocked by desktops and only allow the proxy to resolve external DNS. This will simplify blocking those external locations significantly.  You can setup a home network like this too. Then you can more easily block facebook, twitter, and other social networks that include games too.

Whatever you decide, please post the compromised solution later. Others will want to learn more.

---

### Post by jmcgovern on 2012-11-29
This is going to be nearly impossible to do, frankly.  Assuming you're talking about standalone programs (WoW, CoD, etc.), you can *try* to block the ports commonly used by the game.  However, a user that REALLY wants to play will just use a tunneling service to make the game traffic look like normal, permissible traffic.

Your best defense against this, really, is a very clear, well written  Acceptable Use Policy that explains what actions are and are not permitted on the network, and what the consequences for violating this policy are.

---

### Post by SeijiSensei on 2012-11-29
I block games and similar services in a workplace setting with iptables by denying communication between the clients' high ports (>1023) and remote high ports:

```
/sbin/iptables -A FORWARD -s 192.168.1.0/24 -p tcp -m tcp --sport 1024:65535 --dport 1024:65535 -j REJECT
/sbin/iptables -A FORWARD -s 192.168.1.0/24 -p udp -m udp --sport 1024:65535 --dport 1024:65535 -j REJECT
```

This keeps the router from forwarding any traffic on the LAN (192.168.1.0/24) to remote high ports.  Since these are the only ports to which ordinary users can bind services (ports < 1024 are limited to root), that's where torrents and games tend to accumulate.  

You may need to exempt some specific ports.  If you have people using things like PC Anywhere or other Citrix-based services on port 1494, add a line like this before the ones above:

```
/sbin/iptables -A FORWARD -s 192.168.1.0/24 -p tcp -m tcp --dport 1494 -j ACCEPT
```

---

### Post by Leo Matheus on 2012-11-30
well, it is a lab school network, so i cant create a whitelist of sites, since some people will be doing some research there and i cant be sure of site they will be looking for ansewers, and there isnt a DNS server on the lab, just a external dns and the students machines just have few permissions. 
the proxy is on the boder of the network, and in the same machine it has a ids sensor(snort).

---

### Post by Leo Matheus on 2012-11-30
well, it is a lab school network, so i cant create a whitelist of sites, since some people will be doing some research there and i cant be sure of site they will be looking for ansewers, and there isnt a DNS server on the lab, just a external dns and the students machines just have few permissions. 
the proxy is on the boder of the network, and in the same machine it has a ids sensor(snort).

---

### Post by SeijiSensei on 2012-11-30
That's all well and good, Leo, but squid is not capable of doing what you want.  As I said, things like games use high ports.

Now you could just block all outbound traffic through the router with iptables and only allow squid for web browsing.  But you're not going to be able to block connections to some remote high port with squid.  For that you need iptables rules.

---

### Post by CharlesA on 2012-11-30
> **SeijiSensei said:**
> That's all well and good, Leo, but squid is not capable of doing what you want.  As I said, things like games use high ports.

Now you could just block all outbound traffic through the router with iptables and only allow squid for web browsing.  But you're not going to be able to block connections to some remote high port with squid.  For that you need iptables rules.
What he said.

Your best bet would be to filter any high numbered destination port that you do not need VPN, etc.

---

