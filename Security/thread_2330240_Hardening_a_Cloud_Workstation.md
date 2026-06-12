---
title: "Hardening a Cloud Workstation"
date: 2016-07-09
forum: Security
---

### Post by branau on 2016-07-09
Hi everyone, I'm looking for some advice on the feasibility of using a cloud workstation. My main concern regarding this is of course security. Here's what I'm looking to achieve:


[LIST=1]
[*]The ability to work anywhere, as long as I have an internet connection
[*]The ability to work from any device, so that I don't need to rely on expensive hardware
[*]Peace of mind knowing that my data is secure (because really, it wouldn't be all my own data)
[/LIST]

I'll cover the why at the end, but for now, is this reasonable? I need something like a DigitalOcean droplet that I could spin up and connect to work on, and preferably persist the data. I currently have a web server running on Linode that I rent each month and I host a Codiad editor there so that I can work on code all in the cloud right now, but I only use it for small, personal projects that don't contain any sensitive data. Ideally, I'd like to harden my setup so that I could use it for my serious work projects as well, but I have a few concerns. 


[LIST=1]
[*]Can VPS providers be trusted? I don't know if it would be a good idea to leave my data in their hands because I'm not sure how much access VPS providers allow themselves to my "private" data. I suppose I could cover my tracks by encrypting all of the data, but would that suffice?
[*]Should this be separate from my web server? My concern is that if there was a vulnerability in my web server, an attacker could somehow gain access to other parts of the server, including where my private work projects are stored. I would rather pay the extra $10 a month for a separate virtual server than risk my work being compromised if that's a threat.
[/LIST]

I'm sure there are other security concerns that I might not be thinking about, which is also why I'm coming here with this. If anyone could help me address these and other problems, I would greatly appreciate it. Finally, I'd like to give some background on myself and my motivation for doing this:

I move around a lot (I'm 21 years old and have lived in 14 different cities across 3 countries and I can't remember how many different houses/apartments/cars I've slept in). I don't foresee myself settling down in one place any time soon, and now that I'm on my own, I tend to travel a lot because my work permits me to do so. Because of this, I'm looking to lighten my load, and be able to work from a tablet with a keyboard/mouse or a Chromebook and just SSH into my server to get some work done. I'd really like to be able to avoid expensive hardware, and pay more into the cloud, in case of any problems that I run into. While traveling, things get broken or lost or stolen, and I'd rather have to replace a $150 Chromebook than a $1,000 Dell or System76 or whatever I've got on me in case of some problem. For work, I do a mix between PHP/JavaScript development and Linux system administration, so both I could easily do via a remote server as long as I had an internet connection (which is really something I need to work even locally). In my mind, working from the cloud would solve my problems because I could use cheaper hardware that's easier to replace, and also smaller devices like Chromebooks that are light and easy to move around. I don't live in hotels or anything like that, but I've never been in one spot longer than 4 years at a time, and I've been in some places as short as 6 months before I moved again. 

Anyways, I would greatly appreciate any advice or constructive criticism that anyone has to offer!

Cheers

---

### Post by DuckHook on 2016-07-10
You make a strong case for a cloud-like solution, and the technology was developed in part for people just like yourself. The popularity of cloud solutions is growing exponentially, and Canonical, the parent firm of Ubuntu, is a big player in that market. It is also used by most major corporations these days, so it can hardly be said to be a nascent technology or even a junior one.

However, you are asking about security, and this is where things get murky. Any time things get more complicated, security follows right along and gets just as additionally complicated. Cloud computing adds several additional layers of complexity, so you are very wise to seek out opinion before taking the plunge:

Here are a few articles that might help:
[http://www.infoworld.com/article/3041078/security/the-dirty-dozen-12-cloud-security-threats.html](http://www.infoworld.com/article/3041078/security/the-dirty-dozen-12-cloud-security-threats.html)
[http://www.cloud-council.org/deliverables/CSCC-Security-for-Cloud-Computing-10-Steps-to-Ensure-Success.pdf](http://www.cloud-council.org/deliverables/CSCC-Security-for-Cloud-Computing-10-Steps-to-Ensure-Success.pdf)

...and one of the best is actually from that old standby, Wikipedia:
[https://en.wikipedia.org/wiki/Cloud_computing_security](https://en.wikipedia.org/wiki/Cloud_computing_security)

Since you will be handling other people's data and doing this as part of your work/professional services, I would strongly advise you to engage a real security professional, preferably a firm. This is one area where it is a really bad idea to just "wing it".

---

### Post by TheFu on 2016-07-10
Ok, a few comments.

Can you trust any cloud provider?  No.  You don't control the hardware, therefore you are at their whim and the whim of whatever DevOps team they have and whatever country's govt is involved.  There have been occasions when the FBI took an entire rack of hardware because 1 company was hosted in that rack - 300+ OTHER companies had a really bad day.  There was a Canadian company nearly taken out of business over this.

Your data isn't any safer in the cloud than it is at home.  You need it both places and it needs to be encrypted, always.

Ok ... so if I'm so against this, why reply at all?

a) I've had a "private cloud" that is under my physical control running since 2008-ish.  Moved my primary desktop into a headless VM around 2011-ish. There are things that aren't possible with this solution - think of all the physical things you'd like to do - ripping a DVD, watching a video, listening to Music, simple things like that either don't work or work with lots of caveats.  

b) Lived in 14 different cities and 11 different states - most by the time I was 23.  I understand the need to be light and mobile.

c) Tried to travel lightly beginning in 2008.  Started with a Nokia tablet (debian based), which worked surprisingly well at the time. This was NOT a phone. Had to carry a BT keyboard and fight with a 4in screen, poor battery life, slow CPU, non-standard charger, and rebooting to change the battery.  
Got a 10in Android tablet (with USB keyboard) and tried a 2 week trip through Europe (5 countries). At the time, most of the hotels only had wifi in the common areas, not in the rooms. Rooms were wired ethernet. Tablets need wifi, left a travel wifi router at home to save weight. Plus a few of the hotels blocked ports and android just wasn't enough OS to find a way around their blocks. Wasn't able to get a tunnel working for VNC to be used.  VNC cannot be used without either ssh or a full VPN. 
Moved to an 10in Asus Eee.  For the most part, it was a good experience, just slow Atom, 2G of RAM, 2 hrs of battery, terrible resolution. After traveling to 3 continents with it, decided it was time to upgrade. 
Acer C720 Chromebook - wiped ChromeOS, loaded a minimal Ubuntu (personal preference). Got everything working, used NX for the remote desktop, 7+ hrs of battery, fast enough to make me smile (2955U was an amazing CPU). Even got KVM working (though with 2G of RAM, it wasn't worth it).  After 18 months the keyboard stopped working. Attempts to replace it pointed out a huge flaw with these devices. $90 for the assembly which also holds the keyboard. Somehow, I broke the LCD - $30 ... then I'd bricked the C720 and needed $50 in equipment to de-brick it.  Decided it was time for a nicer Chromebook. I will never buy anything from Acer again due to a number of tiny issues with the chromebook and that tablet above.
Toshiba 13in - 1080p, 8+ hrs of battery, Core i3, nice keyboard, 4G of RAM, user replaceable m2.SSD, and I already had the USB3-to-GigE adapter.  Typing on this now - has Ubuntu Mate installed, but I login to a minimal openbox environment.  Running a few VMs, still use NX (x2go) to connect to my private cloud, along with ssh - mostly use ssh for stuff.

Should point out that I have a Core i5 Dell Laptop which was the best laptop I'd owned for about 5 yrs. It is till working, though the Toshiba is faster (much newer generation).
[B]
None of these touch the performance from a $450 desktop. Not even close.[/B] 

So ... recommendations.
1) get a whitebox midtower desktop to be your "server."  Spend $450-ish and you'll be amazed. Setup x2go and ssh - x2go uses ssh tunneling. Lock down ssh access and only allow key-based connections over the internet.  The next upgrade will be $200.  I've been doing this for years and years.  Keeping the RAM, PSU, cheap video card, and HDDs all this time. Plus it has an extra disk for backups ... you'll want to backup that local data somewhere.  As a software developer, you'll need a git server - use this desktop for that too. The desktop you can build for this price will easily support 20 VMs or almost 200 containers. Plenty of trouble to get into with that - much more cost effective than buying those at a provider.  Plus it isn't like you won't have broadband internet at the house/apartment, right?  I have 2 external disk arrays and 4 internal disks in mine. Get a quality Supermicro JBOD card (4 SAS ports == 16 SATA) and you'll never run out of ports. No need for a monitor, BTW.  USB3 is fine for backups.

2) get a nice chromebook - not the $150 version. 768p just isn't enough pixels and 2G of RAM isn't enough for someone like you or I.  We don't need 16G (not doing java here), but 4G is a "nice" point. 2G just isn't quite enough - modern browsers will suck that up.  The current Toshiba for $330 has a fast CPU that won't feel slow, under 3lbs, 1080p screen. It isn't perfect - be very careful with the screen, only open it from the center, slowly. Don't hold it by the screen/lid either. Toshiba is known for refusing screen warranty claims.  Dell Chromebooks are VERY nice, but $200 more.  The toshiba was the best choice for me in Feb and I don't think that has changed.  I really do miss having a Delete key, F11, F12 keys, however. 

3) For a remote desktop, use x2go. Even from across the Pacific, normal productivity applications work just like being on the machine. It feels 2-3x faster than VNC or RDP. That limits which client devices can be used - must be Linux, OSX, or Windows. No iOS or Android support.  If you are working, you'll want a keyboard anyway. If you need a replacement device, boot up Linux on a USB stick, apt install x2go-client openssh-client fail2ban then generate some keys for the remote machine. ssh-copy-id, and you are back up and running. This can be preconfigured on a flash drive.

