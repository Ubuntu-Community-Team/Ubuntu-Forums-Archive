---
title: "Who uses OpenDNS?  What is it for?"
date: 2008-11-24
forum: The Cafe
---

### Post by Athanasius on 2008-11-24
Somebody tossed a link my way [http://www.opendns.com/]("http://www.opendns.com/").  Can somebody explain, in layman's terms, what it is for?  One thing I want to do is to be able to access my computer via ssh from another computer (not on the same network - or for that matter, in the same state).  I think this has something to do with making me able to do that...

---

### Post by uknowho008 on 2008-11-24
I don't know if OpenDNS keeps track of you dynamic ip address like you want. But what I use it for is to connect to websites faster. There servers are faster than comcast so it just makes resolving domain names to IP addresses quicker.

---

### Post by klange on 2008-11-24
It's an alternative DNS service that's probably faster than your ISPs due to their caching methods, updates faster, and is supposed to be more secure.

I use it, primarily because my ISP flushes and resets their DNS servers what seems to be every night at 9:00PM, which yields a broken Internet for me.


What you want to do has nothing to do with OpenDNS.

---

### Post by nightmare0 on 2008-11-24
If you want to be able to access your computer via SSH or host a site through Apache, then stick with DynDNS or No-IP. They both offer dynamic updates, so when your IP Address changes their DNS servers update too. They also give you a free subdomain to access your computer. blah blah blah. If you need more info just ask!

---

### Post by Prefix100 on 2008-11-24
A DNS replaces your IP with a memorable word adress.

FreeDNS or OpenDNS is a service that gives you a free DNS so that you don't pay to change you IP into words.

However, it won't be much use to you if you don't have the auto-update IP programs for the service installed, because the DNS needs to be updated with a new IP every time your IP changes ( which is more than likely with a normal ISP ).

---

### Post by Skripka on 2008-11-24
> **WindowsSucks said:**
> It's an alternative DNS service that's probably faster than your ISPs due to their caching methods, updates faster, and is supposed to be more secure.

I use it, primarily because my ISP flushes and resets their DNS servers what seems to be every night at 9:00PM, which yields a broken Internet for me.


What you want to do has nothing to do with OpenDNS.

I use OpenDNS because quite frankly, 10000 monkeys typing into GNU eMacs would make a better DNS than the DNS of my ISP.

---

### Post by handy on 2008-11-24
> **WindowsSucks said:**
> 
It's an alternative DNS service that's probably faster than your ISPs due to their caching methods, updates faster, and is supposed to be more secure. 

I use it, primarily because my ISP flushes and resets their DNS servers what seems to be every night at 9:00PM, which yields a broken Internet for me.

Yes, that is why I used to use OpenDNS, though I have had a different ISP for well over a year now & use them as my DNS. 

For what they do do, OpenDNS do it well.

> **WindowsSucks said:**
> 
What you want to do has nothing to do with OpenDNS.

To the OP, the above is absolutely true.

---

### Post by Athanasius on 2008-11-24
Sounds good.  I will give it a try.  There seems to be good web filtering options, it is probably just dansguardian.  If it works then I don't have to run it from my own computer.

---

### Post by Dr Small on 2008-11-24
> **Athanasius said:**
> Sounds good.  I will give it a try.  There seems to be good web filtering options, it is probably just dansguardian.  If it works then I don't have to run it from my own computer.
Actually, OpenDNS's filtering is based on domain names and user submitted ones that have been flagged for a certain category. You can filter certain categories, and any domain that is flagged in that category will be denied.

---

### Post by stmiller on 2008-11-25
OpenDNS is great! You can set it up in your router. That is the best way to do it. Then your entire network will use it without having to make any changes on your computers or devices.

It is quite fast. Web page addresses resolve faster and your entire internet experience is faster than your isp's dns servers.

---

### Post by Sealbhach on 2008-11-25
I use it. I find it faster.


.

---

### Post by blueturtl on 2008-11-25
OpenDNS can also be used to circumvent stupid government policy.
Here in Finland we're having web censorship shoved down our throats by blocklists handed to ISPs from government officials/police. The supposed intent is to block child pornography while it has already been found that the blocklists are used to filter out other content as well. One such page was simply a public site that was critizising the blocklist approach and web censorship. So if you live in a country such as China or Finland or possibly one of the former soviet nations -- why not USA today actually -- OpenDNS is your friend if you wish to reach all of web and not just the slice the officials want you to see.

---

### Post by cyberfin on 2008-11-25
Stunningly enough, I found OpenDNS to be slower than my isp's DNS'.

Then again my isp is in the top 5 of Spain's providers. Anyway, what I did find interesting and might be a future option in my houselhold, is that you can filter browsing and setup family filters.

When my daughter grows up to computer age, I will probably use it to setup appropriate filters.

---

### Post by Izek on 2008-11-25
I didn't notice a performance increase much. In fact, I had troubles getting to certain sites after switching to openDNS. So I switched it back to auto, and everything worked better.

---

### Post by Dr Small on 2008-11-25
> **stmiller said:**
> OpenDNS is great! You can set it up in your router. That is the best way to do it. Then your entire network will use it without having to make any changes on your computers or devices.

I wish I could do that. Unfortunately, my router doesn't support this.

---

### Post by geoken on 2008-11-25
> **Prefix100 said:**
> 

However, it won't be much use to you if you don't have the auto-update IP programs for the service installed, because the DNS needs to be updated with a new IP every time your IP changes ( which is more than likely with a normal ISP ).

Many routers can do that. My netgear, for example, has a section where I can enter my DynDNS account info and it will update my IP every time the router detects it has been changed.

---

### Post by doorknob60 on 2008-11-25
I use it because my parents won't l;et me have a computer in my room if it doesn't have parental controls, and OPenDNS provides parental controls and you can "install" (can't think of a better word than that) it to your router and it's free. Also websites do seem to load a little faster, but it might eb just me.

---

### Post by smartboyathome on 2008-11-25
I use OpenDNS at my house because Comcast's DNS isn't very good. This at least gives me some features, versus the bare minimum from Comcast.

---

### Post by Kernel Sanders on 2008-11-25
Just tried this. Epic win. OpenDNS FTW! Internet speed FTW!

---

### Post by bobbocanfly on 2008-11-25
I used to use openDNS but didn't like how it took over the DNS error pages. By default (at least for me) if i type in something like "ubuntu forums" it will do a google "I'm Feeling Lucky" and most of the time land me on the correct page. With OpenDNS it would just direct me to a dodgy OpenDNS search page with not very good results. If there was a way round that, I'd definately start using OpenDNS again.

---

### Post by Tristam Green on 2008-11-25
I use OpenDNS simply because of one event that occurred last year:  AT&T/Bellsouth ISP outage across an entire day for most of the Eastern Seaboard of the US because of a DNS outage.  Been with OpenDNS since, and had no problems at all.

---

### Post by lifestream on 2008-11-25
> **bobbocanfly said:**
>  With OpenDNS it would just direct me to a dodgy OpenDNS search page with not very good results. If there was a way round that, I'd definately start using OpenDNS again.

There is, you just go to your OpenDNS account page, and turn that off.
That's one of the reasons why I use openDNS.
Another reason is that I do Web development, and buy/transfer a lot of websites. With OpenDNS, I don't have to wait 24 hours et al, to have my website working.

---

### Post by lswest on 2008-11-25
> **lifestream said:**
> There is, you just go to your OpenDNS account page, and turn that off.
That's one of the reasons why I use openDNS.
Another reason is that I do Web development, and buy/transfer a lot of websites. With OpenDNS, I don't have to wait 24 hours et al, to have my website working.

To be clearer, it's the auto-correction of typoes in the URL bar that's what you need to disable.  Under the advanced configuration options of the Settings menu.

---

### Post by bobbocanfly on 2008-11-25
> **lswest said:**
> To be clearer, it's the auto-correction of typoes in the URL bar that's what you need to disable.  Under the advanced configuration options of the Settings menu.

Thanks thats fixed the problem I was having!

---

### Post by lswest on 2008-11-25
> **bobbocanfly said:**
> Thanks thats fixed the problem I was having!

No worries, spent some time figuring it out myself after I read your post :P

---

### Post by bkaplan on 2008-12-05
I'm having a strange issue with opendns:  I configured it on my Westell dsl router.  Internet works fine across my network (peer to peer, mixed ubuntu/XP boxes, mixed wired and wireless); however, the opendns configuration prevents my samba shares from being accessed anywhere on the network or from the host machines themselves.  When I go back to my ISP's dns addresses, both internet and samba shares work fine across the entire network.  I'm guessing it is some kind of loopback issue with opendns routing, but I'm not able to figure it out.

I'm pulling my hair out ... any ideas for a fix?

---

### Post by timzak on 2009-09-07
> **bkaplan said:**
> I'm having a strange issue with opendns:  I configured it on my Westell dsl router.  Internet works fine across my network (peer to peer, mixed ubuntu/XP boxes, mixed wired and wireless); however, the opendns configuration prevents my samba shares from being accessed anywhere on the network or from the host machines themselves.  When I go back to my ISP's dns addresses, both internet and samba shares work fine across the entire network.  I'm guessing it is some kind of loopback issue with opendns routing, but I'm not able to figure it out.

I'm pulling my hair out ... any ideas for a fix?

Did you ever find a solution?  I'm trying out opendns and just noticed the same issue.

---

### Post by cariboo on 2009-09-07
If you have a problem with Samba and DNS please ask the question in the correct forum, in this case [Networking & wireless]("http:///ubuntuforums.org/forumdisplay.php?f=336").

This thread is closed.

---

