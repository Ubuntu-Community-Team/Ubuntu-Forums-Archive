---
title: "Hardware Firewall vs Software Firewalls"
date: 2014-02-06
forum: The Cafe
---

### Post by linuxyogi on 2014-02-06
Hi,

_Option 1_

Configure the adsl router and connect it directly to the switch. (So there's one firewall protecting the network and that's the router's firewall)

_Option 2_

Configure the adsl router and connect it to a secondary software firewall like untangle or pfsense. (Therefore 2 firewalls are active)

_Option 3_

Configure the router in bridged mode and dial the dsl connection from the firewall's interface. ( In this case the router is used as a modem and the only firewall is the software firewall)

Which one do you think is the most secure setup ? Or are there other ways also ?

---

### Post by Dave_L on 2014-02-06
I don't fully understand the three configurations. But I think that having an external firewall, such as the one in the router, is important because it's active all the time, even during boots, installs, etc. I like having a software firewall in addition, to provide "fine tuning".

---

### Post by dbass81 on 2014-02-06
Why so much security in the first place?  Your router's firewall should be more than enough.  What are you trying to keep the Sochi hackers out?

---

### Post by TheFu on 2014-02-06
Security needs to be layered.

There really aren't any "hardware firewalls" anymore. Most cheapo routers run Linux and use iptables as the firewall.
pfSense is a better firewall than any of the Linux options. It is smarter about tracking connections and because it is based of BSD, it tends to slow down, not fail, under heavy loads.  That is not to say that iptables is any slouch either, just that mixing OSes is good from a security perspective.

Without a diagram of your total network setup, I can't say which is *better*.  **Better** is highly subjective too, so only you can decide.  I think pfSense is a *better* firewall, but I also run firewalls on every internal device that I can, since we have a few Windows machines on the LAN and there are ways to make them be nasty.  All my portable devices also run a firewall with all inbound ports blocked explicitly.  I've deployed pfSense for customers after discussing the options with many members of the local "defcon" group.  A few suggested linux-based firewalls, but the about 80% of the most trusted guys recommended pfsense. That is what the universities around here used as well, so it is extremely capable; ready for prime-time use in hostile environments.

If the ADSL router is controlled by the telecom provider, I wouldn't trust it.  I have a cable modem owned by the cable company and still run my own router inside to block their stuff.  Before, when I owned the cable modem, I learned that the cable company had full access to the configuration and could open/close any ports they wanted even without the admin password.  That is the nature of CPE.  BTW, I used to work for a very large, 3 letter, DSL provider in the USA and deployed a DSL router management system there. Definitely do not trust them with anything related to your security is my advice. Sometimes very large mistakes happen (by accident) and it would be better to have another layer, completely under your control to mitigate those mistakes.

---

### Post by dbass81 on 2014-02-06
> **TheFu said:**
> Security needs to be layered.

There really aren't any "hardware firewalls" anymore. Most cheapo routers run Linux and use iptables as the firewall.
pfSense is a better firewall than any of the Linux options. It is smarter about tracking connections and because it is based of BSD, it tends to slow down, not fail, under heavy loads.


You are right on the money, my friend. I haven't tried pfSense or used BSD in years (my last foray was running OpenBSD as a firewall/router before wireless routers were <$100), but I am currently running Debian behind a wireless router acting as a Squid3 web caching server, among other things.  On my Windows 7 PC, whenever I download multiple Games from Steam (I have proxies enabled in Windows), it crashes my Debian/Squid machine.  Not only Squid, but the whole machine.  No pings, no SSH, nothing.  Reboot fixes it, but the Debian server runs stable if I don't download with Steam or use proxy under Windows.

---

### Post by TheFu on 2014-02-06
> **dbass81 said:**
> You are right on the money, my friend. I haven't tried pfSense or used BSD in years (my last foray was running OpenBSD as a firewall/router before wireless routers were <$100), but I am currently running Debian behind a wireless router acting as a Squid3 web caching server, among other things.  On my Windows 7 PC, whenever I download multiple Games from Steam (I have proxies enabled in Windows), it crashes my Debian/Squid machine.  Not only Squid, but the whole machine.  No pings, no SSH, nothing.  Reboot fixes it, but the Debian server runs stable if I don't download with Steam or use proxy under Windows.

@dbass81 - crashing when using squid shouldn't have anything to do with the firewall and certainly shouldn't happen with reputable downloads. You have a different issue to be solved.  Neither iptables nor squid should crash any Linux system under loads that a DSL or residential cable modem can achieve.

---

### Post by dbass81 on 2014-02-06
> **TheFu said:**
> @dbass81 - crashing when using squid shouldn't have anything to do with the firewall and certainly shouldn't happen with reputable downloads. You have a different issue to be solved.  Neither iptables nor squid should crash any Linux system under loads that a DSL or residential cable modem can achieve.

I also thought that, but it only happens when I download using Steam and I have proxies enabled.  I also use DNS caching with pdnsd.  My pdnsd.conf uses ping as query so its probably being pinged to death by my Steam downloads.  LOL.

---

### Post by gordintoronto on 2014-02-06
+1 for modem ==> pfsense ==> local network. (pfsense does everything a router does, as well as acting as the firewall.)

---

