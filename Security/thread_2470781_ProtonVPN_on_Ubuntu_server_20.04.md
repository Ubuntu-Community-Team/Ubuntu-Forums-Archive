---
title: "ProtonVPN on Ubuntu server 20.04"
date: 2022-01-11
forum: Security
---

### Post by johndid on 2022-01-11
Hi everybody,

I was thinking about installing ProtonVPN on my linux ubuntu server 20.04:

[https://protonvpn.com/support/linux-vpn-tool-early-access/](https://protonvpn.com/support/linux-vpn-tool-early-access/)

I use this VPN on my Windows PC already and it works quite well usually.

Has anyone experienced this VPN on a linux machine without GUI?
Your thought, please
Thanks

---

### Post by TheFu on 2022-01-11
a) just because something works, that hardly means it is secure or that your specific setup is secure.
b) VPNs should be based off one of these tools and we should load those standard packages, no use whatever "magic" the provider creates for normal desktops.

** ipsec (part of the IPv6 spec)
** L2VPN (older, but with correct setup and authentication, highly secure)
** openvpn (old standby using TLS.  Ensure TLS v1.3+ are used)
** wireguard (fast, new, might be fine, but ... nobody really knows for sure)

ProtonVPN is reputable, but we shouldn't blindly trust anyone or new products.

If you are simple trying to download stuff from parts of the world for entertainment, then I wouldn't worry too much.
If your connection is already scrutinized by your ISP for bad behavior, I'd use a proven solution, for the next year+.
If your life depends on this VPN working, run away from "new".

As always, *new* is the enemy of stable and proven.

---

### Post by DuckHook on 2022-01-11
Though I have no experience with ProtonVPN per se, I will hazard some comments on the larger context:

[LIST]
[*]If you already use it in Windows, then you already have an existing account, an understanding of its throughput/efficacy in your area and are presumably happy with it. Therefore, it is only natural to extend it to Linux as well. No added cost or vetting needed.
[*]The whole VPN world has sadly gotten very shady in recent times. It's depressing, but much of the degradation has been due to scoundrels buying up commercial VPN providers—said scoundrels having made their fortunes as malware merchants (when the mafia start buying security companies, it would be wise to avoid such companies too).
[*]Fortunately, more reputable players are now getting into the game. I believe that Proton is one of the reputable ones—though my knowledge is admittedly based only on cursory research to date. Mozilla is now also a player I have some trust in.
[*]The industry consolidation by scoundrels has been vexing, and I've had to switch VPN providers twice in the last three years. I'm curious what your experience with Proton has been like.
[*]Though setting up a VPN on a Linux non-GUI server is not a trivial exercise, it isn't oppressively arcane or obscure either. FWIW, I don't like the "wizards" and auto&#8209;configuration apps from vendors, even vendors that I trust. I don't know how well such apps are coded and setting up the VPN with Ubuntu's native tools is not oppressively difficult, so I prefer to not introduce yet another attack surface.
[*]Though it applies to my current provider (NordVPN) I wrote [this guide]("https://blog.simos.info/how-to-use-nordvpn-in-a-lxd-container/") for setting up a VPN using only Ubuntu's native tools. It's at the bottom of Simo's blog in the comments. No need for any auto&#8209;config deb app. It can probably be used as a template for ProtonVPN too with minimal adjustments. It will require you to find Proton's listing of worldwide VPN servers. That part would be up to you.
[/LIST]
I highly encourage you to explore VPN on your server. Once you are past the initial learning curve (which is appreciable but not insurmountable), you will find it very useful.

---

### Post by johndid on 2022-01-11
> **TheFu said:**
> a) just because something works, that hardly means it is secure or that your specific setup is secure.
b) VPNs should be based off one of these tools and we should load those standard packages, no use whatever "magic" the provider creates for normal desktops.

** ipsec (part of the IPv6 spec)
** L2VPN (older, but with correct setup and authentication, highly secure)
** openvpn (old standby using TLS.  Ensure TLS v1.3+ are used)
** wireguard (fast, new, might be fine, but ... nobody really knows for sure)

ProtonVPN is reputable, but we shouldn't blindly trust anyone or new products.

If you are simple trying to download stuff from parts of the world for entertainment, then I wouldn't worry too much.
If your connection is already scrutinized by your ISP for bad behavior, I'd use a proven solution, for the next year+.
If your life depends on this VPN working, run away from "new".

As always, *new* is the enemy of stable and proven.

I am aware that there is no VPN service out there that you can totally trust or rely on, however reputable they can be considered.
In fact, my question wasn't about trust or any kind of magic they can do.
I just wanted to know if someone has already used it and come across problems of any kind (setup expecially) that can make the service unreliable in linux.

Thanks

---

### Post by DuckHook on 2022-01-11
> **johndid said:**
> I am aware that there is no VPN service out there that you can totally trust or rely on, however reputable they can be considered.
In fact, my question wasn't about trust or any kind of magic they can do.
I just wanted to know if someone has already used it and come across problems of any kind (setup expecially) that can make the service unreliable in linux.

Thanks
These being forums (vs a help desk), you are bound to get meta&#8209;answers to your queries. Frankly, we pride ourselves on being able to help newcomers with a larger picture that many of them are not even aware exists. We have no idea of your general computer savvy, hence the colour commentary.

And advice from an old-time guru like TheFu should not be causally dismissed.

