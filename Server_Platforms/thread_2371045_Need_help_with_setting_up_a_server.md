---
title: "Need help with setting up a server"
date: 2017-09-10
forum: Server Platforms
---

### Post by littlemonkey2 on 2017-09-10
I am new to linux and want to setup a monero pool via this guide: [https://github.com/Snipa22/nodejs-pool](https://github.com/Snipa22/nodejs-pool)
If anyone has any basic knowledge with linux and can help me get started I would be happy to tip you as I need it all setup asap!

---

### Post by littlemonkey2 on 2017-09-10
[COLOR=#000000]I am new to linux and want to setup a monero pool via this guide: [/COLOR][https://github.com/Snipa22/nodejs-pool](https://github.com/Snipa22/nodejs-pool)
[COLOR=#000000]If anyone has any basic knowledge with linux and can help me get started I would be happy to tip you as I need it all setup asap!
[/COLOR]

---

### Post by TheFu on 2017-09-10
This is not a "basic knowledge" question.

The github page offers an install service onto a plain Ubuntu 16.04 server for 7 XMR (about US$800 today).  For 4 XMR more, they will tune it - so about US$1200.  There are many downsides to this crypto-currency, but I'm not your father.

The learning curve required will be very steep, especially if coming from Windows without any Unix background.  When I was brand new - and I was a software developer for OS/2, Windows, Dos and MVS already - there would have been no way I could setup a server on any Unix system properly, with the correct security, and having it working, backed up, safe on the network.

If you want to do this, you'll need to get significant background knowledge before beginning.
[http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) - read that book - at least the first 9 chapters.  That will cover the basics.

BTW, I skimmed the requirements and they lost me when they asked for their installer to have sudo without a password.  I would never do that - NEVER.  Basically, these requirements provide a back door into your server(s) forever.  It wouldn't take much to drop a weekly back channel contact to anywhere they want.

I would be afraid to install that system.

BTW, this isn't the place to ask for someone else to perform the work for you. That is in a different sub-forum.

---

### Post by littlemonkey2 on 2017-09-10
Thank you so much for enlightening me, I never realized what I was actually messing with. I am an entrepreneur that likes trying lots of different ways to make successful investments whether they're short term or long term (like this one), I was aware of the risk as monero pools are no where near a guaranteed success (on the contrary the biggest percent of them end up in a loss). Now that you mention these numbers, I don't think I want to make such a big investment on a field I have no knowledge over, I was just planning on using a server I had that costs about 30 bucks a month and see what happens, I guess I will have to follow a simpler guide like this one: [https://github.com/zone117x/node-cryptonote-pool](https://github.com/zone117x/node-cryptonote-pool)

Again, thank you!

---

### Post by TheFu on 2017-09-10
I would stay away from node.js.  The cool kids love it, but many of them are extremely new and don't really understand Unix security.  Of course, there are multiple, different opinions.

$30/month seem high for a VPS these days.  Plus for crypto mining, you'd be better off building a new Ryzen box for $500, putting it in your basement and leaving it run 24/7.  Using shared resources like a VPS aren't usually a good method for mining.  I did read that this currency is designed to need a full CPU for mining, not an ASIC like BC.

I earn my living with more common investments and don't even dabble in crypto currencies.  If your investments gain 15%/year, then in 5 years, you've doubled your money.  Do that over a working lifetime and you can get to $5M - most of it in the last 5 yrs.  Just sayin'.
 This year, the NASDAQ is up almost 20%.  With those rates of return, I just don't see why anyone would risk investment money in any of these schemes.  Sure, for some play money - like I'd drop in a weekend in Vegas - sure, but that isn't investing. It is gambling or play money.

---

### Post by littlemonkey2 on 2017-09-10
Its a dedicated server with a quite strong CPU and 8 cores, I got it on a special offer from OVH so I thought why not. I'm a miner myself and I have around 22KH/sec mining Monero so I decided to just put couple bucks aside and get a pool running myself and see how it goes (I really love trying out new stuff in life just for the experience).

All the guides I find happen to have node.js, what would you recommend instead? I don't want to make something that risks being compromised by any means! From what I've been told OVH should cover me in terms of DDoS but security would be quite important as I have no idea what I'm doing which isn't really the best.

---

### Post by wildmanne39 on 2017-09-10
*Thread moved to **Server Platforms**.*

---

### Post by ian-weisser on 2017-09-10
The setup instructions seem reasonably clear.
However, this is clearly not a project for beginners - it requires *understanding* of various Linux  concepts.
The developers have not made installation as easy as they could have.

Have you a specific problem or question?

---

### Post by TheFu on 2017-09-10
> **littlemonkey2 said:**
> Its a dedicated server with a quite strong CPU and 8 cores, I got it on a special offer from OVH so I thought why not. I'm a miner myself and I have around 22KH/sec mining Monero so I decided to just put couple bucks aside and get a pool running myself and see how it goes (I really love trying out new stuff in life just for the experience).

All the guides I find happen to have node.js, what would you recommend instead? I don't want to make something that risks being compromised by any means! From what I've been told OVH should cover me in terms of DDoS but security would be quite important as I have no idea what I'm doing which isn't really the best.

This is my opinion.

If you don't want any method of being compromised, then don't run this on
* someone else's computer
* using someone else's hard disks
* on someone else's network
* connected to the internet
* that anyone can connect to either from the internet or on the private LAN at the hosting provider or from the storage LAN there.

Someone new to Unix-like systems really isn't equipped to install node.js stuff in a secure way. Actually, a plain web server would be a challenge for a beginner to install in a secure way, IMHO.  Security isn't a checkbox, "yes."  It is a constant process that forever changes based on the software used, attack vectors seen, and constant monitoring is required.  Right now over 1 milleeeeeeeon wordpress websites are hacked. Some are being run by professionals and others are being run by someone who followed some guide they found on the internet.  

Really, I'd suggest that you run a bonehead static website for 6 months first, then do something dynamic for a year (some sort of webapp) and learn a little about network security, OS security, web-server security, web-app security and probably VPNs, since you'll likely want to connect to this thing over a VPN only.  You'll want to know enough about the OS to absolutely know that only the VPN connection can be used for connectivity.  At least I would, before having even $100 in crypto-currency on the box.  Easy targets have their crypto-coins stolen all-the-time.

Others will have different opinions, but it isn't their money at risk.  Regardless, it would be good to have some of those opinions.

---

### Post by vasa1 on 2017-09-10
As a basic courtesy, please don't open more than one thread on what is essentially the same subject. It wastes the time of people who are volunteers here.

You already have [https://ubuntuforums.org/showthread.php?t=2371053](https://ubuntuforums.org/showthread.php?t=2371053).

---

### Post by QIII on 2017-09-10
Threads merged.

---

### Post by littlemonkey2 on 2017-09-11
> **ian-weisser said:**
> The setup instructions seem reasonably clear.
However, this is clearly not a project for beginners - it requires *understanding* of various Linux  concepts.
The developers have not made installation as easy as they could have.

Have you a specific problem or question?

Sorry for the late reply, I am indeed a beginner so I went and read some beginner and intermediate guides on how to use Linux, I have already learnt a lot in a few hours but I've barely scraped the surface. I started following this guide: [https://github.com/zone117x/node-cryptonote-pool](https://github.com/zone117x/node-cryptonote-pool) as it felt easier to understand and follow. Right now I just found out about AES256 so I'm looking into firewalls for my ports etc.

---

### Post by littlemonkey2 on 2017-09-11
> **TheFu said:**
> This is my opinion.

If you don't want any method of being compromised, then don't run this on
* someone else's computer
* using someone else's hard disks
* on someone else's network
* connected to the internet
* that anyone can connect to either from the internet or on the private LAN at the hosting provider or from the storage LAN there.

Someone new to Unix-like systems really isn't equipped to install node.js stuff in a secure way. Actually, a plain web server would be a challenge for a beginner to install in a secure way, IMHO.  Security isn't a checkbox, "yes."  It is a constant process that forever changes based on the software used, attack vectors seen, and constant monitoring is required.  Right now over 1 milleeeeeeeon wordpress websites are hacked. Some are being run by professionals and others are being run by someone who followed some guide they found on the internet.  

Really, I'd suggest that you run a bonehead static website for 6 months first, then do something dynamic for a year (some sort of webapp) and learn a little about network security, OS security, web-server security, web-app security and probably VPNs, since you'll likely want to connect to this thing over a VPN only.  You'll want to know enough about the OS to absolutely know that only the VPN connection can be used for connectivity.  At least I would, before having even $100 in crypto-currency on the box.  Easy targets have their crypto-coins stolen all-the-time.

Others will have different opinions, but it isn't their money at risk.  Regardless, it would be good to have some of those opinions.

I will only be running this on my PC using my own network etc., I presume I don't need to connect via a VPN since the project is not ready and released to the public yet. Would you recommend any links/examples in securing node.js?

---

### Post by littlemonkey2 on 2017-09-11
> **vasa1 said:**
> As a basic courtesy, please don't open more than one thread on what is essentially the same subject. It wastes the time of people who are volunteers here.

You already have [https://ubuntuforums.org/showthread.php?t=2371053](https://ubuntuforums.org/showthread.php?t=2371053).

My apologies, I wasn't aware of which discussion to post it in so I just opened 2 threads, it's been merged and placed in the correct area now thanks to the staff though so thanks!

---

### Post by TheFu on 2017-09-11
> **littlemonkey2 said:**
> I will only be running this on my PC using my own network etc., I presume I don't need to connect via a VPN since the project is not ready and released to the public yet. Would you recommend any links/examples in securing node.js?

Start here:  [https://www.amazon.com/Real-World-Linux-Security-2nd/dp/0130464562](https://www.amazon.com/Real-World-Linux-Security-2nd/dp/0130464562) but it isn't a beginning level reference.

If someone can get to the port from another network, it is already released.  An announcement means nothing.  These days it is possible to scan the entire ipv4 internet in 5 minutes.  There are services looking for new things doing this constantly.

[https://www.wired.com/story/why-its-so-easy-to-hack-cryptocurrency-startup-fundraisers](https://www.wired.com/story/why-its-so-easy-to-hack-cryptocurrency-startup-fundraisers)

---

