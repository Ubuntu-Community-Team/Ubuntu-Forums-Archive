---
title: "Moniter My sons Computer"
date: 2012-09-26
forum: Security
---

### Post by Shmockey329 on 2012-09-26
Needless to say sons can be a pain with technology. i have parental controls set up on the router and on his computer (both of us use ubuntu 12.04 lts) but i know there are ways around those (i tried to test and there are to many ways to block it all). now without being an it expert, while being able to figure out most problems is there anyway to moniter his activity online and off with out physically logging onto it? a program i can install or something of the same genre? mostly just worried about what he gets into on my router my wife works at a bank and im an engineer so we both use vpn's on our work laptops (windows) and would like to add some security/watchdog properties to the device network. Would just like to be able to check on it every once in awhile if you know what i mean. i feel bad for using a distro developed in openness and freedom to lock him down but he is 14 and dosent need to be into stuff like he has been.

Anyhow let me know thanks in advance

---

### Post by Ubu_Fester on 2012-09-26
I am also interested in this.

---

### Post by Kinstonian on 2012-09-26
Here's something from around 2010.  [How to Create a Family Friendly Ubuntu Setup](http://www.howtogeek.com/54036/how-to-create-a-family-friendly-ubuntu-setup/)

There is also [DansGuardian](http://dansguardian.org/?page=whatisdg), although I've never used any of this.

Keeping the computer in a public place in the house is also a good idea.  A hardware keylogger might be useful too.

---

### Post by Ubu_Fester on 2012-09-26
Thanks!  I will check those out

---

### Post by Ubu_Fester on 2012-09-26
...And what about some filtering created at the router level?

---

### Post by Kinstonian on 2012-09-26
> **Ubu_Fester said:**
> ...And what about some filtering created at the router level?

Filtering with a network device is good if you want to filter traffic for a bunch of computers because you can centrally manage the filtering.  You would probably have to install something like a web proxy like Squid with a blacklist and have traffic go through that server.  So if you're dealing with a computer or two, you might be better off installing filtering software on the individual computers.

However, I'm pretty sure [OpenDNS](http://www.opendns.com/home-solutions/) has the ability to block certain sites at the DNS level.  So you wouldn't have to maintain your own server, you could just configure each computer to use an OpenDNS server.

---

### Post by 1clue on 2012-09-26
I guess we kinda need to know how computer-oriented you are, and how computer-oriented your son is.

IMO your only real control will be:
[LIST=1]
[*]Lock your cable modem in a closet.
[*]Connect a transparent proxy between the cable modem and your switch/wireless router/the rest of your internal network into a closet and hide the key.
[*]Figure out what things to monitor, and make sure everything else of interest is accounted for.
[/LIST]

IMO if you could get a lot of information from DNS.  I've never tried it so I don't know how hard it is to log requests, but here's what I would do:
[LIST=1]
[*]Lock dns down through the proxy, so that only your DNS has access through the proxy.
[*]Make that DNS server log all requests and which IP address they came from, and maybe a host name/computer name.
[*]Look at the log every now and then.
[/LIST]

To me, that would be the place to start.  If you see names that worry you then you can decide to do something else.  The thing is, many domain names are hosted on a single IP address, I know this because I had a domain name for my email and the ip address was the same as that of a porn site, both hosted by the same provider for two different clients.  I was black-listed by nearly every mail server there was because they were spamming.

So your son could be going somewhere legitimate which also happens to be hosting something not-legitimate, and you wouldn't know for sure.  But if the DNS query shows something alarming then you know.

Another thing you could do, but I don't know if you can do it with home equipment:  On Cisco switches, you can define a single ethernet port which, read-only, mirrors another port.  It's a monitor port.  I had one set up to monitor the external connection when I ran the office firewall.  Every packet going through that port was echoed to a computer on the monitor port, and from there I could see everything that went in or out of the office without any latency issues induced by a proxy.

---

### Post by Shmockey329 on 2012-09-27
so i have it locked down at the router through a couple different ways including Linksys' own parental controls. a couple of the ip addresses i have blocked but i have to keep others for certian forums and what not because of cross hosting. that article from 2010 i have some of it but not others so i think that will be a good place to start. as well as dansguardian will be. i have been watching my logs because we had a couple firewall intrusion attempts. i mean both the wifes and myselfs work computers are locked down really really well but it is a computer, and it does run windows and there are always ways around everything. as i read through logs and his web history if/when i get the chance i lock down prob a new site a week. its just bloody hard to keep up. i can leave my router in a n open place because funny enough the reset button doesnt work and its a combo unit. idk. thank you all for the suggestions they will make a huge difference im sure. 

is there still anyway to remote view his activity on his computer. like not at the same time but just a history?

---

### Post by Ubu_Fester on 2012-09-27
Thanks, this is helpful.

---

### Post by Ubu_Fester on 2012-09-27
Another question:

I think I'll need something at the router level (D-link), since we have some wi-fi devices (iTouch and Android).  ... really, a mix of a lot:  Windows PC, Ubuntu PC, etc.  Guarding against dangerous sites is time consuming -- and I've put off for too long....

Thanks All!!

---

### Post by Kinstonian on 2012-09-27
> **Shmockey329 said:**
> so i have it locked down at the router through a couple different ways including Linksys' own parental controls. a couple of the ip addresses i have blocked but i have to keep others for certian forums and what not because of cross hosting. that article from 2010 i have some of it but not others so i think that will be a good place to start. as well as dansguardian will be. i have been watching my logs because we had a couple firewall intrusion attempts. i mean both the wifes and myselfs work computers are locked down really really well but it is a computer, and it does run windows and there are always ways around everything. as i read through logs and his web history if/when i get the chance i lock down prob a new site a week. its just bloody hard to keep up. i can leave my router in a n open place because funny enough the reset button doesnt work and its a combo unit. idk. thank you all for the suggestions they will make a huge difference im sure. 

is there still anyway to remote view his activity on his computer. like not at the same time but just a history?

Are you using a blacklist?  People already make blacklists that have a bunch of "bad" sites, so much of the work is done for you...  Both DansGuardian and OpenDNS can apparently log.  However, I just looked at DansGuardian some more and apparently it's a proxy that likely should be installed on another computer.  That might be too much of a hassle.  OpenDNS would probably be a simpler way to both filter and log.  Although, the OpenDNS logs won't show you exactly which computer on your network went to a site.

---

### Post by Kinstonian on 2012-09-27
> **Ubu_Fester said:**
> Another question:

I think I'll need something at the router level (D-link), since we have some wi-fi devices (iTouch and Android).  ... really, a mix of a lot:  Windows PC, Ubuntu PC, etc.  Guarding against dangerous sites is time consuming -- and I've put off for too long....

Thanks All!!

Can you configure your router to use the OpenDNS servers?  That's as much of a "router level" as you will probably get without making your own from an old computer and Linux.  If by router level you mean network, then maybe DansGuardian would work.  Hopefully someone else who actually used it before could verify, or you could go ask them on their site. :)

---

### Post by Ubu_Fester on 2012-09-27
Here's some add'l links:

[http://internet-filter-review.toptenreviews.com/](http://internet-filter-review.toptenreviews.com/)

[http://www.consumersearch.com/parental-control-software](http://www.consumersearch.com/parental-control-software)

[http://www.safefamilies.org/parents.php](http://www.safefamilies.org/parents.php)

---

### Post by cortman on 2012-09-27
> **Shmockey329 said:**
> so i have it locked down at the router through a couple different ways including Linksys' own parental controls. a couple of the ip addresses i have blocked but i have to keep others for certian forums and what not because of cross hosting. that article from 2010 i have some of it but not others so i think that will be a good place to start. as well as dansguardian will be. i have been watching my logs because we had a couple firewall intrusion attempts. i mean both the wifes and myselfs work computers are locked down really really well but it is a computer, and it does run windows and there are always ways around everything. as i read through logs and his web history if/when i get the chance i lock down prob a new site a week. its just bloody hard to keep up. i can leave my router in a n open place because funny enough the reset button doesnt work and its a combo unit. idk. thank you all for the suggestions they will make a huge difference im sure. 

is there still anyway to remote view his activity on his computer. like not at the same time but just a history?

Check out [Net Responsibility]("http://netresponsibility.com/")- it logs ALL internet activity and emails it to your desired email address. It runs as a daemon and will alert you if ever shut down.
I use it for myself and have been quite pleased.

---

### Post by chadk5utc on 2012-09-27
Hello I have a couple suggestions to add to the list purely as options as from what Ive read most of the earlier suggestions require traffic to be routed through a single machine. These are a couple of suggestions that will need to be installed on a computer and ran on their own they are complete operating system router firewall dns dhcp and more with logs charts graphing you can see whos doing what and secure the entire network. These are based and built on Debian and can be run on older hardware so if you have an older machine your set. The first is pfsense and another is untangle both of these will do everything your looking for including routing giving you a lot more control of your network hook this up with a simple switch plug every pc into it and eliminate your existing router. I believe they can be setup for wireless AP's as well. Heres a list for more and certainly worth a look. [http://en.wikipedia.org/wiki/List_of_router_or_firewall_distributions](http://en.wikipedia.org/wiki/List_of_router_or_firewall_distributions)

---

### Post by mr-woof on 2012-09-28
Hi,

as said above in this thread, you'll need a transparent proxy between your modem/router and the internal network. I am going to recommend Smoothwall with the url filter addon installed, something along these lines:

internet --> Modem/router ..> smoothwall -> clients

You can filter what websites you can view using url filter, block IP ranges, log IM conversations, log pop3 email, you can also block what traffic can get out onto the internet, all sorts of things. It'll run on old hardware, you just need an old pc with two network cards.

Any questions/problems with the setup, ask away and I'll try my best to get you up and running.

---

### Post by el_heffe on 2012-09-29
> **1clue said:**
> I guess we kinda need to know how computer-oriented you are, and how computer-oriented your son is.

IMO your only real control will be:
[LIST=1]
[*]Lock your cable modem in a closet.
[*]Connect a transparent proxy between the cable modem and your switch/wireless router/the rest of your internal network into a closet and hide the key.
[*]Figure out what things to monitor, and make sure everything else of interest is accounted for.
[/LIST]

This.  There are still ways to get around a transparent proxy(VPN, SSH tunnel) but this will work for the lazy kids.  It does not have to be a high end computer.  I am going to be doing this with an Atom 1.6GHz with 1.5GB ram and I honestly think this is overkill.  You can even have antivirus monitor the cache to ensure no leaks of that nature get through.

There are a plethora of options available to do this with too- installing pfsense is a simple way of doing things, but I am going to go with ubuntu as it is a more familiar playground for me.  I plan to do this tonight in fact, and will be following this guide:
[http://ubuntuforums.org/showthread.php?t=926001]("http://ubuntuforums.org/showthread.php?t=926001")
Once I get the basics installed I intend to install squid and possibly follow this link:
[http://kokikode.wordpress.com/2010/03/14/configuring-squid-havpclamav-in-ubuntu-reviews/]("http://kokikode.wordpress.com/2010/03/14/configuring-squid-havpclamav-in-ubuntu-reviews/")

More to follow at a later point in time.

---

### Post by el_heffe on 2012-09-29
> **Ubu_Fester said:**
> Another question:

I think I'll need something at the router level (D-link), since we have some wi-fi devices (iTouch and Android).  ... really, a mix of a lot:  Windows PC, Ubuntu PC, etc.  Guarding against dangerous sites is time consuming -- and I've put off for too long....

Thanks All!!

If you have a wireless router, you can turn off DHCP and use one of the switch ports as a up-link port and run Ubuntu as your DHCP server.  This will utilize the routers wireless and wired ports.  Unless you have DD-WRT or tomato or some such, you cannot use the WAN port.  As I have DD-WRT I can set the WAN port as a switch port, and any device, iPad, iPhone, Kindle, can connect to the routers wireless and pull DHCP from the transparent proxy machine running Ubuntu.  Really nifty actually. 

For the sake of clarity- I am running pfsense 2.0.1 currently on my machine.  It is running HAVP, Squid, Snort and is acting not only as a transparent proxy, but also a firewall, IDS/IPS, and providing DHCP for the clients on my LAN.  I intend to replace it with Ubuntu because that is what I am familiar with and I can run other programs I want without the hassle of figuring out FreeBSD(what can I say- I am lazy)

---

### Post by Soul-Sing on 2012-09-29
Children and computers? put the computer in the living room, and limit access to it. Best way to monitor and take care of them. don't let them waste their time before a screen. period.

---

### Post by dodo3773 on 2012-09-29
@Shmockey329

Build your own router / switch / firewall and setup an isolated local vpn or something similar just for the kid. Use ip blocklists to block the stuff you want and be sure to block proxies (maybe even whole countries if you want). You need a computer with 2 ethernet ports and wireless card probably if you need wifi. You would probably be better off with going with something like pfsense or similar for all this.

---

### Post by robtygart on 2012-09-29
> **Soul-Sing said:**
> Children and computers? put the computer in the living room, and limit access to it. Best way to monitor and take care of them. don't let them waste their time before a screen. period.

+1 

I agree, if you can't keep him off those sites then its time to bring the computer out in the family room. At 14 I would have found a way around blocks and fire-walls it just takes time and Googleing.

---

### Post by MG&amp;TL on 2012-09-29
> **Soul-Sing said:**
> Children and computers? put the computer in the living room, and limit access to it. Best way to monitor and take care of them. don't let them waste their time before a screen. period.

What follows is an opinion.

As a teenager, although (mercifully) close to exiting that phase, I disagree.

The internet is a fantastic way of maturing in an environment that doesn't blame or leave permament problems. Restricting access to a computer just creates an urge to 'find out' what exists in the shadier areas of the internet that you wouldn't visit under the watchful eye of a parent. If you've got access to it, you won't feel compelled in the same way.

Things I would suggest instead.

1. Instruct them in the risks of real names and locations. Ideally, impress upon them the importance of going under an alias until they are old enough to make decisions about which parts of themselves they show online.

2. Make them aware of the laws regarding the internet. Discussion of the sentences involved (and how disappointed in them you'd be?) is the best way of discouraging dubiously legal activities.

3. Restricting time spent on a computer is a sure-fire way to make them annoyed about their lack of freedom, having just discovered a world on the internet. However, encouraging them to do something constructive at least part of the time is a good thing as it leads to more positive things for them to do on a computer.

Also, bear in mind how IT is growing. Do you really wish to have them naive about the internet in today's world? In tomorrow's world it might be the difference between a job and the employment office (not saying it will be, but it's looking more and more likely).

Just a couple of thoughts that you might like to consider before imposing a restrictive regime.

---

### Post by 1clue on 2012-10-01
+1 for instruction.

To me, block lists have never been appropriate.  First thing, they are never accurate.  There are always sites that should be on it that aren't and sites that aren't on it that should be.  Second thing, after a point your kid will either figure out one of the many ways around them, or they'll go to someone else's house and use THAT internet.

My suggestion of a transparent proxy or a monitor port was not to limit anything at all, it was so you can see what your kid is getting into so you can talk to them about it.  It's also about as high tech as most people will want to get for a home installation.

Once your kid gets over about 14 years or so, telling them what they have to do or limiting their access no longer works.  They'll just be that much more determined to do it their way.

IMO the best way to rein in your kids' behavior is to find out what they're doing and then show them the real-life risks inherent in that behavior.

---

### Post by 1clue on 2012-10-01
Actually though it might be a good place to mention a trick one of the IT guys I know did.

He was the network admin at work with 100+ people in the office, so he had hardware and a real firewall, and most importantly a real DHCP server and a real DNS server.

So what he did is change facebook.com to point to an internal office page, and linked the IP address to the specific box, and from there to the username.  The page showed 4 pieces of information:
[LIST=1]
[*]Username
[*]How many times today you tried facebook.
[*]How many times this week you tried facebook.
[*]How many times this month you tried facebook.
[/LIST]

What's funny is that the totals kept climbing.  When I saw it, it had been several months since he put it in, and his 'admin page' showed some users who evidently kept trying it dozens of times a day, all month, evidently thinking that if they kept trying it might break through somehow.  One guy had over 800 hits that month.

I have no idea if the personnel managers knew about the page, although to me it seems unlikely that someone from management wouldn't be on the list.  Misha said he hadn't heard a peep out of management, but that he had been told to block facebook.

---

### Post by Soul-Sing on 2012-10-01
I prefer internet education, and limiting access, before monitoring them. Monitoring your children makes them objects, and is reactive in many ways. I prefer a proactive attitude. the internet is part of our life, like television. but the challenge is to educate and care. Young children playing games with no time limit is imho a shame. Education is a "discours" between parents and children.
subjects:
- privacy
- content
- time limits
- etc.

---

### Post by 1clue on 2012-10-01
@Soul-Sing,

I seriously do not want to start butting heads here, but I strongly but respectfully disagree about limiting access.

If you're talking about a young child then maybe your position has some merit.  If a 6-year-old hits a porn site then it's an accident, and probably the result of him/her finding the history from some other family member.

My approach is about as proactive as it gets.  Limiting access through your network only teaches the kid that they can't do whatever they're trying from home, they have to find someplace else.  Someplace you can't control.  They will.  Preventing access can only work if you control every access point they can possibly reach, and be 100% certain of the controls being complete and legitimate.  This is right up there with using television or a video game as a babysitter in my opinion.  You can't be a parent by proxy and expect good results.  Especially if the proxy is a device.

Do you want to know who your children spend their time with?  Do you insist on knowing their friends?  Do you ask them where they're going before they leave, and what they'll be doing, and who they'll be doing it with?  Do you ask your kids about drugs?  A passive monitor is exactly the same thing.  Let them know you're doing it and that you care.

Frankly I've been using a passive monitor for years, even though I'm the only one who should have been using my it for most of those years.  If nothing else, it helps me figure out if my network security is adequate.  I've been unpleasantly surprised.

I'm in no way saying you should keep the existence of monitoring a secret, or that you should stalk them on facebook.  I'm saying you should get an idea what your kids are doing, which you have both a right and a responsibility(both legal and moral) to do.  I'm saying you should monitor what your network is used for, which is your right and your legal responsibility.  I'm saying you should watch what your kids do so you have some hope of influencing their decisions in a constructive way.

I've seen a lot of conservative, ultra-moral friends raise their kids with the iron fist you mention, denying kids the privilege of choosing their activities altogether because they might make the wrong decisions or be exposed to some immoral predator.  They're told the answers to life's Big Mysteries based on their parents' experience, believing they know what they need by the time they become adults.  Most of those kids that I personally knew wound up going crazy when they went to college or moved out into the Big Bad World.  Drugs, STDs, unwed pregnancy and the whole bit.  They had all sorts of theoretical advice but no experience making small mistakes when the parents were watching.

I'm not talking about overall statistics here, I'm thinking of a few families I personally know.  Parents can't anticipate everything their kids are exposed to, they can only see where their kids are going and help guide their decisions so that future decisions are not destructive.  Especially once they become teenagers.

---

### Post by Soul-Sing on 2012-10-01
> I've seen a lot of conservative, ultra-moral friends raise their kids with the iron fist you mention, denying kids the privilege of choosing their activities altogether because they might make the wrong decisions or be exposed to some immoral predator. 

really? iron fist? denying kids the privilege of choosing their activities?
the outcome with my adult children?
- they are critical/assertive users of the world wide web
- they are using Linux :)
- they limit their internet time. because their busy with other things.
- their non conformists avant la lettre

don't put me and them in the corner of conservatism, please.

---

### Post by 1clue on 2012-10-01
Dude, I'm sorry for calling you a conservative!  :)

Seriously, I wasn't thinking you were, but the several families I referred to definitely were conservative.

And I'm also not saying unrestricted access, kids should get outside and find some real-world activity to take the majority of their time.

What I'm saying should be unrestricted is the places they go on the net, at least after they're teenagers.  You should be able to see what interests them.  You should know what to talk about when that uncomfortable talk session comes up.

FWIW I remember several of those uncomfortable talks as a kid, made more uncomfortable because my parents weren't even on the same planet I was on.  The one about drugs was particularly painful because I had already been exposed to that by my peers and already made the decision that I didn't want anything to do with them, and my dad went on and on about it as though I were hiding something.

---

### Post by robtygart on 2012-10-01
I really don't see the problem with leaving the Internet as is and just keeping the computer in the open. 

A 14 year old does not need to be alone in his room looking at naughty sites, your brain is a computer and you need to watch how you program it. 

If he has something better to do with the Internet maybe he will have a better time staying off those sites.

---

### Post by a2j on 2012-10-02
> **Soul-Sing said:**
> Children and computers? put the computer in the living room, and limit access to it. Best way to monitor and take care of them. don't let them waste their time before a screen. period.

As a parent, I'd agree here.

DansGuardian works.

---

### Post by Stonecold1995 on 2012-10-03
> **mg&tl said:**
> what follows is an opinion.

As a teenager, although (mercifully) close to exiting that phase, i disagree.

The internet is a fantastic way of maturing in an environment that doesn't blame or leave permament problems. Restricting access to a computer just creates an urge to 'find out' what exists in the shadier areas of the internet that you wouldn't visit under the watchful eye of a parent. If you've got access to it, you won't feel compelled in the same way.

Things i would suggest instead.

1. Instruct them in the risks of real names and locations. Ideally, impress upon them the importance of going under an alias until they are old enough to make decisions about which parts of themselves they show online.

2. Make them aware of the laws regarding the internet. Discussion of the sentences involved (and how disappointed in them you'd be?) is the best way of discouraging dubiously legal activities.

3. Restricting time spent on a computer is a sure-fire way to make them annoyed about their lack of freedom, having just discovered a world on the internet. However, encouraging them to do something constructive at least part of the time is a good thing as it leads to more positive things for them to do on a computer.

Also, bear in mind how it is growing. Do you really wish to have them naive about the internet in today's world? In tomorrow's world it might be the difference between a job and the employment office (not saying it will be, but it's looking more and more likely).

Just a couple of thoughts that you might like to consider before imposing a restrictive regime.

**BIG +1 here**

---

### Post by samiux on 2012-10-23
In my opinion, your kids can go to other places (such as internet cafe or classmates home), which have internet access, to go to the sites that you banned/disallowed at home with some kind of methods/softwares.

I think it is the most important to teach your kids the following when they are accessing the internet :

(1) don't use real name and real personal information in any place in the internet, such as forums, instant messengers and etc.

(2) don't reveal any real information of them including address of home, name of school and family details as well as their friends.  Moreover, don't talk about where they often go and etc.

(3) don't talk to any strangers even they claimed that they are kids or teenagers.  If need to, do (1) & (2) above.

(4) don't go to the porn sites as they are not designed for their age.  Tell them they will be allowed to be there when they are matured.

In addtion, I would suggest to install/implement an Unified Threat Management System (UTM) to your network at home.  The open source UTM that I would suggest is [Untangle]("http://www.untangle.com/").  It can block/ban some sites according to your desire.

If you really want to monitor their activity in the internet, I would also suggest to install [TeamViewer]("http://www.teamviewer.com/en/index.aspx") which can see the desktop of your kids remotely.  However, your kids will be noticed.

Samiux

---

