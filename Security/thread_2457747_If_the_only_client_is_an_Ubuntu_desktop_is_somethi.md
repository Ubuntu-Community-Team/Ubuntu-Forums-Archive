---
title: "If the only client is an Ubuntu desktop is something like IPCop necessary ?"
date: 2021-02-08
forum: Security
---

### Post by linuxyogi on 2021-02-08
Hi,
I am planning to avail a fiber broadband connection. I dont want to use the ISP provided router coz I have no idea how secure it is & how well they offer timely firmware updates.
At the moment the only client is my desktop running Lubuntu. I watched on Youtube that in order to convert a fiber connection a MODEM is needed which converts fiber to RJ45.
My question is if I connect the RJ45 which comes out of the modem directly to my PC's LAN port will this cause any issues from a security angle ?

In future I am planning to buy an Amazon Fire TV stick. When I do that I will install IPCop on a dedicated PC and use a cheap router in ACCESS POINT mode.

For now the only client is my Lubuntu 20.04 box.

---

### Post by TheFu on 2021-02-09
> will this cause any issues from a security angle ?
YES!
Most people don't secure their desktops anywhere near enough to place them on the unfiltered internet. Even the ISPs busted router would be better than doing that.  For people in these forums with lots of experience, but little desire to run a router distro, the easy, relatively cheap, answer, is to get a Microtik or Ubiquiti router to perform the WAN firewall/routing work. Both those vendors have a long history (10+ yrs) of providing patches for their equipment.  If you want to blow more cash, Asus has been forced by the US-FTC to provide new firmware after a few high-profile failures. I think they are under a 20 yr mandate using best security practice techniques - but they charge $250+ for their equipment.  The others are around $75 for good enough routers.  For about $120, you can get a purpose built, PCEngines device and load any BSD or Linux routing distro you want.

Is ipcop distro maintained?  There was a time when they didn't have any updates for over 2 yrs I just read.
> The latest stable IPCop version is 2.1.9, released on 2019-02-23. 
I wouldn't touch that if you paid me.  There have been a number of remote exploits to the kernel since that time.

---

