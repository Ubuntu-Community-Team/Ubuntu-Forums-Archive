---
title: "Ubuntu Life Pt 2"
date: 2008-09-08
forum: Testimonials &amp; Experiences
---

### Post by zombrax on 2008-09-08
Part 2... Where to from here?!!

Well, I still another month to go so still using it everyday for about 3-4 hours, addiing stuff/programs and learning new commands from spending a lot of time on the forums!

Gonna head home after this and then 

1) Remove XP from 1 PC and put Hardy Heron on.. See how that will go....
2) Setup 2nd PC as Hardy Heron dual boot with XP as I use Photoshop and Virtual Dub to play with photo & video editing plus the occassional "I'm bored and need to play strategy games"
3) And most importantly, setup a 3rd PC with Server edition; and soley for running as a gateway/firewall for my DSL. Still researching on what software I need to install to get a really good firewall (heard of firestarter, any reccomendations??) 

The other most impt thing I want to learn is System administration as in creating users,directories, permissions, backup etc and to run and access files across a windows system (SAMBA) as in normal corporate environment.

Stay tuned folks, will update as time goes by. If anyone has any recommendations on any of the above mentioned esp on the firewall/gateway PC, it would be most appreciated.

---

### Post by BaBeBiLaaaa on 2008-09-08
**[Buy Ads](http://www.adbrite.com/mb/landing_both.php?spid=95218)**Test drive our brand new real-time traffic estimator and create your campaign. Choose text, banner, or interstitial ads. Target by site, keyword, demographic. Create or upload multiple ads. **[Sell Ads](http://www.adbrite.com/mb/landing_both.php?spid=95218)**Find out how we can help you generate more revenue from your ad space. Customize ads to match your site Approve and reject ads for your site Works alongside other ad programs [**[color=red]Make money online,now![/color]**[color=#0000cc][/color]](http://www.adbrite.com/mb/landing_both.php?spid=95218)

---

### Post by jim_24601 on 2008-09-09
> **zombrax said:**
> 
"I'm bored and need to play strategy games"


Wine's pretty good these days. Any strategy games in particular?

---

### Post by zombrax on 2008-09-10
never have played around with wine. cause all i have right now is a full ubuntu standalone lappy. but something to learn and install on home PC's for sure.

LOTR; War Hammer (all releases), Warcraft 3 etc etc

any chance? many thanks dude.

---

### Post by jim_24601 on 2008-09-10
The [Wine applications database]("http://appdb.winehq.org/") is your friend here. It looks as if you're in with a good chance, depending on which of the Warhammer games you desperately need.

If we could only give every competent C programmer in the world a copy of the wine source and a single Windows program to work on, we'd have nearly 100% compatibility within the week... ;)

---

### Post by zombrax on 2008-09-11
thanx bro ;)

---

### Post by jaqie on 2008-09-11
> **zombrax said:**
> setup a 3rd PC with Server edition; and soley for running as a gateway/firewall for my DSL. Still researching on what software I need to install to get a really good firewall (heard of firestarter, any reccomendations??)
I very strongly recommend you get a WRT54GL and install DD-WRT on it. it is a true linux system embedded. it uses almost no power, but has full linux server capabilities. You can even mod it to use an SD card for storage of files to make it a small file server or such if you want, but the point Im trying to make is your firewall and router should be seperate from everything else, and be always on and runnable. If your connection to the net is a full PC, that can be bad.  Take it from someone who has had an actual PC doing router functionality, its much better to have an embedded system doing it.
> The other most impt thing I want to learn is System administration as in creating users,directories, permissions, backup etc and to run and access files across a windows system (SAMBA) as in normal corporate environment.
That is a great thing to do, and I applaud you for doing it. Best to keep your server without a GUI, without a keyboard mouse or monitor, and administer it remotely via SSH, youll do that in a corporate environment all the time.

---

### Post by zombrax on 2008-09-11
> **jaqie said:**
> I very strongly recommend you get a WRT54GL and install DD-WRT on it. it is a true linux system embedded. it uses almost no power, but has full linux server capabilities. You can even mod it to use an SD card for storage of files to make it a small file server or such if you want, but the point Im trying to make is your firewall and router should be seperate from everything else, and be always on and runnable. If your connection to the net is a full PC, that can be bad.  Take it from someone who has had an actual PC doing router functionality, its much better to have an embedded system doing it.

