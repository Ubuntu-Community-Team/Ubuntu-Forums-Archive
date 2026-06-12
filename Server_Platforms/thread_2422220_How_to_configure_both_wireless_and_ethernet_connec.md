---
title: "How to configure both wireless and ethernet connections"
date: 2019-07-03
forum: Server Platforms
---

### Post by dendron2000 on 2019-07-03
Hi,

First of all, I'm a complete noob regarding servers. Last few days I've been trying to setup both ethernet and wireless connections (as a fallback) on my home Ubuntu Server installation but haven't succeeded. If anyone could help me I'd really appreciate that.

The network configuration seems to be overly complicated these days. There are several competing methods to do that (netplan, networkd, NetworkManager, custom wpa_supplicant service, ifupdown) but none of them seem to do the job.

The netplan service using a networkd simply refuses to work with WPA2 protected wireless network. I followed the example andthe config looked simple, but it just refused to work. When started with "--debug generate" it does say that it has generated a config for wpa_supplicant in the /run directory, but it appears it doesn't do anything. Only a config for the networkd is present, but not for wpa_supplicant. Not sure if it is a bug or what. And honestly, this meta YAML generator for other meta subsytems (like networkd) feels like its completely superflous and hard to debug. There doesn't seem to be a proper log file

networkd seems to be overly complicated, too. And I've heard that it doesn't properly support wireless networks.

NetworkManager does not seem like an option for the server.

ifupdown refuses to work with wireless interface at all. There are nice guides to do what I want using /etc/network/interfaces (fore example [this one]("https://linuxconfig.org/setup-wireless-interface-with-wpa-and-wpa2-on-ubuntu")) which looks really nice and simple, but the only downside of it is that it doesn't work at all. At least not with wireless connections.

The only way I could get a wireless connection is by writing a custom wpa_supplicant service by following some other guide from the internet. This does work reliably. But then I have to pair it up with the ethernet connection and I don't really know how to do that when the wireless one is being setup by a custom service like that.

I'm really desperate. All those network managing systems seem to depend on each other and conflict with each other at the same time. None of them feel like a finished and easy to use solution. netplan looked like a meta tool which tried to bind them all together but instead it became just another unfinished and buggy tool itself. I don't even understand how to debug all of this mess because there are so many points of connections between those systems (netplan->networkd->wpa_supplicant->???) and each of them has its own unique way to get logs.

Now I don't mind using netplan or ifupdown, just whatever works. I'm really not happy about writing my own custom services or scripts to manage the network, there has to be a proper solution.

---

### Post by SeijiSensei on 2019-07-03
Servers should use wired connections. Don't bother with wireless.

There's no performance gain to be had from trying to use both interfaces on a single network unless you use the advanced technique called "bonding." For now, just disable the wireless adapter.

---

### Post by dendron2000 on 2019-07-03
Bonding is what I evenually aim to achieve. And it doesn't seem to be advanced. In fact setting up a wireless connection in Linux is much more unnecesseraly "advanced" than anything else. As I've mentioned, I want to use wireless connection as a fallback. There are numerous guides how to do that but none of them seem to work. It feels like all those netplan and networkd systems are getting in my way more than they are helping and it's really annoying.

---

### Post by houstonbofh on 2019-07-04
Bonding wired and wireless will not work.  Trust me.  And wifi on a non-gui system is also a headache.  If you really want it, go buy an AP that will do client mode bridging and use that.

But if you really want to try it to learn, remove netplan and go back to the old net-tools and you have a much better chance.

---

