---
title: "My master adblock plans, but need halp.."
date: 2017-03-08
forum: Server Platforms
---

### Post by flaZh on 2017-03-08
Hi, I've been thinking about this for awhile. And I've tinkered with it,but I need help. I hate ads, they don't affect me and often I can't even remember what it was a commercial for. They just annoy me. So I run adblock when watching twitch or youtube on my pc..But there's no solution for this on my tablets and phones.

Which leads to me wanting to setup some kind of software(squid?) and then set up my router to connect through a proxy or something so that I can skip using adblock on pc(saves some system resources), it will enforce phones and tablets to block ads and if I can connect to it via 4g I'll never have ads again,ever! And adblock has the option to subscribe to lists that will have urls that'll update automatically.

I installed squid, tried to configure it ,didn't get it to work. Didn't got proxy to work but not sure that's the correct solution or a tunnel/vpn is.

So any thoughts, did you set it up and got it working? What's your configs for squid?

---

### Post by TheFu on 2017-03-08
At home, setup [pi-hole.]("https://pi-hole.net/")
When you are outside the house, use something like this: [http://blog.jdpfu.com/pages/hosts-for-security](http://blog.jdpfu.com/pages/hosts-for-security) - it requires a rooted phone.

If you want to use the pi-hole service when outside the network, you'll need a full VPN that terminates inside your home network. Many people find that a simple SOCKS proxy is sufficient, as ssh can provide, but getting this working on non-computing devices like tablets and smartphones is non-trivial. **OpenVPN** is easy to get working on tablets and phones, but harder to configure on the server side. The server config is harder because there are hundreds of options and no 2 network admins configure theirs the same.

Running a squid proxy that is open in the interent is asking for problems. Plus, if you use pi-hole, it will handle all protocols, not just http for ads.  My current pi-hole based block list is 130K and was updated about a month ago.  I do not run pi-hole, since my router (pfsense) already handles that sort of stuff nicely.  However, on my netbook, I have been using the very long /etc/hosts file as the link suggests for 8+ yrs.

---

### Post by DuckHook on 2017-03-08
*Thread moved to **Server Platforms** as the more appropriate forum.*

---

### Post by flaZh on 2017-03-09
> **TheFu said:**
> At home, setup [pi-hole.]("https://pi-hole.net/")
When you are outside the house, use something like this: [http://blog.jdpfu.com/pages/hosts-for-security](http://blog.jdpfu.com/pages/hosts-for-security) - it requires a rooted phone.

If you want to use the pi-hole service when outside the network, you'll need a full VPN that terminates inside your home network. Many people find that a simple SOCKS proxy is sufficient, as ssh can provide, but getting this working on non-computing devices like tablets and smartphones is non-trivial. **OpenVPN** is easy to get working on tablets and phones, but harder to configure on the server side. The server config is harder because there are hundreds of options and no 2 network admins configure theirs the same.

Running a squid proxy that is open in the interent is asking for problems. Plus, if you use pi-hole, it will handle all protocols, not just http for ads.  My current pi-hole based block list is 130K and was updated about a month ago.  I do not run pi-hole, since my router (pfsense) already handles that sort of stuff nicely.  However, on my netbook, I have been using the very long /etc/hosts file as the link suggests for 8+ yrs.

Oh, thanks. I'll look into this. I actually have two Rasberry Pi's I haven't been using for anything, so if that's required I have it already(nope, doesn't seem needed at all). 
About the rooted phone I don't have this, so I would have to use VPN. My router is currently a DD-WRT so it has VPN options there, but not sure if I can do that when the ubuntu/pi is behind that?

So now pi-hole is installed, I can just install OpenVPN, and set its settings to DNS of my pi-hole. 

OR can I set the DNS up in my router now to enforce the blockings?
(nope, this ^ did not work, I set both the local dns and the network dns1 to be the pi-hole DNS in the router, wait.. I might need to adjust settings or update lists in the pi-hole? I'm messing with it to try make it work)

Edit: Seems like the blacklist comes empty, how do I import 130k list you had into there? (I pasted in like 26k into the blacklist, that's not a good solution at all, it froze -.-) --Using the admin webUI. (also I found etc/pihole/adblock.default thing)

---

### Post by flaZh on 2017-03-09
Ultimate solution became this:
[https://alternate-dns.com/](https://alternate-dns.com/)

 ;)

---

### Post by TheFu on 2017-03-09
There are lots of different solutions.

pi-hole isn't required. You can use any DNS that you prefer, running on any system that you prefer - for the home network solution. A r-pi isn't required, but for a problem like this in a home environment, a r-pi is a fine solution.  I wrote a few scripts to merge the different block lists into my local /etc/hosts entries. You cannot just replace the existing hosts file, that will cause major issues to any networked system.** It must be merged.**  I do not use pi-hole myself. I use the block lists.

Be careful running dd-wrt (or openWRT or tomato). Many devices don't have current versions of that software available. Running out-of-date OS on your router is really bad for security. At this point, it is better to avoid using home routers at all if they can't run a constantly patched OS. Go with purpose built-hardware and either a constantly updated router distro (pfsense/smoothwall) or a stock OS that supports routing, like Linux, that is patched at least monthly, if not daily.  Ars has a nice article about building Linux routers. These days, it is smartest to avoid most commercial small-biz/home routers. Price doesn't seem to help with getting updates for the life of the hardware. IMHO .... I've run an Alix and APU2 setup with pfsense for years to avoid the dd-wrt dead-end problem my original HW had.  Basically, dd-wrt hadn't been updated in 4 yrs for my specific hardware and had at least 20 known security flaws.

Please be very careful in selecting a DNS provider. If they are not reputable, your entire security is gone.  DNS is the cornerstone of HTTPS security.IMHO

If this is solved, please mark the thread as SOLVED to help others seeking solutions or to help.

---

### Post by flaZh on 2017-03-09
> **TheFu said:**
> Please be very careful in selecting a DNS provider. If they are not reputable, your entire security is gone.  DNS is the cornerstone of HTTPS security.IMHO

I totally agree, I wanted my own system, but when I couldn't get it to work, and I tried a few different lists as well. I went with an easier solution, though it's more risky I take risks, no problem.

---

