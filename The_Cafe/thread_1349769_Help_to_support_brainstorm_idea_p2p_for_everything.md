---
title: "Help to support brainstorm idea: p2p for everything (even system update)"
date: 2009-12-08
forum: The Cafe
---

### Post by Ylon on 2009-12-08
I did try to set up [this idea](http://brainstorm.ubuntu.com/idea/22756/) in Ubuntu's Brainstorm portal.

But I was unlucky and/or unable to explain: so now this idea results as "already implemented".



Actually, Ubuntu support torrents by default with [transmission](http://www.transmissionbt.com/). So I thought: why don't move ahead and try a little more.

I'd remeber a nice project I was following by interest some time ago: [MLDonkey](http://en.wikipedia.org/wiki/MLDonkey)


This [daemon like](http://en.wikipedia.org/wiki/Daemon_(computer_software)) software support torrent, ed2k and some other p2p protocol (also http).. other kind of supports can be added by plugins.

There's no default gui for MLDonkey: this mean that it... can be graphically controlled in many way: front-end, web browser, telnet and... [by terminal](http://mldonkey.sourceforge.net/File_completed_cmd) (yes, you can download torrent file in the same way wget does)


My hypothesis was to use it via panel-applet, more likely the way networkmanager do (just think: instead see the wifi network, you see your download status). Plus it also would allow download updates (you need just some commandline script).. and in future, who know! even software!

Everything in p2p, and everything in _ANY_ kind of p2p: from the well know torrent, the "mature" ed2k to the who-know-what-will-be in future!









But something goes wrong in the way I'd explain all this: so, need some help out from the community to explain in proper English grammar, will you all?

I am there for more **trying** explication, anyway. :KS

---

### Post by the yawner on 2009-12-08
Back in Intrepid I've read about a guide to use torrent as a means to download updates. [http://torrentfreak.com/use-bittorrent-to-upgrade-to-ubuntu-intrepid-ibex-081029/]("http://torrentfreak.com/use-bittorrent-to-upgrade-to-ubuntu-intrepid-ibex-081029/")
It uses a script(?) called apt-p2p that can be integrated with apt-get. Never tried it though.

---

### Post by user1397 on 2009-12-08
While I and many others would probably support this idea, it is true that bittorrent can be a bit unreliable for some people.  If only few people are seeding their system updates for example, updates might be overall slower than the method used atm.

Maybe if they implemented a way that you *had* to be seeding them at all times would make this work...but isn't that taking some freedom away?

I don't know, I'm not closing the argument down, I'm just putting up a possible argument.

---

### Post by Xbehave on 2009-12-08
Many people can't seed so this will cause problems.
As dl bandwidth is rarely a problem for ubuntu+mirrors, this has limit usefulness, in fact the overhead of using bt may out-weight the benefits (especially for small downloads).
So while i like the idea i don't think it should be default.

> If only few people are seeding their system updates for example, updates might be overall slower than the method used atm the ubuntu servers could still seed, so it's only overhead vs advantage that matters, you won't get stuck with really slow downloads because they are under seeded.

---

### Post by jollysnowman on 2009-12-08
> **Xbehave said:**
> Many people can't seed so this will cause problems.
As dl bandwidth is rarely a problem for ubuntu+mirrors, this has limit usefulness, in fact the overhead of using bt may out-weight the benefits (especially for small downloads).
So while i like the idea i don't think it should be default.

 the ubuntu servers could still seed, so it's only overhead vs advantage that matters, you won't get stuck with really slow downloads because they are under seeded.

If the ubuntu servers seed, then there's no need for using the current download-by-mirror method, correct?

---

### Post by Xbehave on 2009-12-08
> **jollysnowman said:**
> If the ubuntu servers seed, then there's no need for using the current download-by-mirror method, correct?
True, but that would require the mirrors to seed too, if my ISP offer me a really fast connection over http but don't over a fast bt server (setting up a http server is easier/cheaper) or even throttle bt, then it would still be faster to use my mirror.

---

### Post by starcannon on 2009-12-08
Can this delivery method be made safe and secure? I'm not a torrent guru, just off the top of my head I considered the possibility of a rogue seeder to hose up the whole show, or even infect the seed.

---

### Post by Xbehave on 2009-12-09
> **starcannon said:**
> Can this delivery method be made safe and secure? I'm not a torrent guru, just off the top of my head I considered the possibility of a rogue seeder to hose up the whole show, or even infect the seed.
Infection is impossible (to break bittorrent you need to crack SHA1 keys, which isn't practical, and to install it on your system they need to break GPG keys which is next to impossible).
They could try and slow a torrent down by pushing bad data but they could do that to normal torrent and:
1) it doesn't happen
2) it would only affect you if your unlucky enough to connect to them (if there are enough seeds (especially fast seeds such as ubuntu servers), this will be rare
3) After a few bad packets from one, the client can add them to a blacklist and look elsewhere.

So the Damage they could do would be minimal and can only increased the overhead slightly, it can't bring anything to a grinding halt.

---

### Post by Ylon on 2009-12-09
> **the yawner said:**
> Back in Intrepid I've read about a guide to use torrent as a means to download updates. [http://torrentfreak.com/use-bittorrent-to-upgrade-to-ubuntu-intrepid-ibex-081029/]("http://torrentfreak.com/use-bittorrent-to-upgrade-to-ubuntu-intrepid-ibex-081029/")
It uses a script(?) called apt-p2p that can be integrated with apt-get. Never tried it though.

I am more than sure that this ideas isn't 100% original: never eard about Itrepid torrent update, but by sure many are working on this idea:


Design a new way to deal with p2p (which IS NOT all about torrent: ISOs and software release a part, it's main use is for illicit download): p2p is another one challenge for the future. I want just Ubuntu ahead in this challenge.

> **ubuntuman001 said:**
> While I and many others would probably support this idea, it is true that bittorrent can be a bit unreliable for some people.

This is mainly the concept I'd see in MLDonkey: it's support any actual (and possible future) p2p technology.


Big companies pressure ISP for blocking p2p protocols?

Update Ubuntu System: "fix torrent" or another plugin download (new protocol: next updates from torrent to kadmelia)

> **Xbehave said:**
> Many people can't seed so this will cause problems.
As dl bandwidth is rarely a problem for ubuntu+mirrors, this has limit usefulness, in fact the overhead of using bt may out-weight the benefits (especially for small downloads).
Let's make an example.... Last Ubuntu Release:
tons of user browsing to find the best server (http/ftp), some are lucky... some other had push on too popular server == mess (some dowload fast, someone download slow).

But the system integrate p2p (wich involve: torrent, ed2k, kadmalia), the ISO is parted in 7 file (100MiB the piece).
Torrent is slow (1 file each 2 hours), but ed2k is fast (2 file each hour) and http remain superfast (3 file each hour).

You will _always_ take the file in the fastest way possible: you *merged* three different technologies... it will like segment download (as Windows's Getright does)... just way more powerful).
Can you cheat on three different technologies... at the same time? I don't think so.

> **starcannon said:**
> Can this delivery method be made safe and secure? I'm not a torrent guru, just off the top of my head I considered the possibility of a rogue seeder to hose up the whole show, or even infect the seed.
Safe, no. Indeed this could be even more dangerous... since is a, relatively, new technology.
But is more unsafe than http protocol?
Safety is a relative concept, it vary on many circumstance:
- ability of the attacker
- the "human client" be vigilant
- willing of the community to fix and keep working on a idea.
...and so go on










/////////////

Please, remember: the idea is not all about system update or illicit download.
P2p technology IS COMING in many ways some, (like phone/video call) are already fully effective, while other are... just ideas.


Put p2p in the os: and (other than open to new danger) you will make evolve the OS in future.

Evolution is all about danger.

---

### Post by jollysnowman on 2009-12-09
> **Xbehave said:**
> True, but that would require the mirrors to seed too, if my ISP offer me a really fast connection over http but don't over a fast bt server (setting up a http server is easier/cheaper) or even throttle bt, then it would still be faster to use my mirror.

Ah, didn't know about that. That's a good point. ISPs are probably unwilling to really acknowledge torrents as a non-piracy entity (I'm sure there are other reasons why it's easier to set up an HTTP server; I just don't know them)

---

### Post by Xbehave on 2009-12-09
> Torrent is slow (1 file each 2 hours), but ed2k is fast (2 file each hour) and http remain superfast (3 file each hour).
Perhaps for illegal files, but for legal downloads with webseeding, torrent is the fastest way to get anything big. However you typical system upgrade is only a few MB so it may not be worth the overhead and be easier to just pull the files from the nearest mirror.

For releases Ubuntu already offer the ISOs over torrent, but the default method has to be http because:
1) many users don't know how to download over p2p.
2) many users can't download over p2p because their ISP throttles them if they do.
3) You can't guarantee that the users have a p2p client installed as they could be coming from windows/mac/etc.

---

### Post by Ylon on 2009-12-09
> **Xbehave said:**
> Perhaps for illegal files, but for legal downloads with webseeding, torrent is the fastest way to get anything big.

Not everyone that want to share (legally) their stuff can relay on webserver bandwidth: the real propose of the p2p is that "share" is the real engine for "diffusion".

Anyway, this idea is not about close torrent protocol in favor in something else: but add more (actual) protocol and let possible add/modify easily in future (also know as: evolve).


> **Xbehave said:**
> However you typical system upgrade is only a few MB so it may not be worth the overhead and be easier to just pull the files from the nearest mirror.
"Update technology" don't involve just security fixes of some KB anymore, but also new version of software, firefox2/3... OpenOffice 3,4 whatever.
There's a large traffic made all relay on webfarms mirrors viability. But this isn't granted... What's obviously today will not in future.

Webserver mirror can be filter, closed, partially updated, bad syncronized, censored (avoid to run too much in politic) for nondemocratic governments desires and, more simply, you hadn't anyone (or very little) close to you.

Same thing can happen for p2p networks.. but _both_ at same time? Add a choice that slightly (well, not really.. indeed just from now that will be already of GREAT...) help you today, it will be essential tomorrow.



> **Xbehave said:**
> For releases Ubuntu already offer the ISOs over torrent, but the default method has to be http because:
1) many users don't know how to download over p2p.
[updated reference](http://www.ipoque.com/resources/internet-studies/internet-study-2008_2009)

> **Xbehave said:**
> 2) many users can't download over p2p because their ISP throttles them if they do.
So... leave this possibility to anyone to have *equal rights*?

> **Xbehave said:**
> 3) You can't guarantee that the users have a p2p client installed as they could be coming from windows/mac/etc.
The time Windows and Mac will take upon this technology.. you will lost _another_ chance to make BIG difference from Ubuntu/Linux/Gnu community from the big guys of the economy ;)

---

### Post by starcannon on 2009-12-10
> **Xbehave said:**
> Infection is impossible (to break bittorrent you need to crack SHA1 keys, which isn't practical, and to install it on your system they need to break GPG keys which is next to impossible).
They could try and slow a torrent down by pushing bad data but they could do that to normal torrent and:
1) it doesn't happen
2) it would only affect you if your unlucky enough to connect to them (if there are enough seeds (especially fast seeds such as ubuntu servers), this will be rare
3) After a few bad packets from one, the client can add them to a blacklist and look elsewhere.

So the Damage they could do would be minimal and can only increased the overhead slightly, it can't bring anything to a grinding halt.

Excellent, thanks for the reply.
So basically, so long as people use an official torrent, safety and security are intact.
Thanks again.

---

