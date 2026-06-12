---
title: "Blocking Adult Material"
date: 2009-02-06
forum: Security
---

### Post by frozenfire0808 on 2009-02-06
Are there any free programs that can stop kids from seeing adult material online?

---

### Post by hyper_ch on 2009-02-06
IMHO best shot would be to use OpenDNS

---

### Post by Dr Small on 2009-02-06
Depending on your situation and network setup, you can use OpenDNS as hyper_ch recommended, or if you can dedicate a box as either a firewall or just a server, you can install DansGuardian and Squid on it and have all the clients redirect port 80 to Privoxy which will proxy everything to DansGuardian -> Squid and out to the internet.

I use this method, and it works very well for me. Here was the thread that I made about it. [http://ubuntuforums.org/showthread.php?t=1038761](http://ubuntuforums.org/showthread.php?t=1038761)

---

### Post by treymul on 2009-02-06
I use a simple firefox addon, foxfilter.  Its not perfect and can be bypassed fairly easily, but my kids are young and it prevents any accidental typos from causing problems.

---

### Post by donkyhotay on 2009-02-06
Dansguardian is probably what you're looking for. Be aware that in my experience no form of 'internet babysitter' does anything worthwhile, especially when kids are involved. Someone that doesn't want to see porn will avoid sites that have it and should avoid sites that probably will have it (like places that offer crackz and warez) and the false positives get annoying. On the other hand if someone *does* want to see porn then they'll find a way to bypass any security setup and do so. I've seen many a parent think since they have net nanny or something similar their kids can't view objectionable content but the average kid is *way* more tech savvy then the average parent. I've seen a 3 year old that could launch starwars battlefront on his own and play well enough to hold his own against average bots (admittedly his parents *are* hardcore gamers that used to play it in front of him quite a bit). I was reading and editing source code on my C64 when I was about 6 or 7 and figured out how to modify some of it to 'cheat' at some games. I know 8 year olds fully capable of modifying proxy and firewall settings to perform basic network troubleshooting. Remember, no matter what security you put on your computers a simple liveCD will bypass all of it instantly (except for maybe file encryption). If you are wanting to protect your own kids my recommendation would be to keep the computers in a public area and keep a visible eye on what they do when on it.

---

### Post by Dr Small on 2009-02-07
> **donkyhotay said:**
> On the other hand if someone *does* want to see porn then they'll find a way to bypass any security setup and do so. [...] 

I know 8 year olds fully capable of modifying proxy and firewall settings to perform basic network troubleshooting. Remember, no matter what security you put on your computers a simple liveCD will bypass all of it instantly (except for maybe file encryption). [...]



If you are routing all connections through a firewall server that is redirecting all traffic through iptables and then to DansGuardian or whatever filter, then how would someone bypass that? There is no means of changing proxy settings on client machines, as everything must pass through the firewall-filter first. And a LiveCD would still have to connect through the firewall to reach the internet.

---

### Post by kevdog on 2009-02-07
Dr. Small

Writing that up as a formal tutorial would be great!!! Good stuff on that page -- things I don't know about.

---

### Post by knipknup on 2009-02-07
I installed suricate, which is a firefox addon.  So far it has been fine.

---

### Post by rileinc on 2009-02-08
> **hyper_ch said:**
> IMHO best shot would be to use OpenDNS+1 on OpenDNS. 
Aside from blocking porn sites, it can also block hateful sites, advertisement, phishing/typosquatting sites, and many more.

---

### Post by warp99 on 2009-02-08
Dansguardian, tiny proxy, and iptables is most likely the way to go. I have three children between the ages of 8 and 6 so it's mandatory there's a strong filter on the network. Basically with Dansguardian I blacklist everything and whitelist what I feel is appropriate. It's a professional filtering program with varies log levels and add-on virus scanning. 

It's pretty easy to set up and with iptables you can filter on a per user basis so me and my wife can surf uninhibited while the kids are filtered. Once you do this just take normal precautions on securing systems (use bios and grub passwords, boot to hard drive only, use case locks, etc.) on the host machine and everything will be locked down pretty tight.

---

### Post by Dr Small on 2009-02-08
> **kevdog said:**
> Dr. Small

Writing that up as a formal tutorial would be great!!! Good stuff on that page -- things I don't know about.
Thanks. I'll think about it sometime :)

---

### Post by kevdog on 2009-02-08
> **Dr Small said:**
> Thanks. I'll think about it sometime :)

Great -- If you are anything like me, that means its going to be awhile!

---

### Post by brainac0cult on 2009-02-10
why would you want to BLOCK adult content! lol
just kiddin'. try opendns

---

### Post by ushills on 2009-02-10
If using firefox you can install the add-on procon latte.

It does whitelist, blacklist, bad-words etc.  I use it in conjuntion with opendns to refine filtering for individual users.

---

### Post by donkyhotay on 2009-02-10
> **Dr Small said:**
> If you are routing all connections through a firewall server that is redirecting all traffic through iptables and then to DansGuardian or whatever filter, then how would someone bypass that? There is no means of changing proxy settings on client machines, as everything must pass through the firewall-filter first. And a LiveCD would still have to connect through the firewall to reach the internet.

If you have a dedicated firewall server thats one thing, but most personal users I've seen set this type of thing up have the client function as the proxy server as well (don't know about openDNS as I've never used it, I have set up dansguardian for a friend of mine though). Most instructions on setting up dansguardian assume this is what you're doing. If the client is also the proxy then a liveCD goes right around it. Now if he has the time and ability to create a dedicated proxy server on a seperate machine then so long as access to the server is restricted, the liveCD won't work. Even though that is a way to fix the workaround I described I still think my initial point is valid that no type of filtering is 100% effective and the best solution to this type of problem is to keep an eye on what your kids are doing while online.

---

### Post by warp99 on 2009-02-10
> **donkyhotay said:**
> If you have a dedicated firewall server thats one thing, but most personal users I've seen set this type of thing up have the client function as the proxy server as well (don't know about openDNS as I've never used it, I have set up dansguardian for a friend of mine though). Most instructions on setting up dansguardian assume this is what you're doing. If the client is also the proxy then a liveCD goes right around it. Now if he has the time and ability to create a dedicated proxy server on a seperate machine then so long as access to the server is restricted, the liveCD won't work. Even though that is a way to fix the workaround I described I still think my initial point is valid that no type of filtering is 100% effective and the best solution to this type of problem is to keep an eye on what your kids are doing while online.

You don't need a dedicated machine to install Dansguardian. I've had this setup in the past on a single machine and it works fine. As for keeping an eye on what my kids are doing there's a log file that I routinely grep for any sites I feel are inappropriate that the filter may have missed somehow. I have no problems with my children surfing the internet unattended which they frequently do.

As for using a LiveCD password protect the BIOS, turn off boot to CD-Rom, and lock the case so they can't reset the BIOS. Set grub passwords to prevent boot to recovery mode. Now the machine is locked down tight at this point. The only way you're going to bypass the filter is by pulling the cat5 cable out of the modem or router, then having one of your kids friends plug it into his or her notebook. That's really what you need to be looking out for.

Edit:

There is one way to by-pass the filters if you have a virtual machine set to bridged networking. They could use that to boot to an ISO and by-pass the proxy filters, so during setup have VMware or VirtualBox set to NAT only.

Remember, we were all children at one time. You just have to reach back to a time when your raging hormones and devious mind was running rampant and ask yourself how would you bypass the system?

---

### Post by Dr Small on 2009-02-10
> **warp99 said:**
> You don't need a dedicated machine to install Dansguardian. I've had this setup in the past on a single machine and it works fine. As for keeping an eye on what my kids are doing there's a log file that I routinely grep for any sites I feel are inappropriate that the filter may have missed somehow. I have no problems with my children surfing the internet unattended which they frequently do.

As for using a LiveCD password protect the BIOS, turn off boot to CD-Rom, and lock the case so they can't reset the BIOS. Set grub passwords to prevent boot to recovery mode. Now the machine is locked down tight at this point. The only way you're going to bypass the filter is by pulling the cat5 cable out of the modem or router, then having one of your kids friends plug it into his or her notebook. That's really what you need to be looking out for.
Yeah, that will work, so long as you're not on a network. Then you have to do this to every system on the network. I still think it would be more secure and less of a hassle if there was some box between the router and modem that filtered all the traffic.

---

### Post by warp99 on 2009-02-10
> **Dr Small said:**
> I still think it would be more secure and less of a hassle if there was some box between the router and modem that filtered all the traffic.

You're absolutely correct, but if you have only one machine then this shouldn't be a problem.  Even then if the kids are smart they will reset the router or modem to gain access anyway for a by-pass, so physical access to the equipment should be restricted.

When my kids get a little older my server, router, and modem is basically going into a cage in the basement. I'm not going to be the parent that gets called up by other parents saying there kids were surfing porn at my house. Sorry, that's not going to happen.

---

### Post by donkyhotay on 2009-02-10
> **warp99 said:**
> Remember, we were all children at one time. You just have to reach back to a time when your raging hormones and devious mind was running rampant and ask yourself how would you bypass the system?

Thats my point, you have to focus exclusively on how you can bypass the system but even when you can't think of any further weaknesses doesn't mean they won't. For the people that mention having a seperate proxy filter thats kept under lock and key will keep you safe then what happens if they attach a WiFi card and connect through the neighbors internet? Sure you can come up with a solution to my proposed work around but it becomes a never-ending arms race that can't be won! These tools often give parents a false sense of security that *doesn't* exist. You can lock down the system and make it difficult to use but there are no guarantees especially when someone has physical access to the machine. The only truly effective 'filter' is (as I mentioned before) keeping your computer in a public area (living room type location) and keep an eye on what they're doing.

---

### Post by warp99 on 2009-02-10
> **donkyhotay said:**
>  The only truly effective 'filter' is (as I mentioned before) keeping your computer in a public area (living room type location) and keep an eye on what they're doing.

I'm sorry unless you're in the living room 24 hours a day this isn't going to do anything in the least bit. My children already know that I log pretty much everything they do, so the chances of them by-passing the filters without my knowledge is slim to none.

Besides it's not my computers I'm worried about being by-passed, it's their friends that don't have a technically knowledgeable parent logging and checking their usage. If your too intrusive looking over their shoulders all of the time you can pretty much guess who's computer they're going to use.

---

### Post by Dr Small on 2009-02-10
> **donkyhotay said:**
> Thats my point, you have to focus exclusively on how you can bypass the system but even when you can't think of any further weaknesses doesn't mean they won't. 
That's my job. To think of how to bypass security, and then fill the gaps.

> **donkyhotay said:**
> 
For the people that mention having a seperate proxy filter thats kept under lock and key will keep you safe then what happens if they attach a WiFi card and connect through the neighbors internet? 
These situations have to be thoroughly thought out. For people living in an apartment complex, yes, this is most likely impossible to defeat. But not everyone lives in an apartment complex. The nearest wireless networks where I live are completely out of range.

---

### Post by warp99 on 2009-02-11
> **Dr Small said:**
> These situations have to be thoroughly thought out. For people living in an apartment complex, yes, this is most likely impossible to defeat. But not everyone lives in an apartment complex. The nearest wireless networks where I live are completely out of range.

Every situation is different. I live in an town house complex with about 20-30 houses with four apartments to a unit. When I do a wireless scan about 10-15 networks show up in WICD. In every single case they all have WPA encryption enabled. There are no WEP networks that I could see and the area is densely populated. Once of the reasons that I attribute this is because many of the tenants are either college students or young professionals so they seem comfortable with the technology. 

This is in stark contrast to the working class neighborhood when I lived in Des Moines. In Des Moines most of the networks were either open or WEP. I could roam around the house and pick up at least 3 or 4 open networks very easy.

---

### Post by donkyhotay on 2009-02-11
> **warp99 said:**
> I'm sorry unless you're in the living room 24 hours a day this isn't going to do anything in the least bit. My children already know that I log pretty much everything they do, so the chances of them by-passing the filters without my knowledge is slim to none.

Besides it's not my computers I'm worried about being by-passed, it's their friends that don't have a technically knowledgeable parent logging and checking their usage. If your too intrusive looking over their shoulders all of the time you can pretty much guess who's computer they're going to use.

Yet another (pretty obvious) way of bypassing a filter. My point in this thread has always been you can't trust technology completely with this type of issue and you need to teach them the values you want beforehand then put your trust in them. If they really want to bypass a filter then they *will* do so. When I say 'watch what they do on the computer' I don't mean stand over their shoulder 24/7 but try to be aware of what they are doing. Treat it like television. Chances are there are certain shows/movies you don't want them to watch just like there are certain places on the internet you don't want them to go, and while you probably don't stand there and watch every show they watch with them; with the television in a public place (for most families) you are probably aware of what shows they watch in general and turn it off if it's something you don't approve of.

---

### Post by warp99 on 2009-02-11
> **donkyhotay said:**
>  ... you are probably aware of what shows they watch in general and turn it off if it's something you don't approve of.

Actually I know every single show they watch since I also have a MythTV server, running Mythbuntu of course. Basically all media coming into my house is logged and monitored be it internet or television. I'm well aware of what my children view since I normally ask them and they show me, no problems there.

You should have seen the look on my daughters face when I asked here about a site she went that the filter missed. It wasn't obscene, but not appropriate for her age. I basically told her that you have a lot freedom with the computer, but I know exactly where you go and what you look at so don't try anything "stupid" because it's real easy to catch you.

No argument, no drama, nothing of the sort. It's much less intrusive and she still feels that she has some privacy when on the computer. You pull the reins too tight and they will go somewhere else where I have no control over the content and have to rely on someone else that may not be as diligent as me.

---

### Post by x3roconf on 2009-02-13
adult material sucks :lolflag:

---

### Post by ooobooontooo on 2009-02-13
Lol. Everything donkyhotay has said has kind of been like the story of my life. My dad put up a whole bunch of filters and stuff and I got through them (not to watch adult material of course :P), and then he would discover I got through them. Then he put new ones and I got through those, but in the end it did teach me a ton about network and security.
Anyway, the advice so far has been good, set some sort of filter and log sites. But the best choice, as donkyhotay said, would probably be to put the computer in the living room with the screen facing you. That way the kid has no chance to do anything he feels is bad because he knows you're watching him. However as warp99 mentioned that might bring up privacy issues. If that's the case, you could try facing the screen the other way. That way the kid still feels self-conscious about going to "bad" sites because you're still in the same room, but he still feels like he has a bit freedom...at least from my experiences....

---