Oh ... and only the lite-DEs work for remote desktops. That means no Gnome3 or Unity.  Video streaming barely works on the same GigE LAN, audio works well on the LAN.  I can't really tell the difference between using the remote desktop and running programs locally on the LAN. I use sshfs a bunch to access audio when away.

If you need a VPN, use an IPSec VPN, not pptp (which has been broken since 2002-ish). Run the version you use on your own HW - so that's 2 ports open which need to be secured.  Some country-based blocking is useful, but running on non-standard ports is handy too ... until a hotel decides to block all ports except 80, 587, 443, .... that's about it.  So would be smart to have ssh on 443 in addition to some random port very high. Use a dynamicDNS provider for convenience.

Don't put an internet facing web/smtp/anything server on your desktop. 'nuff said?

Every few years, I got through a "data center consolidation" here. New equipment arrived, but didn't necessarily replace anything. Been using smaller, less wattage, systems more and more. A system built for $150 last year is faster than a $500 system from 2010. If you don't need tons of CPU, a $100 MB+G3258 CPU can make a fine desktop, media server, ebook server, backup server, plus have room for 10+ VMs. If you load it up, it won't be fast, but ... for less than 60W, it is amazing.

Cloud security ... ah ... in the public cloud, you cannot convince me there is any security, only TIME and frustrated crackers will convince me of that.  At this point, I just haven't seen any frustration from them.

