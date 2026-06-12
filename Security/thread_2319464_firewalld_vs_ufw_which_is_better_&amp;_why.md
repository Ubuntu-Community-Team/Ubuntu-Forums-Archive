---
title: "firewalld vs ufw which is better &amp; why?"
date: 2016-04-04
forum: Security
---

### Post by trpted on 2016-04-04
Hello.

I have both installed and like the title says. 

I appreciate the help.

Thank you.

---

### Post by Geoffrey_Arndt on 2016-04-04
Whichever is the easier to use, as they are both front-ends (gui) for the iptables protocol in Linux:   [https://www.digitalocean.com/community/tutorials/how-the-iptables-firewall-works](https://www.digitalocean.com/community/tutorials/how-the-iptables-firewall-works)

---

### Post by slickymaster on 2016-04-04
*Moved to the ***Security*** sub-forum*

---

### Post by trpted on 2016-04-04
> **Geoffrey_Arndt said:**
> Whichever is the easier to use, as they are both front-ends (gui) for the iptables protocol in Linux:   [https://www.digitalocean.com/community/tutorials/how-the-iptables-firewall-works](https://www.digitalocean.com/community/tutorials/how-the-iptables-firewall-works)

Ok.

Which is easier to use and why?

Thank you

---

### Post by QDR06VV9 on 2016-04-04
For server administrators it doesn’t really matter which one you use.  ufw is disabled by default in Ubuntu Server edition but is very trivial  to learn and enable but FirewallD is enabled by default in Fedora and  Red Hat Enterprise but the more complex syntax may require more  learning.
I like UFW, its easy and theres a lot of good documentation out there its a good choice if you want to to learn iptables syntax.

ufw is a full featured interface for the CLI, while firewalld  mostly just provides an API and you'd have to use another program on  top of that. I haven't used firewalld much myself, but ufw does have a  lot of experience/exposure as it's the recommended tool for Ubuntu-based  distros. (Perhaps debian as well, but I haven't seen an official  position one way or the other.)

---

### Post by 1clue on 2016-04-04
I just use iptables.

---

### Post by trpted on 2016-04-06
I use (the GUI) firewall-applet to control firewalld and use (the GUI) gufw to control ufw.

Between the two, which is better and why?

I appreciate the help.

Thank you.

---

### Post by trpted on 2016-04-06
Duh! on me.

I have both firewall-applet and gufw.

I know it says solved, but it more like Sort of solved. Thread/issue continues at [http://ubuntuforums.org/showthread.php?t=2319684](http://ubuntuforums.org/showthread.php?t=2319684)

---

### Post by howefield on 2016-04-06
Threads merged.

---

### Post by keith-k on 2016-04-07
I use iptables also obviously on my servers and on desktop. Besides my own rules I always install fail2ban. It is surprising to see how many ip addresses are temporarily banned from incorrect logins. Most from China.

---

### Post by HermanAB on 2016-04-08
The actual firewall is the netfilter kernel module.  Iptables is a front-end for netfilter and all the other utilities are front-ends for the front-end.  So you can just as well read the iptables man page a few times and then get rid of the other cruft.

---

### Post by Morbius1 on 2016-04-08
"Better" is a relative term. I'm not the best person to comment on firewalls since in my universe Linux is not used on anything mobile ( laptops, phones, tablets ) so I don't use "firewalls" on it. And I only played around with FirewallD once out of curiosity but I would think it holds promise for those that use firewalls on Linux. I'll give you one example. 

Gufw introduced profiles lately: Home, Office, Public. That's great but it has to be enabled manually because it has no way to determine to what "network" it's connected.

FirewallD - or more precisely NetworkManager ( as in nm-connection-editor ) which supports FirewallD - can assign a "firewall zone" to things like Home and Office based on the connection itself.

---

### Post by 1clue on 2016-04-08
@Morbius1,

Some of us use Linux as a firewall for private networks.

Even if you don't use your linux box for anything unusual, IMO you should have a firewall anyway. You should take a few minutes to decide what sort of remote access should be allowed in on each box, and block everything else.

SOHO (small office/home office) routers are notoriously easy to hack. Assuming that you can't be hacked because you're behind a firewall with NAT is not a good idea.

---

### Post by trpted on 2016-04-08
> **1clue said:**
> Assuming that you can't be hacked because you're behind a firewall with NAT is not a good idea.

Especially when in the long term future with IPv6, as with IPv6 there is no NAT.

---

### Post by trpted on 2016-04-08
> **Morbius1 said:**
> "Better" is a relative term. I'm not the best person to comment on firewalls since in my universe Linux is not used on anything mobile ( laptops, phones, tablets ) so I don't use "firewalls" on it. And I only played around with FirewallD once out of curiosity but I would think it holds promise for those that use firewalls on Linux. I'll give you one example. 

Gufw introduced profiles lately: Home, Office, Public. That's great but it has to be enabled manually because it has no way to determine to what "network" it's connected.

FirewallD - or more precisely NetworkManager ( as in nm-connection-editor ) which supports FirewallD - can assign a "firewall zone" to things like Home and Office based on the connection itself.

Interesting reply.

With FirewallD - or more precisely NetworkManager: 

a) The computer must have at least two NICs

b) OR does it do it by the IP Address (For example: That is what my Windows 7 computer does)

