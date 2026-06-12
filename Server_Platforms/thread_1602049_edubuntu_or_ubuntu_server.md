---
title: "edubuntu or ubuntu server?"
date: 2010-10-20
forum: Server Platforms
---

### Post by wideyes on 2010-10-20
Hi folks. I am looking to set up a thin client server for my business. It will be small (~15 workstations) and the requirements are very modest (mostly web browsing). Looking at edubuntu, I see it comes setup and preconfigured with some features I was expecting to use, like ltsp, dhcp, menu editors/thin client management gui tools, gnome nanny, etc. In general its feature set seems very useful. However, I would like this server to have maximum longevity, since it will probably remain unchanged for the forseeable future once it's properly configured. I was originally considering installing ubuntu server 10.04 because of the long-term support promise of five years. I have had some trouble locating more documentation relating to edubuntu's integration with ubuntu updates and its support into the future on any given version. Does anybody have any input that could inform me to make the right decision? Thanks in advance!

---

### Post by HermanAB on 2010-10-21
Howdy,

For an Edubuntu setup, I would definitely disable updates once the system is installed, tested and working.  The risk of an update breaking your whole organization all at the same time, is just too great and far outweighs the risk due to not doing updates.  Linux is not Windows.  Linux is extremely stable if you just leave it alone.

I never update my servers automatically.  I rather lock them down best I can and rebuild them from scratch every few years when they suffer a hardware failure.

---

### Post by Nizumzen on 2010-10-21
> **HermanAB said:**
> Howdy,

For an Edubuntu setup, I would definitely disable updates once the system is installed, tested and working.  The risk of an update breaking your whole organization all at the same time, is just too great and far outweighs the risk due to not doing updates.  Linux is not Windows.  Linux is extremely stable if you just leave it alone.

I never update my servers automatically.  I rather lock them down best I can and rebuild them from scratch every few years when they suffer a hardware failure.

That has to be the worst advice I have ever heard. You do realise that your network is probably full of huge security holes don't you? Including the last well advertised kernel security announcement.

---

### Post by wideyes on 2010-10-21
I can see the argument for 'locking down' a server, but I do not wish to go that route. I'm doing this upgrade to replace a similar server based on Debian Sarge that is a total dinosaur at this point. My whole goal with this upgrade is to have a new server that will be A). stable, and B). supported in the longterm. I'm just wondering if I'll have better and longer overall support going with ubuntu server.

---

### Post by James78 on 2010-10-21
Ubuntu Server has all the required tools you'll need, regarding dhcp, BIND, etc. As for the GUI, Ubuntu Server comes without one, but you can install one later if you wish by doing something like "sudo apt-get install ubuntu-desktop", although, for a server you'll probably want a lighter GUI if you do use one.

.. Workstations? People are going to be using these servers mostly? Why not use the main Ubuntu distribution which already comes with a desktop and everything. You can still use Ubuntu Desktop 10.04 LTS if you wish too. Depends on what you want and how the computers are being used though.

> **HermanAB said:**
> Howdy,

For an Edubuntu setup, I would definitely disable updates once the system is installed, tested and working.  The risk of an update breaking your whole organization all at the same time, is just too great and far outweighs the risk due to not doing updates.  Linux is not Windows.  Linux is extremely stable if you just leave it alone.

I never update my servers automatically.  I rather lock them down best I can and rebuild them from scratch every few years when they suffer a hardware failure.
That's extremely bad advice. There's automated zombie computer botnet networks everywhere scanning and waiting to find your computer, to exploit the latest vulnerability in an old application, and script kiddies. Locking them down "the best you can" isn't enough. Only way to stay protected is to cut it off from the internet and network.. Even then others can still get it. The virus, malware, and hacking community is bigger than you think. Of course, the best way to prevent those problems is simply stay updated, and THEN do the best you can to secure it. I update all the time, and my server's configuration is fine. When updating, apt will tell you if it's going to replace your config, and will give you the option to not replace it, and see the changes.

---

### Post by bmathis on 2010-10-21
Edubuntu should have the same LTS as the main Ubuntu distro. What I have done is use 10.04 LTS Desktop. You can use the Alternative ISO or after installing all the apps you need and making any changes that you want, then its as simple as running ```
sudo tasksel
```selecting Edubuntu Server, and following the [ltsp documentation]("https://help.ubuntu.com/community/UbuntuLTSP") provided by Ubuntu.

> Howdy,

For an Edubuntu setup, I would definitely disable updates once the system is installed, tested and working. The risk of an update breaking your whole organization all at the same time, is just too great and far outweighs the risk due to not doing updates. Linux is not Windows. Linux is extremely stable if you just leave it alone.

I never update my servers automatically. I rather lock them down best I can and rebuild them from scratch every few years when they suffer a hardware failure. 

@HermanAB - this has got to be the poorest advice I have ever seen you provide on these forums (besides recommending Citadel to everyone). 

Whatever you do Wideyes, ***_please do not listen_*** to HermanAB on this one. Updates are essential to maintaining a proper, secure system. If you are concerned about breakage, the best thing to do is to have a live or virtual test system to verify updates. If an update breaks your test system, then you for-go that particular updated file/program, report a bug, and wait for the next stable update to test. Trust and verify!

---

### Post by James78 on 2010-10-21
> **bmathis said:**
> @HermanAB - this has got to be the poorest advice I have ever seen you provide on these forums (besides recommending Citadel to everyone).
I gotta agree with the Citadel part.

---

### Post by wideyes on 2010-10-25
Thanks for the responses, fellows! Sorry it took me a few days to get back. Before I heard any more responses after my previous post, I went ahead and tried an Edubuntu 10.04 install. In addition to having lots of bloat, it didn't even install an LTSP environment by default! Tsk. Maybe my fault though for not doing the install properly? While at first I was excited about the prospect of using it, I'm starting to think I would be better served with either the server or desktop editions and just working up to what I need. I appreciate the input - thanks all!

---

### Post by wideyes on 2010-10-25
Just occurred to me, bmathis: if I use tasksel and choose Edubuntu Server like you suggested, what can I expect to be installed as a result? Will it want to give me all of the classroom applications? It is an intriguing option.

---