Last month I attended a Linux conference with lots about cloud this and cloud that, including cloud security.  The videos from it should be posted to youtube ... nope. Not yet. In 2015, the HVM solution was found to have a few different take-over-the-entire-system bugs. This was over a decade AFTER it was considered production ready and widely adopted.  So ... there isn't any absolute security and your specific risk factors have to be weighed before making this decision.  

Jut remember that cloud VMs are running on someone else's hardware, on someone else's network, using someone else's storage. All of these things are shared with other people/companies, some will have bad intentions. Lots of my red-team security professional friends use cloud providers to do some nasty things. They take great lengths to avoid being traced back to themselves - phony names on credit cards, always use a VPN exit node from other countries, often hopping through different corrupted systems to make tracking them just a little harder. Be afraid.  Sure, they aren't likely to be after you, but OTOH, they are after everyone.

Did I cover everything? Probably not. Hopefully it isn't just babble either.

---

### Post by DuckHook on 2016-07-10
^The Fu

Not babble as far as I'm concerned. A very interesting perspective that conforms to my own rather paranoid instincts, so I do admit that there may be some confirmation bias at work on me here.

For what it's worth, I do not use cloud computing. Such cloud-*data* as I have, whether Google Drive or Dropbox is innocuous stuff that I wouldn't care having broadcast to the whole world. Like The Fu, I take the attitude that once it's out of my physical control, it's public. I am not advocating non-privacy (quite the opposite, in fact)&#8213;I'm just taking the realistic and conservative approach that if I don't control it, I must assume that the guy who does control it can get up to no good.

I assume The Fu is talking about either running your own VPN or ownCloud. These are technologically marvellous options, but you must note that they require:

[LIST=1]
[*]
[*]You to set up and maintain your own servers
[*]A good ISP connection with decent upload speeds. Since most ISPs throttle uploads to be 1/10 their download speeds, you usually have to buy their commercial services, which can be quite expensive.
[/LIST]
The whole topic of security is vast, very complex and to a large extent, subjective, because it depends on risk tolerance, which varies from person to person. What The Fu and I would find unacceptable may be perfectly okay to you, though you must be far more careful with the data of others than with your own.

Good luck in your continuing research! If nothing else, it will be interesting and educational.

---

### Post by TheFu on 2016-07-10
@DuckHook - think you got exactly what I meant, but for clarification of others .... 

A "server" doesn't need to be a $3000 piece of hardware. My "servers" are $300 (or less) desktops that just happen to run a server install (debian or Ubuntu). Each "server" is a VM for me. The hostOS is **not** directly available over the internet. Whether that helps with security or not is still a question. I believe it does.

Any home broadband with 128Kb up can be used for this stuff on a small scale.  I managed Mom's system from 3 states away for years and she only had a 128Kbps DSL connection.  Many businesses ran many different data services over T1 lines (1.54Mbps) for decades.  When I started running servers from home, only had 384Mbps up here.  Now only have 10x that and don't have **any** bandwidth issues when the connection is up. OTOH, for the last 2-3 months, my internet connection has been flaky, but not enough that I'm pissed enough to deal with customer support and have a truck roll. About every 5-8 yrs, I need a truck to fix some connector somewhere in the chain from the street to my router. Always happens in summer. Think the dB loss due to distance from the curb is the main problem due to the layout of coax at my house.

BTW, I have a 16/3 plan and that ratio seems common for non-DSL providers (except TW).

