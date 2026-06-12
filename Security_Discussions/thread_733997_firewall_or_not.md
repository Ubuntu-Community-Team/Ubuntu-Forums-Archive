---
title: "firewall or not"
date: 2008-03-24
forum: Security Discussions
---

### Post by mistux on 2008-03-24
I just set up Ubuntu 7 and instaleld Gallery2 for shairing my family photos.  Along with Apachie and PHP.  All is working just fine on my local network, but now I want to move it over to the outside world, i.e. the Internet.

My question is do I need to have a firwall on it?  I've read mixed thoughts on the need for one on a Linux box (as I am comming from the Windows world, where I previously had my Gallery2 installed...but it crashed so I took the oportunity to switch it over to Ubuntu and am teaching myself about the Linux/Ubuntu world)

My current network has a dedicated firewall on it, but I had the old Windows/Gallery2 box connected outside it like this:  
```

Cable Modem-->Linksys Router-->Windows/Gallery2 (with Windows bult in firewall)
                            I-->Firwall-->my network
```
*Note: the Linksys Router is also our VOIP device which is why I have it connected to the modem and outside the firewall where I don't need the extra phone traffic.*

My thought is to do the same thing and put the new Ubuntu/Gallery2 box at the same point that I had my old Windows/Gallery2 box.

```

Cable Modem-->Linksys Router-->Ubuntu/Gallery2 
                            I-->Firwall-->my network
```

The Ubuntu/Gallery2 box won't be used for anything else put serving up pictures.

So, do I need to put a firewall on it (like Firestarter) or what are your thoughts?

Thanks.

---

### Post by muchas on 2008-03-24
I would say just set up a firewall. it won't eat that much of space on your HD so why not? Just a precaution. Linux may be called as virus free but we can't call it hacker/etc.. free... LoL so I suggest install a firewall.

---

### Post by cdenley on 2008-03-24
You don't need a software firewall since your linksys router acts as one, and you probably won't have any servers running that you need to block. However, it couldn't hurt, except for the inconvenience of having to specify what traffic to allow.

---

### Post by The Cog on 2008-03-25
I don't see any point in setting up a firewall - what would you do with it? You are only running one service and that's apache. So only port 80 needs protecting. But that's the only port you would have to open in your firewall rules anyway because you want the internet to have access to it.

A firewall would only be useful if either you were running other services that you want to prevent access to, or you wanted to limit access to certain preferred remote IP addresses (or perhaps to block foreign IP address ranges).

---

### Post by hyper_ch on 2008-03-25
> **The Cog said:**
> I don't see any point in setting up a firewall - what would you do with it? You are only running one service and that's apache. So only port 80 needs protecting. But that's the only port you would have to open in your firewall rules anyway because you want the internet to have access to it.

A firewall would only be useful if either you were running other services that you want to prevent access to, or you wanted to limit access to certain preferred remote IP addresses (or perhaps to block foreign IP address ranges).

+1

---

### Post by wieman01 on 2008-03-26
> **The Cog said:**
> I don't see any point in setting up a firewall - what would you do with it? You are only running one service and that's apache. So only port 80 needs protecting. But that's the only port you would have to open in your firewall rules anyway because you want the internet to have access to it.

A firewall would only be useful if either you were running other services that you want to prevent access to, or you wanted to limit access to certain preferred remote IP addresses (or perhaps to block foreign IP address ranges).
Unless there are services running that you are not aware of. That's why I decided to install "Firestarter" which does all the configuration for me. Certainly, I only need it because I am too lazy to remove all the critical services that I installed at one point in time. 

I would say I agree with you, however, if you aren't sure what other service are running (e.g. SSH server) and you want to block them, then install Firestarter or configure IP tables manually. 

For laptop users a firewall makes sense by all means.

---

### Post by Sporkman on 2008-03-31
I run a firewall on my server, in case there are services that I'm not aware of upon install, or installed or enabled after the fact due to my own incompetence. Also, it'll put up an extra hurdle in case the machine gets hacked & a malicious service gets installed.

---

### Post by brian_p on 2008-04-02
> **Sporkman said:**
> I run a firewall on my server, in case there are services that I'm not aware of upon install, or installed or enabled after the fact due to my own incompetence.

Why not become aware of them and increase your competence by using netstat? 

>  Also, it'll put up an extra hurdle in case the machine gets hacked & a malicious service gets installed.

Not offering the service means the extra hurdle is superfluous.

---

### Post by brian_p on 2008-04-02
> **wieman01 said:**
> Unless there are services running that you are not aware of. That's why I decided to install "Firestarter" which does all the configuration for me. Certainly, I only need it because I am too lazy to remove all the critical services that I installed at one point in time. 

Too lazy to use netstat. Tut, tut.

> I would say I agree with you, however, if you aren't sure what other service are running (e.g. SSH server) and you want to block them, then install Firestarter or configure IP tables manually. 

I would say he should become sure. It's not Windows and it's easy enough.

> For laptop users a firewall makes sense by all means.

