---
title: "OpenDNS Security Implications"
date: 2009-11-30
forum: Security
---

### Post by the.scarecrow on 2009-11-30
I have been testing Karmic with the intention of replacing Intrepid on my Dell Latitude D600 Laptop. Using the Live CD and a bootable USB, I immediately had problems accessing the Internet in Firefox, the WiFi and wired connections look fine but all sites time out on both, even Google. 

So I did a quick bit of research and found this solution in these forums.

Goto System>Preferences>Network Connections then edit in Wired and Wireless IPv4 Tab change from “Automatic DHCP” to “Auto (DHCP) addresses only” add IP address 208.67.222.222 in the DNS Servers box.

This works like a charm, browsing the web is if anything faster than using the hard drive installed Intrepid installation. However, I don't understand what this does. It seems to be something to do with OpenDNS of which I know nothing. As the security of Linux is top of my list of benefits when using Ubuntu and accepting that I am my computers weakest security link, I have these questions.

1	Put simply, what is Open DNS?
2	Does this reduce my privacy when accessing sites on the Internet?
3	Is there a better solution to Internet browsing problems in Karmic?
4	Has this browsing problem been fixed in any of the updates released so far?

Please help by answering any of these questions. I have read [http://en.wikipedia.org/wiki/OpenDNS](http://en.wikipedia.org/wiki/OpenDNS) about it but I don't have an account with them, it seems to just work. I know that I am a bit paranoid but better safe than sorry eh.

---

### Post by cdenley on 2009-11-30
Anytime you access a domain such as google.com or ubuntu.com, you need to query a DNS server in order to resolve that domain to an IP, such as resolving ubuntu.com to 91.189.94.156. Typically, your ISP will automatically provide you with their DNS servers via DHCP. If you use a home router or public wifi, they may assign the LAN router as your DNS server, which then forwards to another DNS server, probably their ISP's.

If you choose to manually assign OpenDNS as your DNS server, then all DNS queries will be sent directly to their free, secure DNS server, instead of your ISP's or your router. If using OpenDNS solves a network problem, then the DNS server(s) you were originally assigned probably aren't working. This indicates there is no problem with ubuntu or your computer.

The only disadvantage I could think of to using OpenDNS would be that it is probably easier to intercept your DNS queries so some third party may be able to see what domains you are accessing. Using your ISP's DNS may be safer in a way, since queries originating from your IP never have to leave your ISP. However, in most cases, using OpenDNS is probably safer than using your ISP's, in general.

Something about OpenDNS that might be a little annoying is if you access a domain which cannot be resolved, they resolve it to their own web server, which then lists suggestions for sites you may be trying to access. I believe the project is supported by ad revenue from these suggestion pages.

---

### Post by Logan1985 on 2009-11-30
I use Open DNS for both work and home and it's a good service. It's widely reputed as a secure, stable DNS choice.

Timeouts in Karmic have been fairly common, as I had the same issue. I would be tempted to set the config back to full DHCP, and then check the DNS servers that are received from your DHCP Server/Router/whatever

You can do so by firing up a shell and entering "more /etc/resolv.conf"

Are the nameservers as you would expect?

A possible reason for your issue (this was my problem) is that you may have more than one nameserver defined on your network and the first one in resolv.conf may be down/gone. Karmic seems to take ages before switching to the second nameserver in the list (which doesn't happen in Windows)

You are safe using Open DNS, but in future I would suggest you ask/check BEFORE you make the changes. Rogue DNS servers are a big security issue.

---

### Post by the.scarecrow on 2009-11-30
Hi and thanks for both your replies. I am feeling more relaxed about using OpenDNS from what you say and what I read about it, I don't care about the adverts occasionally.

I am trying out Karmic at the moment using a boot USB with 9.10 so I haven't exposed the PC to much risk and I'm not accessing any sites with critical passwords e.g. the chance of being connected to a spoof bank website.

This problem appears to be widespread and something to do with IPv6 interfering with older PCs that only support IPv4. Looking at it, the nameserver has one entry that is correct. I really like all other aspects of Karmic an so I am eager to get on with a fresh installation.

---

### Post by pbrane on 2009-11-30
I experienced this issue when I upgraded from 9.04 to 9.10. What I discovered was that at home on my Linksys (Cisco) router /etc/resolv.conf contained the nameserver addresses of my ISP and name resolution was almost instant. When I was at work on a 2Wire router /etc/resolv.conf contained the router itself as the nameserver, consequently name lookup was slower and in some cases was 10-20 seconds. I use OpenDNS at work and it seems to be fine, it is certainly _much_ faster.

I think this has more to do with the router not doing IPv6 correctly than it does with older computers. Some of the fixes that involved disabling IPv6 in FireFox did not make any difference for me.

Also I have two nameserver addresses in /etc/resolv.conf, at home, one is a primary and the other a secondary. This is normal, some ISP's even have a third or tertiary address. If the first one is down there is usually no delay. But I suppose there could be under some circumstances.

---

### Post by slakkie on 2009-11-30
> **cdenley said:**
> However, in most cases, using OpenDNS is probably safer than using your ISP's, in general.


I don't think that is true. But I work for an ISP, so I guess I have to say that ;)

I think OpenDNS is a great service, if your ISP's name servers are flacky you can use theirs. I would use my ISP's DNS servers and have OpenDNS as a backup (if I would use it).

---

### Post by the.scarecrow on 2009-11-30
more /etc/resolv.conf in Jaunty returns the IP address of the router, not the ISP DNS server. This however works ok.

Firing up Karmic more /etc/resolv.conf returns the OpenDNS address 208.67.222.222, which is understandable and this works noticeably faster than the Jaunty setup.

I don't know what the best option is, perhaps I should try the DNS IP address configured in the router. That would work here perhaps but not at other locations using a different ISP.

I really don't want to delay/not install Karmic because of this small problem but I like keeping things standard out the box as far as possible.

I did all the Karmic security updates this evening, maybe one of those has fixed it if I put it back as it was originally, but somehow I doubt it.

Thanks for your advice.

---

### Post by Bjalf on 2009-12-01
I've been using OpenDNS for more than a year, and so far, so good. No security problems, and no annoyances. No black helicopters or men in black skulking around, either!  ;)

You don't need to have an account, but it's free for home users anyway, so why not? There's a bunch of neat stuff in the free version, like web content filtering, phishing protection, typo correction and so on. [http://www.opendns.com/start/](http://www.opendns.com/start/)

Another good thing about OpenDNS is that it bypasses any overzealous ISP blocks, like when several Danish ISPs blocked access to the Pirate Bay. [http://forum.suprbay.org/showthread.php?tid=17473](http://forum.suprbay.org/showthread.php?tid=17473)

---