Excellent points about your and my level of paranoia when compared to that of other people.  
For reference,
I don't use cloud storage for anything. No google data (though I have 3TB free), no drop box, not much social networking ... never with my real name.  I have 5+ google accounts, which are used for different purpose, but not for email.  On Android, I don't use any google email, google chat, and avoid google maps as much as possible.  Haven't used hangouts ever.  If I need to share information with someone, I'll post it on an ugly URL on one of my public servers.  I am slightly offended whenever people give me a gmail/yahoomail, outlook or other huge email service address in their contact info.  They are forcing me to give up my privacy just to communicate with them. No matter how hard I try to avoid google and their data slurping ways, my friends are forcing me to use it to be part of their lives.  How rude.

I avoid cloud services, unless absolutely necessary.

At the network layer, I block much of google, all of facebook, much of twitter, and any of the other major tracking subnets/DNS/URLs.  Lifehacker republished one of my articles about this.  If you can see **anything** from a site on a webpage, then you've already failed.  Those tiny "G+" buttons ... they are tracking you even if you never push it. Each is unique for you and the page being visited. There are many things we don't see which also track us.  I don't know how to stop it, but I try to provide miss-information as much as possible.

My years in telecom taught me many things about privacy, most would scare average people, but not sufficiently for them to give up the convenience of a personal tracking device for even 1 day.  The metadata captured based on smartphones and internet data use is amazing. Almost don't need access to the content to build a profile about a person. Metadata is enough.  Metadata is what all the internet tracking is about.

