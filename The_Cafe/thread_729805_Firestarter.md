---
title: "Firestarter"
date: 2008-03-20
forum: The Cafe
---

### Post by hyper_ch on 2008-03-20
Is it me or does firestarter make more problems than it solves?

I keep reading that those who install firestarter get blocked everything... nothing works anymore and they sort of have a challenge to either configure firestarter correctly or remove it (plus all it's iptables entries).

While back on widnows I did also have a PFW installed but not anymore since I've been using linux... iptables runs but by default no ports are closed there (until one installs firestarter).

I haven'd had any issue and I have a firewall on my router that I did configure to some extend...

I have come meanwhile to the conclusion that if you have a firewall on your router you shouldn't bee needing a firewall on your computer any longer and that it will save you much trouble.

---

### Post by kjb34 on 2008-03-20
I haven't really had any problems with firestarter. I just let it run in the background and it does its job.

---

### Post by kpkeerthi on 2008-03-20
> **hyper_ch said:**
> t if you have a firewall on your router you shouldn't bee needing a firewall on your computer any longer and that it will save you much trouble.

Exactly.

---

### Post by Dr Small on 2008-03-20
I have had lots of problems with Firestarter in the past. Sometimes it just simply doesn't work.... but I still use it :|

Dr Small

---

### Post by notwen on 2008-03-20
> if you have a firewall on your router you shouldn't bee needing a firewall on your computer any longer and that it will save you much trouble.

Bingo. =]

---

### Post by the yawner on 2008-03-20
I haven't checked my Xubuntu install i a while. But last time I was tweaking it, I noticed that there seems to be a conflict between Firestarter and Network Manager.

---

### Post by intense.ego on 2008-03-20
I  believe I am one of the people you are refering to when you say firestarter causes a lot of problems, but that is simply because of my noobishness. The problem was easily solved and everything works fine. 

When I used feisty, my whole internet connection would be blocked by default and the only way to solve it was to stop firestarter, wait a second, and then start it again.

Those are the only two problems I have had.

I use it because I use a cheapo wireless router that came with the internet connection and I am not sure how good the firewall is (actually i don't even know if it has one). Also, all the other computers on the network are windows, so I don't want to get anything from them.

---

### Post by FuturePilot on 2008-03-20
I've never used Firestarter. I've never seen the need to. The default iptables setup seems to be adequate.  I'm behind a router now anyways.

---

### Post by smooth3006 on 2008-03-20
im using firestarter in ubuntu, does this run silently in the background ? the reason i ask is i have it set to run at startup but the icon on the taskbar never shows up ?

---

### Post by FuturePilot on 2008-03-20
> **smooth3006 said:**
> im using firestarter in ubuntu, does this run silently in the background ? the reason i ask is i have it set to run at startup but the icon on the taskbar never shows up ?

Firestarter itself is not a firewall. It is simply a graphical front end configuration tool to iptables. Therefore it doesn't need to be running the background. Once you set all your configurations, you can close it since the settings were put into iptables which is always running.

---

### Post by drascus on 2008-03-20
I love firestarter. I have never really had an issue with it. The couple of times it really blocked things that were annoying was because I set it to do that. But the default settings never have caused an issue for me. It runs in the background and never asks me to do anything. I understand the argument about the router firewall and agree with it. Unless you have a laptop and travel with it quite often. Then you might want to configure your firewall unless of course you trust other peoples networks. Which I certainly do not.

---

### Post by CrowBgd on 2008-03-22
I have problems with Firestarter. Blocking P2P programs like torrent. When I stop Firestarter P2P is Ok por in my router is open.

---

### Post by gn2 on 2008-03-22
Unless there is  a specific need to change firewall settings, Firestarter is simply not required.

I have even heard tell that because it has root privileges while it runs, that leaving it running could be a security vulnerability.

---

### Post by bruce89 on 2008-03-22
Judging by the fact that there hasn't been a new upstream release of Firestarter since 2005, I think it's dead.

Hardy has a package called *ufw* (uncomplicated firewall).

---

### Post by samwyse on 2008-03-23
I haven't used it in years, but I find it strange that it doesn't import the default iptables settings on start.

---