There is this: [https://techcrunch.com/2021/09/06/protonmail-logged-ip-address-of-french-activist-after-order-by-swiss-authorities/](https://techcrunch.com/2021/09/06/protonmail-logged-ip-address-of-french-activist-after-order-by-swiss-authorities/)
&#8230;although, in their defence, they did go to bat for users like us and ultimately prevailed: [https://www.reuters.com/technology/proton-wins-swiss-court-appeal-over-surveillance-rules-2021-10-22/](https://www.reuters.com/technology/proton-wins-swiss-court-appeal-over-surveillance-rules-2021-10-22/)

As for installation/configuration, see my prior post, although that also comes with its share of meta-commentary.

---

### Post by johndid on 2022-01-11
> **DuckHook said:**
> Though I have no experience with ProtonVPN per se, I will hazard some comments on the larger context:

[LIST]
[*]If you already use it in Windows, then you already have an existing account, an understanding of its throughput/efficacy in your area and are presumably happy with it. Therefore, it is only natural to extend it to Linux as well. No added cost or vetting needed. 
[*]The whole VPN world has sadly gotten very shady in recent times. It's depressing, but much of the degradation has been due to scoundrels buying up commercial VPN providers—said scoundrels having made their fortunes as malware merchants (when the mafia start buying security companies, it would be wise to avoid such companies too). 
[*]Fortunately, more reputable players are now getting into the game. I believe that Proton is one of the reputable ones—though my knowledge is admittedly based only on cursory research to date. Mozilla is now also a player I have some trust in. 
[*]The industry consolidation by scoundrels has been vexing, and I've had to switch VPN providers twice in the last three years. I'm curious what your experience with Proton has been like. 
[*]Though setting up a VPN on a Linux non-GUI server is not a trivial exercise, it isn't oppressively arcane or obscure either. FWIW, I don't like the "wizards" and auto&#8209;configuration apps from vendors, even vendors that I trust. I don't know how well such apps are coded and setting up the VPN with Ubuntu's native tools is not oppressively difficult, so I prefer to not introduce yet another attack surface. 
[*]Though it applies to my current provider (NordVPN) I wrote [this guide]("https://blog.simos.info/how-to-use-nordvpn-in-a-lxd-container/") for setting up a VPN using only Ubuntu's native tools. It's at the bottom of Simo's blog in the comments. No need for any auto&#8209;config deb app. It can probably be used as a template for ProtonVPN too with minimal adjustments. It will require you to find Proton's listing of worldwide VPN servers. That part would be up to you. 
[/LIST]
I highly encourage you to explore VPN on your server. Once you are past the initial learning curve (which is appreciable but not insurmountable), you will find it very useful.


Yes, I heard about the "very hard time", to say the least, the VPN world has gone through over the last few years, and I know that you can't totally trust them.
Actually, I rarely use ProtonVPN on my Windows PC, and I would barely use it on my linux server. It would basically be for learning purpose, I mean, how to set it up the right way, learn something more, and have a new service on my Ubuntu server that might come in handy someday.
By the way, thank you for the link.

---

### Post by DuckHook on 2022-01-11
> **johndid said:**
> Yes, I heard about the "very hard time", to say the least, the VPN world has gone through over the last few years, and I know that you can't totally trust them.
Actually, I rarely use ProtonVPN on my Windows PC, and I would barely use it on my linux server. It would basically be for learning purpose, I mean, how to set it up the right way, learn something more, and have a new service on my Ubuntu server that might come in handy someday.
By the way, thank you for the link.
You're more than welcome. I'm a fellow explorer/tinkerer at heart too.

Given your use case, I would encourage you to look at the whole of Simo's article. It's even fruitful to look at his entire blog. It's a way of segregating the whole VPN into a container, then invoking it only when what you really want is a VPN. I find such fine-grained control to be very useful.

A summary tutorial is in my sig: Sandboxing Apps with LXD

---

### Post by johndid on 2022-01-11
> **DuckHook said:**
> 

And advice from an old-time guru like TheFu should not be causally dismissed.

There is this: [https://techcrunch.com/2021/09/06/protonmail-logged-ip-address-of-french-activist-after-order-by-swiss-authorities/](https://techcrunch.com/2021/09/06/protonmail-logged-ip-address-of-french-activist-after-order-by-swiss-authorities/)
&#8230;although, in their defence, they did go to bat for users like us and ultimately prevailed: [https://www.reuters.com/technology/proton-wins-swiss-court-appeal-over-surveillance-rules-2021-10-22/](https://www.reuters.com/technology/proton-wins-swiss-court-appeal-over-surveillance-rules-2021-10-22/)



I was doing anything but dismissed his advice, and I'm anything but a linux expert. I was just clarifying what my question was about. Interesting articles, I am going to read them through carefully. Thanks

---

### Post by johndid on 2022-01-11
> **DuckHook said:**
> You're more than welcome. I'm a fellow explorer/tinkerer at heart too.

Given your use case, I would encourage you to look at the whole of Simo's article. It's even fruitful to look at his entire blog. It's a way of segregating the whole VPN into a container, then invoking it only when what you really want is a VPN. I find such fine-grained control to be very useful.

A summary tutorial is in my sig: Sandboxing Apps with LXD


Too much information at once ahahhah, but thanks!

I have a few services on my Ubuntu server running as docker containers, it would be great if a docker container for ProtonVPn or something exists, and an article about how to properly set it up.
I hardly experienced LXD, just one time on Proxmox.
Thanks

---

### Post by DuckHook on 2022-01-11
> **johndid said:**
> Too much information at once ahahhah, but thanks!

I have a few services on my Ubuntu server running as docker containers, it would be great if a docker container for ProtonVPn or something exists, and an article about how to properly set it up.
I hardly experienced LXD, just one time on Proxmox.
Thanks
The only container platform I use is LXD. Sorry. This old brain also breaks down with information overload so I know where you are coming from. Docker is a fine platform but you will have to seek that knowledge from others.

If you wish to install the VPN on the host itself, then the procedure outlined in the above link will work. No container needed.

---