Ah - babble myself off-topic again. Sorry.  The lack of privacy on the internet is an issue for me. The ruling in Belgium last week FOR Facebook to track people without their expressed opt-in was a major blow to people like me. [http://arstechnica.com/tech-policy/2016/06/facebook-wins-privacy-case-against-belgiums-data-protection-authority/](http://arstechnica.com/tech-policy/2016/06/facebook-wins-privacy-case-against-belgiums-data-protection-authority/)  I had hoped the courts would see the internet as a series of private roads where permission to spy must be requested, not as public streets for anyone with means to watch.

My cloud is private. There are multiple VMs running inside a network that I control. If you control the network, then you control everything. Is your ISP as trustworthy as any cloud provider?  I cannot say. Data privacy laws in the USA would say no, but data doesn't have anywhere near the same protections as POTS telecom. Cellular telecom isn't as protected either - just be aware. These laws are being re-interpreted constantly in the courts and law enforcement is doing some scary things without asking first.

[http://webhostblog.com/servers-seized-by-fbi-without-producing-evidence-or-probable-cause/](http://webhostblog.com/servers-seized-by-fbi-without-producing-evidence-or-probable-cause/)
[http://blog.instapaper.com/post/6830514157](http://blog.instapaper.com/post/6830514157)
[http://redtape.nbcnews.com/_news/2012/05/11/11647813-the-fbi-took-and-mysteriously-returned-their-server-heres-their-story?chromedomain=usnews](http://redtape.nbcnews.com/_news/2012/05/11/11647813-the-fbi-took-and-mysteriously-returned-their-server-heres-their-story?chromedomain=usnews)
[http://bits.blogs.nytimes.com/2011/06/21/f-b-i-seizes-web-servers-knocking-sites-offline/?_r=0](http://bits.blogs.nytimes.com/2011/06/21/f-b-i-seizes-web-servers-knocking-sites-offline/?_r=0)

Enjoy.  Seems I was confused into believing the USA was under rule of law, not rule of law enforcement.

---

### Post by branau on 2016-07-11
Firstly, thank you both for your replies! I greatly appreciate them :D

> **DuckHook said:**
> The popularity of cloud solutions is growing exponentially, and Canonical, the parent firm of Ubuntu, is a big player in that market.

One of the reasons I've recently come back to Ubuntu is because of their involvement in the cloud and because I generally view them as the most progressive of the Linux distros. No other distro is really working on mobile platforms at all, and I'm quite certain that that's where we're all headed. The days of desktop computers will probably be coming to a close soon and Ubuntu will be ready for it. Purely speculation of course, but I don't think it's so far-fetched.

> **DuckHook said:**
> Since you will be handling other people's data and doing this as part of your work/professional services, I would strongly advise you to engage a real security professional, preferably a firm. This is one area where it is a really bad idea to just "wing it".

I don't know if I would consider it worth the investment to go through a firm because at that point I would have to really question the cost vs value of running a cloud workstation. I do however respect the opinions and advice of the people on this forum and TheFu in particular has been a great mentor to me on various occasions, so I did want to check in here before going out and doing something stupid that could potentially get me into legal troubles. I've added those links to my reading list to take a look at them before I make any moves, so thank you for them!

> **TheFu said:**
> Can you trust any cloud provider?  No.  You don't control the hardware, therefore you are at their whim and the whim of whatever DevOps team they have and whatever country's govt is involved.

Good point, I really hadn't taken governments into account though I suppose they're the most likely to be snooping about my data. Ownership of the hardware makes sense too.

> **TheFu said:**
> a) I've had a "private cloud" that is under my physical control running since 2008-ish.  Moved my primary desktop into a headless VM around 2011-ish. There are things that aren't possible with this solution - think of all the physical things you'd like to do - ripping a DVD, watching a video, listening to Music, simple things like that either don't work or work with lots of caveats.

Do you do everything from your private cloud? I personally make use of things like Spotify, Drive, and Google Play for entertainment because I don't really care if people know what music I listen to or what movies I watch, and those services are all synced across my devices so I wouldn't think that I would need the private cloud for those things. I guess maybe private photos but those are pretty straight-forward.

> **TheFu said:**
> b) Lived in 14 different cities and 11 different states - most by the time I was 23.  I understand the need to be light and mobile.

You beat me on the states, I've only lived in 6 so far :P

> **TheFu said:**
> c) Tried to travel lightly beginning in 2008.  Started with a Nokia tablet (debian based), which worked surprisingly well at the time. This was NOT a phone. Had to carry a BT keyboard and fight with a 4in screen, poor battery life, slow CPU, non-standard charger, and rebooting to change the battery.  
Got a 10in Android tablet (with USB keyboard) and tried a 2 week trip through Europe (5 countries). At the time, most of the hotels only had wifi in the common areas, not in the rooms. Rooms were wired ethernet. Tablets need wifi, left a travel wifi router at home to save weight. Plus a few of the hotels blocked ports and android just wasn't enough OS to find a way around their blocks. Wasn't able to get a tunnel working for VNC to be used.  VNC cannot be used without either ssh or a full VPN. 
Moved to an 10in Asus Eee.  For the most part, it was a good experience, just slow Atom, 2G of RAM, 2 hrs of battery, terrible resolution. After traveling to 3 continents with it, decided it was time to upgrade. 
Acer C720 Chromebook - wiped ChromeOS, loaded a minimal Ubuntu (personal preference). Got everything working, used NX for the remote desktop, 7+ hrs of battery, fast enough to make me smile (2955U was an amazing CPU). Even got KVM working (though with 2G of RAM, it wasn't worth it).  After 18 months the keyboard stopped working. Attempts to replace it pointed out a huge flaw with these devices. $90 for the assembly which also holds the keyboard. Somehow, I broke the LCD - $30 ... then I'd bricked the C720 and needed $50 in equipment to de-brick it.  Decided it was time for a nicer Chromebook. I will never buy anything from Acer again due to a number of tiny issues with the chromebook and that tablet above.
Toshiba 13in - 1080p, 8+ hrs of battery, Core i3, nice keyboard, 4G of RAM, user replaceable m2.SSD, and I already had the USB3-to-GigE adapter.  Typing on this now - has Ubuntu Mate installed, but I login to a minimal openbox environment.  Running a few VMs, still use NX (x2go) to connect to my private cloud, along with ssh - mostly use ssh for stuff.

Should point out that I have a Core i5 Dell Laptop which was the best laptop I'd owned for about 5 yrs. It is till working, though the Toshiba is faster (much newer generation).

I've currently got a Dell i7 laptop with 8GB of RAM though I'm starting to find out that it isn't quite enough. Still, I'm not sure if it's worth the investment because if I could find a way to make the cloud workstation secure, then that would take quite the strain off my laptop. The problem I run into is when I run my IDE with my web server and my browser with 10+ tabs all open at the same time and I'm connected to the VPN with an open SSH session. I suppose I could learn to multi-task a little less but it comes with the job. I'm also curious to see how Ubuntu touch turns out, particularly on the tablet. I dual boot it on my phone with Android so that I can check in on it every once in a while and see the progress of it but it seems to me that it isn't quite ready for commercial use. I believe Canonical themselves state this as well.
> **TheFu said:**
> 1) get a whitebox midtower desktop to be your "server."

My only concern here is that I would need something small, like the size of the System76 Meerkat. It's a 4" square box basically so it would be pretty easy to transfer. My wife and I have plans to move around a bit until we can agree on a place to live in (I'm from the US and she's from Mexico and neither of us is very fond of the idea of living in either of those two countries), so until I can settle down and establish myself, I'm pretty much keeping my belongings down to what I can fit into a suitcase, carry-on item, and a backpack. 

> **TheFu said:**
> Setup x2go and ssh - x2go uses ssh tunneling. Lock down ssh access and only allow key-based connections over the internet.

Just for kicks, I went ahead and checked out x2go on my web server (which is running CentOS). I was amazed at just how fast and responsive it is, because I've tried out VNC before and it feels really slow. Thanks for the suggestion, I'll definitely be using this from now on. 

> **TheFu said:**
> The next upgrade will be $200.  I've been doing this for years and years.  Keeping the RAM, PSU, cheap video card, and HDDs all this time. Plus it has an extra disk for backups ... you'll want to backup that local data somewhere.

Upgrades aren't something I had thought about. Mini PCs probably aren't the greatest in this category, so I'll have to find some super slim casing that I can use to put together my machine in. I'm sure there's bound to be something useful to me on the market.

> **TheFu said:**
> As a software developer, you'll need a git server - use this desktop for that too. The desktop you can build for this price will easily support 20 VMs or almost 200 containers. Plenty of trouble to get into with that - much more cost effective than buying those at a provider.  Plus it isn't like you won't have broadband internet at the house/apartment, right?  I have 2 external disk arrays and 4 internal disks in mine. Get a quality Supermicro JBOD card (4 SAS ports == 16 SATA) and you'll never run out of ports. No need for a monitor, BTW.  USB3 is fine for backups.

Up until now, pretty much all of the code I've written has been on GitHub as open source, and for work I have to use whatever the company I'm working with uses to manage their code, but I suppose it might be a good idea to get something set up for the times when I'm not quite ready to share something or if for whatever reason I decide to write some private code. It does make sense that maintaining my own private server would be cheaper than paying for a VPS to host it for me though. I'll look into the JBOD card too, I admit I had never heard of those before. 

> **TheFu said:**
> 2) get a nice chromebook - not the $150 version. 768p just isn't enough pixels and 2G of RAM isn't enough for someone like you or I.  We don't need 16G (not doing java here), but 4G is a "nice" point. 2G just isn't quite enough - modern browsers will suck that up.  The current Toshiba for $330 has a fast CPU that won't feel slow, under 3lbs, 1080p screen. It isn't perfect - be very careful with the screen, only open it from the center, slowly. Don't hold it by the screen/lid either. Toshiba is known for refusing screen warranty claims.  Dell Chromebooks are VERY nice, but $200 more.  The toshiba was the best choice for me in Feb and I don't think that has changed.  I really do miss having a Delete key, F11, F12 keys, however.

Damn, I should've posted this like 2 weeks ago. I just recently bought a Chromebook that I got on sale from eBay, a new Lenovo N21 that cost me exactly $150. I wanted to check them out before I decided to commit and actually buy a decent one but the N21 has 4GB of RAM. The display is only 1366x768 though, but I so is my Dell now that I think about it. Lenovos are supposed to be a bit more rugged from what I understand, but I'll be extra careful with it just in case. I appreciate the tips.

> **TheFu said:**
> 3) For a remote desktop, use x2go. Even from across the Pacific, normal productivity applications work just like being on the machine. It feels 2-3x faster than VNC or RDP. That limits which client devices can be used - must be Linux, OSX, or Windows. No iOS or Android support.  If you are working, you'll want a keyboard anyway. If you need a replacement device, boot up Linux on a USB stick, apt install x2go-client openssh-client fail2ban then generate some keys for the remote machine. ssh-copy-id, and you are back up and running. This can be preconfigured on a flash drive.