### Post by linuxyogi on 2021-02-09
**[COLOR=#000000][/COLOR]**[COLOR=#000000]> YES!
Most people don't secure their desktops anywhere near enough to place them on the unfiltered internet.
So you are saying that even Ubuntu with ufw enabled is still vulnerable ?

I am facing a slightly different problem. Two big ISPs in my country have started to introduce their high speed fiber connections at a reasonable price but there is one big problem. None of them allow customers to use their own router. Suppose I use the ISP provided router as the perimeter firewall & connect a [Smoothwall]("https://www.smoothwall.org/") box to one of the LAN port of my ISPs router will that make my network secure enough ?[/COLOR][URL="https://ubuntuforums.org/member.php?u=1037685"][B][COLOR=#000000]
[/COLOR][/B][/URL]

---

### Post by CelticWarrior on 2021-02-09
> [COLOR=#000000]None of them allow customers to use their own router.[/COLOR]
Are they using CG-NAT and/or provide landline phone service over the fiber?

---

### Post by linuxyogi on 2021-02-09
> **CelticWarrior said:**
> Are they using CG-NAT and/or provide landline phone service over the fiber?

I am going to try my best to explain.

_Standard procedure_

The fiber optic cable comes into the customer's home. Its then connected to the fiber port of a gpon modem which converts the signal & outputs it via a RJ45 port which then gets connected to a WiFi router. So in total 2 devices are involved the modem & the router.

_Jio Fiber/Airtel Fiber_

These 2 ISPs dont use a separate modem. Instead they use a "hybrid" device which works as both modem & router. I contacted both & they told me I have no other choice but to use their modem/router hybrid device.

---

### Post by SeijiSensei on 2021-02-09
Yes, if you connect a computer to the modem's Ethernet jack, you will be directly on the public Internet. I prefer to have a router between the Internet and my internal network, but it is possible to add a few iptables rules to a computer running Linux and turn it into a masquerading router. I've done it myself in the past, but nowadays I'd just buy a decent router like [https://www.newegg.com/tp-link-archer-a8/p/0E6-002W-006B7](https://www.newegg.com/tp-link-archer-a8/p/0E6-002W-006B7).

I bought my own modem, too. I'm done paying monthly rental fees for hardware from providers. I also have YouTubeTV, which eliminates a DVR by recording shows in the cloud.

---

### Post by DuckHook on 2021-02-10
> **linuxyogi said:**
> I contacted both & they told me I have no other choice but to use their modem/router hybrid device.
This is true of many ISPs. It's understandable because they don't want a dog's breakfast of different devices impacting their network. Some users know just enough to be dangerous. Others are simply up to no good. So they exert at least some measure of control over their least secure attack surface by policing the consumer endpoint.

What they may not have told you—perhaps because they were confused by the way you phrased your question—is that almost all ISP routers are capable of being set up as simple bridges so that they act in effect as modems. Most ISPs are aware that knowledgeable users for many good reasons want to use their own routers. Their business customers would absolutely not put up with being forced to use the ISP's routers, so they clearly must have the capability to set those routers into bridge mode. Your misunderstanding may have been caused by requesting to use your own "device", which would not be allowed (for good reasons).

You don't need your own "device". You only need them to set their device as a simple bridge.

Re: connecting straight to your computer—as TheFu has exclaimed, this is highly unwise unless you know *exactly* what you are doing and are already most of the way to being a security guru. I consider myself something of a security&#8209;savvy power-user and I would never risk it. As much as we sometimes dump on router OEMs, the fact remains that they are in business to build proper firewalls. They can (and should) be raked over the coals for orphaning their equipment, but they are still more knowledgeable on the initial get-go than the vast majority of general users.

---

### Post by linuxyogi on 2021-02-10
> **DuckHook said:**
> This is true of many ISPs. It's understandable because they don't want a dog's breakfast of different devices impacting their network. Some users know just enough to be dangerous. Others are simply up to no good. So they exert at least some measure of control over their least secure attack surface by policing the consumer endpoint. 

Does your ISP do the same ? I mean force you to use their own router/firewall ? What have you done ? Are you using your ISP's router coz you have no choice ?

I am asking this question to all my friends who replied to this thread. Please reply. I am feeling trapped. I need a way out.

---

### Post by DuckHook on 2021-02-10
I've already told you what I've done. Please carefully read my previous reply again.

Though I must use my ISP's "device", they are happy to put it into bridge mode for me, which effectively turns it into a plain modem. If yours will do the same, then no trap exists and no point in feeling that way.

I don't know how ISPs behave in your country, but I would be very surprised if they refused to bridge it for you. As I've already written, no business would stand for an ISP that dictated the use of their router. It's a fundamental security/operational requirement and it's non-negotiable.

Instead of anticipating issues, simply ask your ISP to set their device as a bridge. Then it's a nonissue.

---

### Post by linuxyogi on 2021-02-10
@DuckHook
I found a Facebook group which is created for Reiance Jio Fiber users. I asked them if I can use my own router. They told me its not possible for 2 reasons. The first reason is that they use a hybrid device which does 2 tasks. It converts the fiber to ethernet & do routing & wifi. The second reason is Reliance Jio fiber doesn't allow their router to use bridge mode.

Please watch this video & you will get an overall idea how things are done in my country. Just 10 mins >>>>[URL="https://www.youtube.com/watch?v=1xnLxbhgkiI"]https://www.youtube.com/watch?v=1xnLxbhgkiI

[/URL]

---

### Post by TheFu on 2021-02-10
> **linuxyogi said:**
> Does your ISP do the same ? I mean force you to use their own router/firewall ? What have you done ? Are you using your ISP's router coz you have no choice ?

I am asking this question to all my friends who replied to this thread. Please reply. I am feeling trapped. I need a way out.

My ISP does require using their equipment AND they control all external BGP routes on their equipment.

Like  DuckHook, have setup their equipment into "bridge mode", so all the public IPs I have are passed through to my equipment.  I consider the ISP equipment just as dangerous as stuff hosted by Google, Amazon, MSFT, and every other cloudy service. That box, sitting 1m away from me is NOT trusted.

I have a business connection at home for a few reasons.  It is illegal in my country for residential ISP connections of this type to force the use of ISP-provided equipment, but that doesn't apply to all ISP types nor to business connections.  The ISP provides a DOCSISv3 router+modem+wifi-AP - an all-in-one device.  
The Wifi is not used by me. They enable a hot-spot for other customers to use as part of the residential connection offer. I've thought about wrapping the router in a Faraday cage to prevent that traffic. It has been handy for 1 of our house guests. My ISP plan doesn't provide hot-spot access, so I've never used it or even attempted to use it.  I could enable a wifi-SSID on it, but don't. Most connect to my AP which is connected to the ISP router and treated as a dangerous network node on the internet. My AP is for android devices that cannot support wired ethernet connections. They use a VPN to gain internal LAN access, when needed.
The router part provides a gateway IP, a 10.1.10.0/24 wired LAN subnet and passes through 5 public IPs to my router (bridge mode) - a /29 subnet.  On the 10.1.10.0 wired subnet, I have placed a few untrusted IoT devices, following the advice from the FBI.
The modem part uses tftp to pull firmware, settings, etc over their modem connection from the ISP which controls everything.  Nightly, they reset the password so any technicians who leave or get fired by the company don't have access to millions of these CPE - Customer Premise Equipment.
This DOCSISv3 router+modem+wifi-AP is made by Cisco - meh.  Back when I worked for a very large telco, management systems for CPE was one of my infrastructure projects. Fortunately, I didn't have to get too deep into the details, just setup a bunch of tftp servers that each CPE would pull firmware/settings from at reboot.  We only had 45M customers, but some napkin calculations for bandwidth needed to support all the CPE which might be booted after a huge power outage wasn't really that high. I used 4x the current firmware size to allow for some growth in bandwidth needs and for more customers.

Things in central Asia are different than in the US.  I get that.  Spent a few weeks there upgrading wifi and routing for a monastery. They had a fibre connection, but also had to deal with daily, power outages. These were scheduled to provide power to other parts of the country. Fibre was more reliable internet than other options there. The campus had a 1Mbps link for about 30 people, mostly monks with sponsored cell phones. Wifi was important to them. Monks loved youtube. ;)

---

### Post by linuxyogi on 2021-02-10
@TheFU
I really need your advice before I choose my ISP.
At the moment I have 2 choices. 
(a) Choose a "local" ISP. These local ISPs provide connection using NAT. They provide both CAT5 cable (for low speed connections) & fiber (for high speed plans). If you take their connection and go to the "Network" part of your file manager your neighbour's computers will appear in your computer. You understand what I mean ? Different file managers call this "Network" differently. Since I am using PCMANFM I see it as "Network". They provide username/password to their customers. I dont know which authentication method they use but its definitely not PPPOE. People have told me that its very very insecure.

If I choose this kind of ISP I have absolutely no problem in using my own router. They do not force people to use their router. In fact they dont have any router. If the customer asks for wifi capability which requires a router they just buy a router of whatever brand they like with an extra commision.

(b)Now I have a second option namely Airtel & Reliance Jio. I havent used their connection but (a) the problem of your neighbour's PCs appearing on your PC does not occur & (b) they use PPPOE for authentication. Atleast that's what other users have told me. 

If I choose any of big players ie Reliance or Airtel I get a optic fiber cable to my home. They use a modem/router hybrid device. I have no other choice but to use their device. They don't even allow to put their router in bridge mode.

Which type of ISP should I choose ? Your advice is really important.

---

### Post by TheFu on 2021-02-10
> **linuxyogi said:**
>  Which type of ISP should I choose ? Your advice is really important.

I don't know what is important to you.  Make a list. Assign weights to each item in your list. Weigh the security, convenience, price and mitigations **you** can reasonably accomplish to provide enough security for your needs.

In the 1990s, here we had the ability to "browse" the subnet, see our neighbor's computers and some storage they had. The ISP deployed services without any mention of using a router or firewall, so most people didn't bother.  Let's just say, some neighbors saw files and directories moved. Perhaps a new file would show up on their desktop? Heard that an IBM-Fellow had that happen to his home system through "a friend." Nothing was deleted or harmed, just moved nearby ---- I heard.  Could that happen to you? Is that ok?  Can you take the steps needed to prevent it?

For my needs, a NAT connection is useless, but that's me.  Perhaps your ISPs support IPv6?  Would that prevent the need for NAT?  NAT can break all sorts of things that I use constantly, but only you know what you use and can tell whether NAT matters much.

Good luck.

---

### Post by DuckHook on 2021-02-10
TheFu's advice of a short and dirty cost/benefit analysis is excellent.

The results of such an analysis will be different for you than for me. But perhaps it would help to state what I would do if presented with such poor choices:

[LIST=1]
[*]Choose the most reliable, fastest and highest bandwidth alternative (these properties almost always go together) which would likely be one of your big players.
[*]If you are absolutely sure that the router does not allow bridging, then go into its settings and at least do the following:
[LIST=a]
[*][*]enable the DMZ and set it to a static IP
[*][*]deactivate the WIFI entirely (turn off the radio)
[*][*]constrain the other settings as much as possible (taking care not to lock yourself out)
[*][*]buy a good router with VPN capabilities. Alternatively, if you know what you are doing, replace its firmware with Tomato/OpenWRT/DD-WRT
[*][*]Set this router to the DMZ address. If DMZ is unavailable or scares you, a similar setup can be achieved by port forwarding everything to your own router.
[*][*]Purchase a VPN account from a good provider (must have good reliable throughput). The free ones are practically unusable.
[*][*]Establish a permanent VPN channel between your router and the VPN provider.
[*][*]Set all of your machines to go through your own router; not the ISP's.
[/LIST][/LIST]
This is not ideal (expensive and double NATed), but it will allow you to bypass the ISP entirely and stop them from spying on you. If you have more than typical needs like self web hosting or mail hosting, then you will need further workarounds, but they are not insurmountable and if you are that ambitious, then your technical skills will surely evolve to be up to that challenge.

---

### Post by linuxyogi on 2021-02-11
@DuckHook
I have read you reply carefully. What if I do none of the steps you suggested other than turning off the wifi radio & just connect a cable from one of the LAN ports of the Jio/Airtel router to my own router. I mean the ISP router acts as a "perimeter router" & my own router acts a secondary line of defense. Do you think such a configuration will be secure ?

---

### Post by DuckHook on 2021-02-11
Yes, that would work, but you need to be aware of the limitations:

[LIST]
[*]Without a VPN, your ISP can inspect every packet that goes out and comes in. If such tracking is not a concern, then the VPN and its cost is unnecessary.
[*]You will be double NATed. The ISP router will assign you to one NAT subnet, say 192.168.1.0/24 . Your own router will treat this as its WAN address, then will run yet another NAT subnet, say 10.10.10.0/24 and assign all of your devices address in the 10.10.10.xxx range. This will confuse some apps. For example, I cannot run TOR Browser in a double NATed environment. Maybe it's just me, but it will only work for me on a single layer of address translation.
[*]If you are just browsing with a general browser, it should not give you too much trouble, but if you want to set up any sort of listening service (web hosting, mail, cloud hosting, private VPN, etc.) you will need to do some fancy contorting.
[*]If you are unwilling/unable to DMZ or set up port forwarding on the ISP router, then be prepared for some frustration. Some apps do their business on specific/obscure ports, but you will have two layers of firewalls to manage. Sometimes things/apps will not work and you'll be left with few clues as to why.
[*]My experience is that more packets get dropped and the quality of service takes a hit with each NAT layer.
[*]
[/LIST]
But let's not excessively anticipate trouble beforehand either. Many people double NAT. Some people bring their own routers when travelling. They plug it into hotels, condos, etc on the entirely appropriate suspicion that hotel/cafe/AirBnB routers are not to be trusted. These personal routers are often set to automatically establish a VPN connection with, say, their VPN server at home, but you are not after that sort of functionality.

The general principle is that your own router will do the heavy lifting and guarding. The ISP router will just be used as a conduit whether it is bridged or not. Understand, however, that it is still imperative to set the ISP router up securely. You don't want some bad actor pwning it and using it for nefarious purposes. The only small observation I would make to your assessment is that your own router is the primary line of defence. The ISP router is not only *not* a defence&#8212;it should be treated as suspicious.

As for security, well, if you are not willing to VPN, then there's an upper limit to how much security you can expect. However, ***provided you buy a good router AND set it up properly*** then you will be as secure as can reasonably be expected in a general consumer environment.

---

### Post by linuxyogi on 2021-02-11
@DuckHook
_VPN_
I have never used a VPN but recently I started using a Firefox feature called DNS over HTTPS (Doh). 
[https://hacks.mozilla.org/2018/05/a-cartoon-intro-to-dns-over-https/](https://hacks.mozilla.org/2018/05/a-cartoon-intro-to-dns-over-https/)
They claim that it will protect my privacy. What's your opinion about this feature ? Can it be an alternative to a VPN ? 

> ***provided you buy a good router AND set it up properly***
My plan is to use [Smoothwall]("https://www.smoothwall.org/"). I have in the past used PFsense but the problem is I don't know why but their forum has completely vanished from the www.
In your opinion is Smoothwall a good choice ?

---

### Post by TheFu on 2021-02-11
DNS over HTTPS only addresses DNS queries. While that is important, it isn't the whole issue if you want to stop an ISP from knowing where you go online. DNSSEC would be better.  I haven't setup DNSSEC. It isn't commonly available.  Because of where I think you live, the govt there does seem to like to block what they deem objectionable content. 
Smoothwall Express (the only free version) hasn't been updated in years - 2014 was the last release.  RUN AWAY! [https://www.smoothwall.org/releases.html](https://www.smoothwall.org/releases.html)
If you are planning to get it from somewhere else, be certain they are reputable.  The other places I've seen project files, were updated a year ago. Be very careful.

---

### Post by linuxyogi on 2021-02-11
@TheFu
Frankly I don't want to spend money on a VPN. If I find a website which I want to view is blocked I use the Tor browser.
If you are in my position which free & open source firewall distro will you install ?
Pfsense used to have a dedicated forum.I was a member of that forum but now when I search "pfsense forum" on Google I see a netgate forum thing.

---

### Post by DuckHook on 2021-02-11
There are dangers to trying to do things on the cheap. As your inquiry about Smoothwall and TheFu's response shows, there are all sorts of hidden dangers out there, including stuff that *claim* to be your friends, but are pwned by script kiddies, the mob or some North Korean government agency. Phishing, false flagging and subterfuge have evolved into a fine psychological art these days. Because of this, I make it a habit to not comment on products I know nothing about such as Smoothwall. You must do your own research and make up your own mind.

What I *will* say is that I provisionally trust only three router products: Tomato, OpenWRT and DD-WRT (and even these have limits). They have been around forever, have active devs, demanding and knowledgeable communities, and are constantly maintained. If none of these products are available, then the only alternative I would trust would be my own homespun router. But spinning up a router with dmsmasq, the proper firewalls, settings, etc is not a trivial exercise and I would like to avoid it if I can.

While it offends the spirit of these forums to endorse any one VPN provider, I can note that my provider charges me US$24 a year. This allows me to use five concurrent devices, so it not only covers my home router, but also all of my and Mrs DH's mobile devices. That's very little cost for the added security, privacy and peace of mind. Throughput and bandwidth are excellent. I did get a good deal years ago that has been grandfathered annually, but a quick websearch shows that new pricing is still quite reasonable. It's your call, but a VPN makes a lot of your concerns just evaporate.

Further note: don't conflate firewalls with privacy. They have little to do with each other. Smoothwall, Pfsense, etc stop bad guys from penetrating into your subnet. VPNs stop your ISP from spying on you. You started this thread by asking about which ISP to use. From the context of your question, I assumed that you wished to guard against their spying. No firewall will do that for you, no matter who you download or buy it from.

---

### Post by TheFu on 2021-02-11
> **linuxyogi said:**
>  
If you are in my position which free & open source firewall distro will you install ? 

OPNsense is what I use. ddwrt and openwrt are fine.

If I wasn't a big nerd, I'd get a microtik to avoid the hassles, but get the features and support i want for cheap. Just depends on how much hassle you are willing to have.

Thought I'd already covered this above. Guess that was in another thread of yours?

---

### Post by DuckHook on 2021-02-11
> **TheFu said:**
> &#8230;If I wasn't a big nerd, I'd get a microtik to avoid the hassles, but get the features and support i want for cheap&#8230;
@TheFu

Once again, thanks for sharing. Was not aware of these guys. Just checked out their site. They look *very* interesting. They seem to straddle everything from home router to enterprise level to hobbyist. You mention that they have a track record of long term patching and not orphaning their HW&#8230; personal experience or general knowledge?

---

### Post by linuxyogi on 2021-02-12
Thanks once again to all of you who replied.
Q1) Is a perimeter firewall necessary for Ubuntu ?
Ans: Yes
Q2) Which opensource firewall distro is actively maintained & secure ?
Ans: OPNsense/ddwrt/openwrt

[SOLVED]

---

### Post by TheFu on 2021-02-12
> **DuckHook said:**
> They have a track record of long term patching and not orphaning their HW… personal experience or general knowledge?

Both. 

I had to swap out a microtik router for a client who needed QoS support and at the time, pfSense was the best tool for that. These days, I think microtik routerboards (RB) have good QoS support. They've been around a while.  They did get caught violating the GPL early in their business, just like Ubiquiti and Linksys did.  Microtik is less friendly towards F/LOSS projects, but most of their software is F/LOSS and they do make it non-trivial to get.  Last time I looked a few years ago, they charged $35 for a floppy disk to get a copy of all the software rather than posting it online for free.  But ... if you just want the results and don't care about a holi-war over F/LOSS principles like most people/businesses, then just get passed that and be happy.

About 10 yrs ago, there was an industry-wide bug in almost all linux-based routers that allowed remote take-over of the router. When that was announced 2 companies had patches ready for 1-click updates the same day.  Microtik and Ubiquiti where those companies.  And their fixes weren't like MSFT where they do more harm than good and the fix needs to be fixed. ;)

OTOH, BSD-based routing software wasn't impacted, but BSD has a 20 yr lead on making secure network stuff.

---

### Post by TheFu on 2021-02-12
> **linuxyogi said:**
> T 
Q2) Which opensource firewall distro is actively maintained & secure ?
Ans: OPNsense/ddwrt/openwrt 