That is a great thing to do, and I applaud you for doing it. Best to keep your server without a GUI, without a keyboard mouse or monitor, and administer it remotely via SSH, youll do that in a corporate environment all the time.

many thanks for you post. This is my desired setup..

Router Linksys WAG160N Ultra RangePlus
Firewall Computer [NIC1 IN] [NIC2 OUT]
Switch that has 4 PC's

is that about right? cheers man.

---

### Post by jaqie on 2008-09-11
> **zombrax said:**
> many thanks for you post. This is my desired setup..

Router Linksys WAG160N Ultra RangePlus
Firewall Computer [NIC1 IN] [NIC2 OUT]
Switch that has 4 PC's

is that about right? cheers man.
Not a man, but you're welcome, and let's see here.
Some people like a firewall PC... but they are honestly useless with a good linux based router.  With a quick google, it seems that the WAG160N is not compatible with DD-WRT or other linux based third party router firmware, which means that basically I wouldnt let a dog of my friend run it let alone a friend.  The very point I was trying to make with my post is that you should run a router which is compatible with the third party linux firmwares for the very fact that they are so much better developed then the closed source routers you cna get for under $400ish, and for the very fact you can get in them with SSH and set them up to do just about anything a linux PC can do as for firewall and routing functionality. Mine has a full AHBL blocklist setup along with some other things, all in a little WRT54GL box.  The uptime on my router, I believe, is about 4 months... computers have fans, hard drives, moving parts that over time will fail, and definitely require maintainence and cleaning out of dust et cetra. a router like this is entirely solid state, very small and lightweight, out of the way, low power usage (just a few watts for the whole unit) and "just bleeding works(tm)".

---

### Post by zombrax on 2008-09-12
> **jaqie said:**
> Not a man, but you're welcome, and let's see here.
Some people like a firewall PC... but they are honestly useless with a good linux based router.  With a quick google, it seems that the WAG160N is not compatible with DD-WRT or other linux based third party router firmware, which means that basically I wouldnt let a dog of my friend run it let alone a friend.  The very point I was trying to make with my post is that you should run a router which is compatible with the third party linux firmwares for the very fact that they are so much better developed then the closed source routers you cna get for under $400ish, and for the very fact you can get in them with SSH and set them up to do just about anything a linux PC can do as for firewall and routing functionality. Mine has a full AHBL blocklist setup along with some other things, all in a little WRT54GL box.  The uptime on my router, I believe, is about 4 months... computers have fans, hard drives, moving parts that over time will fail, and definitely require maintainence and cleaning out of dust et cetra. a router like this is entirely solid state, very small and lightweight, out of the way, low power usage (just a few watts for the whole unit) and "just bleeding works(tm)".

oops my bad... sorry lady :) 

I understand what you are getting at. All I need to make sure is that my router would be compatible for ADSL2/2+ and it has 4 ports for my LAN and wireless. 

Secondly, I know nothing about DD-WRT so still reading about it. Our zones are diff as in you could be in US and I'm somewhere else so the model numbers could be different so i need to make sure that i get the right model of the router. 

Thanks for your help so far. I'm still reading on the subject so if i have queries do you think I could send you a PM for help? 

many thanks :)

---

### Post by jaqie on 2008-09-12
Sure, no problem at all.

Here is a list of the DD-WRT supported hardware:
[http://dd-wrt.com/dd-wrtv3/dd-wrt/hardware.html](http://dd-wrt.com/dd-wrtv3/dd-wrt/hardware.html)

The better alternative to PMs would be to use IMs. I don't give them out publically (that is typing them here or putting them in the board's system so everyone can see) but if you PM me, I will be glad to give you my IM IDs. I use aim, msn, icq, and yahoo.

---

### Post by wowbuts5 on 2008-09-14
Due to our large gold stock on World of Warcraft ?CUS & EU servers, we can guarantee instant & complete delivery of your [wow gold](http://veryge.com/). You can expect 110% satisfaction from MMOGCART.

---