Yeah, x2go is amazing, I wish I had known about it a long time ago. Definitely added to my list of must-have software, thanks again for the suggestion. I'll have to set up a flash drive too just in case. I try to keep solid backups on my external drive but I have no way to automate the process at the moment so it's only as often as I remember unfortunately. My SSH keys don't ever change though so those are safely tucked away in case I need to get them for a different device.

> **TheFu said:**
> Oh ... and only the lite-DEs work for remote desktops. That means no Gnome3 or Unity.  Video streaming barely works on the same GigE LAN, audio works well on the LAN.  I can't really tell the difference between using the remote desktop and running programs locally on the LAN. I use sshfs a bunch to access audio when away. 

I'm not too concerned about the DE, I can work with XFCE no problem. I've even gotten along with awesomeWM before. I'll need to look into sshfs though for the few local movies and music files that I have.

> **TheFu said:**
> If you need a VPN, use an IPSec VPN, not pptp (which has been broken since 2002-ish). Run the version you use on your own HW - so that's 2 ports open which need to be secured.  Some country-based blocking is useful, but running on non-standard ports is handy too ... until a hotel decides to block all ports except 80, 587, 443, .... that's about it.  So would be smart to have ssh on 443 in addition to some random port very high. Use a dynamicDNS provider for convenience. 

I'd definitely like to set up a VPN for when I'm in an airport or coffee shop or hotel or whatever. I'll do some research on some options and see which ones I like the best. I would have never thought about restricted ports though so thanks again for the helpful tips. 

> **TheFu said:**
> Don't put an internet facing web/smtp/anything server on your desktop. 'nuff said?

Fair enough, I'll keep 'em on separate VMs

> **TheFu said:**
> Every few years, I got through a "data center consolidation" here. New equipment arrived, but didn't necessarily replace anything. Been using smaller, less wattage, systems more and more. A system built for $150 last year is faster than a $500 system from 2010. If you don't need tons of CPU, a $100 MB+G3258 CPU can make a fine desktop, media server, ebook server, backup server, plus have room for 10+ VMs. If you load it up, it won't be fast, but ... for less than 60W, it is amazing.