That's a minimal list.  I'd include pfSense.  There are definitely others, but the research on each is a little harder.  Of that list, only 2 have working, commercial, plans today.  ddwrt and pfSense. Commercial funding of some sort helps these people do the work.  Nothing against the all volunteer tools, but day jobs get in the way of the speed to solve new problems.  Eventually, those teams will need a profitable commercial arm to their projects.

---

### Post by linuxyogi on 2021-02-12
@TheFu
I have used pfSense in the past. I know how to install/configure pfSense. Before actually implementing I will download all of them excluding pfSense & try them out in a virtual environment like Virtualbox.
So that I get a feel of the web interface of each. Is that a sensible idea ?

---

### Post by TheFu on 2021-02-12
Sure. I do that sometimes too.

---

### Post by Geoff_Lane on 2021-02-18
Agree with TheFu - too many out there trying to get into your computer to leave it vulnerable.

I recently bought a cheap TP-Link TD-W9970 router (For UK lines) and am quite pleased with it.

Even out of the box provided you enable wifi security it works pretty well, if you use an ethernet wire then immediately have the protection of being behind a router, nothing should get in unless you've invited it or in response to something you've sent.

If you get a FireTV then you can (If you want to) isolate it from your Ubuntu machine.

Geoff

---

### Post by kevdog on 2021-02-19
untangle is another commerically available router/firewall you can look at.  It's like pfsense but it runs on Debian.

---