I don't follow this. If no services are being offered the firewall is unnecessary. If they are, you can't block the port it is listening on.

---

### Post by wieman01 on 2008-04-02
> **brian_p said:**
> Too lazy to use netstat. Tut, tut.
I would say he should become sure. It's not Windows and it's easy enough.

I don't follow this. If no services are being offered the firewall is unnecessary. If they are, you can't block the port it is listening on.
True. But again, if you aren't sure what services are installed (in particular if you are a laptop user and do roaming) then a firewall will offer good protection.

I agree with you, disabling all unnecessary services in the first place is the right approach, but sometimes it isn't practical. I - for instance - have Samba enabled by default because I need it for my home network. When I travel, I don't disable Samba but block the respective ports. As simple as that.

So, yes, disabling all services is a good thing to do. But it isn't a must. There is more than 1 school of thought.

---

### Post by brian_p on 2008-04-02
> **The Cog said:**
> I don't see any point in setting up a firewall - what would you do with it? You are only running one service and that's apache. So only port 80 needs protecting. But that's the only port you would have to open in your firewall rules anyway because you want the internet to have access to it.

Nicely logical. There is a listener on port 80. No point in blocking it. So +2.

> A firewall would only be useful if either you were running other services that you want to prevent access to, or you wanted to limit access to certain preferred remote IP addresses (or perhaps to block foreign IP address ranges).

If you do not want a service to be accessed you turn it off. Limiting access is better done from within apache. A firewall is not required.

---

### Post by wieman01 on 2008-04-02
> **brian_p said:**
> Nicely logical. There is a listener on port 80. No point in blocking it. So +2.

If you do not want a service to be accessed you turn it off. Limiting access is better done from within apache. A firewall is not required.
Yes, I think we've got your point. In principle it isn't necessary, I/we very much agree with it. But this also depends on the circumstances.

So let's move on.

---

### Post by brian_p on 2008-04-02
> **wieman01 said:**
> True. But again, if you aren't sure what services are installed (in particular if you are a laptop user and do roaming) then a firewall will offer good protection.

As I said, its easy to be sure.

> I agree with you, disabling all unnecessary services in the first place is the right approach, but sometimes it isn't practical. I - for instance - have Samba enabled by default because I need it for my home network. When I travel, I don't disable Samba but block the respective ports. As simple as that.

/etc/init.d/samba stop

doesn't look particularly impractical or complex.

---

### Post by wieman01 on 2008-04-02
> **brian_p said:**
> As I said, its easy to be sure.

/etc/init.d/samba stop

doesn't look particularly impractical or complex.
Command line after every boot? Yeah, very practical. 

Don't get me wrong, we have got the message. But for practical reasons, it's not always convenient to stop services. A firewall (IP tables) comes in handy. That's all we are saying if you read the posts carefully.

_**EDIT:**_

I think it is rather pointless to continue this discussion. Everything's been said, so the OP needs to find a balance between convenience & security.

---

### Post by netlogic on 2008-04-03
Firewall

Why?
1. sometimes, service applications will have bugs. Apache, Openssl, Vsftp all had vulnerabilities in the past. Programmers are humans too.
2. TC (traffic control). Someone wants to bang on your server, slow them down.
3. Better way to handle your DoS attacks.  
4. You already have a firewall in your kernel if you haven't compiled it yourself. 
5. Traffic control based on your logs
6. Block unnecessary attacks by logs

If your Linksys router has a Linux kernel, I would say, it isn't necessary. Home routers are just routers. They are NAT devices. Today's firewall isn't just a packet filtering router.

---

### Post by lespaul_rentals on 2008-04-03
I don't have a full-blown firewall on my home server.  I'm behind NAT and the only ports that are forwarded to my server are FTP, HTTP, and SSH.  Even if I weren't behind NAT, what would be the point?  I use iptables (having a firewall built into the kernel is one of my favorite things about Linux) to block access to any services I want to keep running for the localhost but don't want the LAN or WAN to have access to.  I also use iptables to block IP address ranges that bruteforce my FTP server.  But honestly, why have a firewall to block already closed ports?

The only situation I could see a full firewall as being helpful would be if a malicious hacker owned a system and installed a rootkit or backdoor.  The firewall rules would prevent the malicious program from accessing the Internet, but any hacker worth his salt would know to add exceptions to the firewall to allow his service network access.  Thus, in Linux, iptables and other firewalls are great tools for the sys admin, but other than that, the practicality is questionable.

If you want to see if you are secure, run a thourough Nmap scan on yourself.  If you see any open ports, that indicates a listening service.  If it's something you want to share with the world (Apache server, for example) then you will need to leave it open.  If it's something that might be vulnerable to exploitation or misuse (cupsys, for example) either stop the service or block the port with iptables.

---

### Post by netlogic on 2008-04-03
hmm... firewall isn't always a two interface machine. iptables is a firewall. firewall doesn't have to be a dedicated device. if you are utilizing iptables, you are running a firewall. you are doing more than yanking out services. you are doing more than blocking a port by removing a service.

---