The way things are going, tech is only going to get smaller. I've got a Raspberry Pi 2 B+ but I think I would need a cluster of them to be any good and even then it would be very iffy. I work a lot with a platform called Magento though so I think I do need a decent CPU if I hope to work on it at all. Magento is known for being a rather resource-heavy platform.

> **TheFu said:**
> Cloud security ... ah ... in the public cloud, you cannot convince me there is any security, only TIME and frustrated crackers will convince me of that.  At this point, I just haven't seen any frustration from them.

Last month I attended a Linux conference with lots about cloud this and cloud that, including cloud security.  The videos from it should be posted to youtube ... nope. Not yet. In 2015, the HVM solution was found to have a few different take-over-the-entire-system bugs. This was over a decade AFTER it was considered production ready and widely adopted.  So ... there isn't any absolute security and your specific risk factors have to be weighed before making this decision.  

Jut remember that cloud VMs are running on someone else's hardware, on someone else's network, using someone else's storage. All of these things are shared with other people/companies, some will have bad intentions. Lots of my red-team security professional friends use cloud providers to do some nasty things. They take great lengths to avoid being traced back to themselves - phony names on credit cards, always use a VPN exit node from other countries, often hopping through different corrupted systems to make tracking them just a little harder. Be afraid.  Sure, they aren't likely to be after you, but OTOH, they are after everyone.

Well I'll definitely have to audit my cloud resources just to make sure I have nothing that could possibly be private on there. I tend to only keep things on the cloud if I don't care about them being public but I did use encfs to hide some private things before I knew better. I'm still going to do some research and testing before I commit to this idea but you've certainly convinced me to stay away from VPS providers for this.


> **TheFu said:**
> Did I cover everything? Probably not. Hopefully it isn't just babble either.

Maybe not *everything*, but I think you've given me more than enough to work with for now, and I greatly appreciate it! I don't consider it to be babble either, I trust in your experience and the advice you've given me so far, so you have my respect!

> **DuckHook said:**
> For what it's worth, I do not use cloud computing. Such cloud-*data* as I have, whether Google Drive or Dropbox is innocuous stuff that I wouldn't care having broadcast to the whole world. Like The Fu, I take the attitude that once it's out of my physical control, it's public. I am not advocating non-privacy (quite the opposite, in fact)&#8213;I'm just taking the realistic and conservative approach that if I don't control it, I must assume that the guy who does control it can get up to no good.

I tend to have much of the same attitude when it comes to privacy online. I don't put anything private on Dropbox or Google Drive or Facebook or whatever because I've seen that pretty much anything that goes onto the internet is as good as public knowledge. 

> **DuckHook said:**
> I assume The Fu is talking about either running your own VPN or ownCloud. These are technologically marvellous options, but you must note that they require:

[LIST=1]
[*]You to set up and maintain your own servers
[*]A good ISP connection with decent upload speeds. Since most ISPs throttle uploads to be 1/10 their download speeds, you usually have to buy their commercial services, which can be quite expensive.
[/LIST]
The whole topic of security is vast, very complex and to a large extent, subjective, because it depends on risk tolerance, which varies from person to person. What The Fu and I would find unacceptable may be perfectly okay to you, though you must be far more careful with the data of others than with your own.

Good points indeed. My risk tolerance isn't that high, but I'm afraid that my ignorance is, which is why I come here looking for advice in the first place. Luckily there's a cure for ignorance :P I greatly appreciate your advice!

> **DuckHook said:**
> Good luck in your continuing research! If nothing else, it will be interesting and educational.

Thanks! I'm always looking to learn and grow and I'm sure that you're right about that.

> **TheFu said:**
> A "server" doesn't need to be a $3000 piece of hardware. My "servers" are $300 (or less) desktops that just happen to run a server install (debian or Ubuntu). Each "server" is a VM for me. The hostOS is **not** directly available over the internet. Whether that helps with security or not is still a question. I believe it does.

Yeah, I consider a server to be any machine that's running for a dedicated purpose, typically headless. Might be a vague definition but I think it's tough to really classify servers and with the IoT, definitions start to get blurry. 

> **TheFu said:**
> Any home broadband with 128Kb up can be used for this stuff on a small scale.  I managed Mom's system from 3 states away for years and she only had a 128Kbps DSL connection.  Many businesses ran many different data services over T1 lines (1.54Mbps) for decades.  When I started running servers from home, only had 384Mbps up here.  Now only have 10x that and don't have **any** bandwidth issues when the connection is up. OTOH, for the last 2-3 months, my internet connection has been flaky, but not enough that I'm pissed enough to deal with customer support and have a truck roll. About every 5-8 yrs, I need a truck to fix some connector somewhere in the chain from the street to my router. Always happens in summer. Think the dB loss due to distance from the curb is the main problem due to the layout of coax at my house.