?

Thank you.

PS #1 Not including any computer acting as NAT Router (if any): All of my computer(s) only have one NIC.

#2 And my computers are not a portable computer(s).

---

### Post by 1clue on 2016-04-09
I manage lots of linux boxes. Almost none of them are portable. Absolutely all of them have firewall rules active. Non-mobility and so-called protected networks have little or nothing to do with it. Some of the boxes I deal with are behind 2 physically separate enterprise grade firewalls, and I take every bit as much care locking them down as the ones on the open Internet.

To continue with this line of thought, the presence of wifi makes risk of intrusion much higher.

The easy proliferation of malware on every platform (including Linux) makes it necessary to not only have defense for your network but also for each computer and vm on it.

There are lots of ways to get owned.

---

### Post by Morbius1 on 2016-04-09
You are forcing me to spend way too much time with something I don't use. But it's my own fault for posting in the first place. :smile:
> **trpted said:**
> #2 And my computers are not a portable computer(s).
Well, if all of your machines are part of your own network and don't find themselves out and about then you don't need the very feature of firewalld I posted about. ufw / gufw should be fine as is.

Anyhoo, What I was talking about was something like this: [ATTACH=CONFIG]268260[/ATTACH]

You configure the services you want to allow in firewalld for the Home zone and then you specify that zone in network manager for that connection.

For example, In my home network I have a samba server enabled on this box ( Ubuntu 15.10 - VBox guest ). So I would configure the "Home" Zone to allow Samba, and set the "Interface" to be my wired network adapter: [ATTACH=CONFIG]268261[/ATTACH]

[I][COLOR=#0000cd]**Edit** -  Side Note to Lennart Poettering: How in the world did you think that "enp0s3" was more intuitive or in any way an improvement over "eth0".[/COLOR]
[/I]
For a Public zone I wouldn't allow samba

---

### Post by trpted on 2016-04-11
Sorry my info came out wrong. I meant to say

> 
#1 Not including any computer acting as NAT Router (if any): All of my computer(s) only have one NIC.

#2 And my computers do not have a wireless NIC / do not use wireless.


#3 It is still true, my computers are not a portable computer(s).

Does the above info on what I meant to say, change anything?

Thank you

---

### Post by 1clue on 2016-04-11
> **trpted said:**
> Sorry my info came out wrong. I meant to say



#3 It is still true, my computers are not a portable computer(s).

Does the above info on what I meant to say, change anything?

Thank you

All of my comments on this thread apply to the scenario you describe here. In my opinion security does not stop at a firewall or a trusted network. You should assume that some computer on your network could become compromised via some exploit you don't know about, or through user error. Are you safe from your own computers?

As I've said repeatedly here, I recommend some iptables rules on every Linux box, and appropriate firewall settings on every other box too. Nothing complicated. Most boxes would simply turn off all access initiated by a computer outside your network, or even any initiated by non-localhost. Each box you should look at the services running, decide what services you want to allow and where to allow them, and block everything else.

---

### Post by trpted on 2016-04-11
> 
Well, if all of your machines are part of your own network and don't find themselves out and about then you don't need the very feature of firewalld I posted about. ufw / gufw should be fine as is.



*Solved*

---