Ah, I live in Mexico at the moment, been here for about 3 years now. I average around 500-600kbps downloads, when the internet works, on a good day, so I'm more or less used to slow internet. I don't even want to talk about my upload speeds. 


> **TheFu said:**
> I don't use cloud storage for anything. No google data (though I have 3TB free), no drop box, not much social networking ... never with my real name.  I have 5+ google accounts, which are used for different purpose, but not for email.  On Android, I don't use any google email, google chat, and avoid google maps as much as possible.  Haven't used hangouts ever.  If I need to share information with someone, I'll post it on an ugly URL on one of my public servers.  I am slightly offended whenever people give me a gmail/yahoomail, outlook or other huge email service address in their contact info.  They are forcing me to give up my privacy just to communicate with them. No matter how hard I try to avoid google and their data slurping ways, my friends are forcing me to use it to be part of their lives.  How rude.

I do accept that Google and Facebook are going to sell my private data, so I use their services, just very limited. Like I said earlier in this post, I consider anything that I do on the internet to pretty much be public knowledge because with data miners like Google and Facebook, it may as well be. The only exception for me is online banking, in which I really don't have a choice considering I live abroad and am paid via electronic transfers. It's not worth it to pay international fees every time I just want to go to the ATM to check my balance or take out some cash. 


> **TheFu said:**
> My years in telecom taught me many things about privacy, most would scare average people, but not sufficiently for them to give up the convenience of a personal tracking device for even 1 day.  The metadata captured based on smartphones and internet data use is amazing. Almost don't need access to the content to build a profile about a person. Metadata is enough.  Metadata is what all the internet tracking is about. 

I may need to read up on privacy. I'm not 100% convinced that I have enough knowledge on the topic to really make an informed decision but I guess ignorance is bliss in my case because I use Facebook to communicate with my family and friends almost daily, since I can't always make it back to the US to see them. 


> **TheFu said:**
> Ah - babble myself off-topic again. Sorry.  The lack of privacy on the internet is an issue for me. The ruling in Belgium last week FOR Facebook to track people without their expressed opt-in was a major blow to people like me. [http://arstechnica.com/tech-policy/2016/06/facebook-wins-privacy-case-against-belgiums-data-protection-authority/](http://arstechnica.com/tech-policy/2016/06/facebook-wins-privacy-case-against-belgiums-data-protection-authority/)  I had hoped the courts would see the internet as a series of private roads where permission to spy must be requested, not as public streets for anyone with means to watch. 

Yep, I heard about that one from a podcast I listen to. Pretty disappointing how much Facebook can get away with in regards to invading the privacy of people who don't even use their services. I mean, consenting to them using your data is one thing, but even people who actively boycott them aren't able to maintain their privacy. It's a shame really.


> **TheFu said:**
> My cloud is private. There are multiple VMs running inside a network that I control. If you control the network, then you control everything. Is your ISP as trustworthy as any cloud provider?  I cannot say. Data privacy laws in the USA would say no, but data doesn't have anywhere near the same protections as POTS telecom. Cellular telecom isn't as protected either - just be aware. These laws are being re-interpreted constantly in the courts and law enforcement is doing some scary things without asking first.

I have no faith in the US gov't to respect my privacy, nor the corporations really. I've seen very little but enough to know that we have no privacy and unfortunately most people are too busy scrolling through their timelines on Facebook and sharing cat videos to care about it. I'm pretty sure using Tails Linux is about the best one can do aside from disconnecting completely or creating a private network (which would pretty much be useless). Oh well, this is the world we live in.

> **TheFu said:**
> 

[http://webhostblog.com/servers-seized-by-fbi-without-producing-evidence-or-probable-cause/](http://webhostblog.com/servers-seized-by-fbi-without-producing-evidence-or-probable-cause/)
[http://blog.instapaper.com/post/6830514157](http://blog.instapaper.com/post/6830514157)
[http://redtape.nbcnews.com/_news/2012/05/11/11647813-the-fbi-took-and-mysteriously-returned-their-server-heres-their-story?chromedomain=usnews](http://redtape.nbcnews.com/_news/2012/05/11/11647813-the-fbi-took-and-mysteriously-returned-their-server-heres-their-story?chromedomain=usnews)
[http://bits.blogs.nytimes.com/2011/06/21/f-b-i-seizes-web-servers-knocking-sites-offline/?_r=0](http://bits.blogs.nytimes.com/2011/06/21/f-b-i-seizes-web-servers-knocking-sites-offline/?_r=0)

Enjoy.  Seems I was confused into believing the USA was under rule of law, not rule of law enforcement.

I'll add these to my reading list too, thanks!

Again, I really appreciate your replies, as always I walk away with a list of things to research and question and try out, but that's what I came for. Thank you very much!

---

