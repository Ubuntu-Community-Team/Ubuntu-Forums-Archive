---
title: "How realistic, security-wise, is it to run my own server?"
date: 2018-04-21
forum: Security
---

### Post by Paddy Landau on 2018-04-21
[SIZE=3]**[FONT=verdana]Background[/FONT]**[/SIZE]

I currently host four websites, all WordPress. Three are on behalf of charity and community, which I provide free of charge as a community service, and one is mine (it doesn't generate a profit).

I use a commercial host, which I pay annually for the hosting.

In other words, I make a loss on these websites.

It's worth noting that as local-only sites, they all receive few hits &#8212; three are just a few daily, and the fourth has around 50&#8211;100 daily (those figures include the maintainers' own views). There are several email boxes and many email forwarders.

[SIZE=3]**[FONT=verdana]Needs[/FONT]**[/SIZE]

Given the current state of internet security, the websites need SSLs.

My current host charges rather a lot for an SSL certificate. Considering that I make a loss providing these websites free of charge for charity, paying rather a lot is rather a lot too much!

Unfortunately, my present host doesn't allow [Let's Encrypt]("https://letsencrypt.org") (which is what I would have used).

So, the only choice that I can think of is to run my own server on something like [AWS]("https://aws.amazon.com/") or [Google Cloud]("https://cloud.google.com/"). I imagine that this would anyway be cheaper long term. Then, I can use any certificate that I want, including Let's Encrypt.

**[FONT=verdana]Security[/FONT]**

My big concern is security. If I install a standard Ubuntu server on my chosen cloud service, how secure would it be?

I know how to create a LAMP server and keep it updated &#8212; but I am no expert. I don't (yet) know how to install CPanel or equivalent.

Would running my own server be insecure and leave the websites open to hacking, bearing in mind my amateur status?

What would you recommend for me, and what pitfalls might I have missed?

---

### Post by TheFu on 2018-04-21
Switch to static websites to avoid the constant wordpress security issues/updates.  Static sites remove almost all typical web-app vulnerabilities.  Obviously, avoid using 1-off WP themes.  Subscribe to all WP security lists and RSS feeds you can.  Wordfence comes to mind.

If you switch to static sites, then something like NearlyFreeSpeech.net becomes possible. It isn't point-n-click. It expects you to know Unix... actually, they use BSD.  You pay for bandwidth only on static sites, so $0.50/month isn't an unreasonable cost estimate.

Not having cPanel is a good thing.  Why provide another attack vector?  This is extremely important for someone fairly new to running servers - avoid the GUIs. That applies to webmin, myphpadmin, or any other webapp admin tool.  Use common sense. More methods equals more attack vectors. The goal is to have minimal exposure to attacks and never provide a userid any more rights than needed to do the task.  

There are lots of VPS providers and Amazon is pretty expensive compared to some others.  If 100% availability isn't a concern, you can go for the cheaper sets like ChicagoVPS.  If you need a little better performance, vultr or digitalocean both use SSDs.

If you run email lists, then the first thing to do with any new server is to verify that the static IP provided isn't on any email block lists.  It is just too much hassle to get them removed. Just ask for a different IP from the VPS provider and tell them why if there is an issue.

While you can run servers at home, that normally requires a static IP from the ISP, which usually means changing to a business account, which usually costs 2x more for 20% of the residential bandwidth.  I pay $110/month for a 15/3 Mbps connection. I'm looking at switching to a single VPS as a gateway for my email gateway and static sites, but I'll keep about 10 servers running at home with a VPN connection to the VPS.  My real email server will remain at home.  I've been running with an email gateway for awhile now and it has been working perfectly.  Spending $50/month less on internet really will open up VPS options.

Being cautious is smart.  After you are hacked the first time, things will look a little different.

Anyways, that's some of my thoughts.

---

### Post by Paddy Landau on 2018-04-22
Thank you for such a comprehensive answer, @TheFu. I'll answer your points before I start to look further into the ideas.
> **TheFu said:**
> Switch to static websites…
That's great in theory, but unfortunately, with one exception, the people need the WordPress functionality. So, it will have to remain WordPress. "I would if I could, but I can't."
> **TheFu said:**
> Obviously, avoid using 1-off WP themes.
I understand about the one-off themes, and I absolutely concur. Ditto plugins. Bona fide reputable providers only!

One good thing that I hadn't thought to mention is that there are no shopping carts or payment portals involved in any of the websites.
> **TheFu said:**
> Subscribe to all WP security lists and RSS feeds you can.
Do you have suggestions for such lists? Running a server for more than play-around is a pretty new area for me!
> **TheFu said:**
> Wordfence comes to mind.
I presume that you mean [this Wordfence]("https://www.wordfence.com")? It looks quite expensive (for my needs, that is; it's cheap for a profitable business, and I'm not even a business much less profitable). I have been using [NinjaFirewall WP+ Edition]("https://nintechnet.com/ninjafirewall/wp-edition/"), which provides a pretty decent free version; again, the full version is too expensive for me.
> **TheFu said:**
> Not having cPanel is a good thing…
Point taken. I didn't realise that cPanel was a significant risk. I shall investigate using non-GUI for multiple websites — at the moment, I host a single website in VirtualBox for play-around only, so I don't (yet) know how to handle multiple sites.
> **TheFu said:**
> There are lots of VPS providers… If 100% availability isn't a concern…
Our websites aren't important enough to warrant the cost of 100% availability. I'll settle for "pretty good." Because of strengthening privacy laws in the EU (I live in the UK), I need an EU-based provider, which I believe that AWS and Google both provide. If you have suggestions for EU, especially the UK, I'd love to hear. I'll add [Vultr]("https://www.vultr.com") and [DigitalOcean]("https://www.digitalocean.com") to the list, because they both support UK servers.
> **TheFu said:**
> If you run email lists…
Not at this stage, but one of the charities might decide to do this (again, strictly local and limited to just a couple of hundred people). I'll keep in mind your warning. Do you know where I can find suitable email block lists to check against?
> **TheFu said:**
> While you can run servers at home…
I don't have a spare computer to do this, but it should be easy to get hold of a secondhand one. I believe that I can get a static IP address from my ISP at no charge should I decide to go ahead with this. (It's already static provided that I don't turn off my modem for more than a few hours at any one time, which I wouldn't do anyway.)

My ISP (cable) already provides a reliable 100 Mbps download, but the upload is much slower at 10 Mbps and even less.

My current host doesn't record bandwidth (!) because I have an "unlimited" plan, but some back-of-the-envelope calculations indicate that the websites provide roughly 22 Mb per day (that's a fairly pessimistic estimate). That's not much at all, is it? Add in emails, and it's no more than 1 Gb per day. The ISP's 10 Mbps would be sufficient, wouldn't it?

 Assuming that the upload speed is sufficient, hosting from home is actually an excellent idea that I hadn't seriously considered. It's something to sleep on.
> **TheFu said:**
> Being cautious is smart.  After you are hacked the first time, things will look a little different.
I can fully believe that! I already have two great habits: I back up all of the websites including databases weekly (they don't change fast), and I protect the back-end with Apache-level password security (in addition to the normal WordPress login security). I wonder what else I could do?

Thank you again for your thoughtful responses, which give me quite a bit to go on.

---

### Post by TheFu on 2018-04-22
I should say that I won't run any wordpress or other php-based webapps on internet facing systems.  I think the risks are just too high. It (php) smells bad to me.  That is for a few reasons.  The php language team has shipped multiple major updates with known sev-1, critical, security bugs.  Also, because php is so easy to get started, it appears from the outside that 95% of the coding done using php is performed by non-experts.  That is a huge liability.  OWASP has an interesting article about every popular scripting language - their "Top 10" list is eye opening.
There are other options to running wordpress.  Wordpress is like MS-Windows. It is a huge target. Running almost any other CMS would drastically reduce the attacks in the same way that running Linux reduces the attacks.  I'd look for a CMS based on python, perl, ruby ... anything but php.  All of them have import tools to migrate from wordpress.  BTW, my neice's partner is a core WP developer. He can definitely make secure php.

I would never run a server on virtualbox.  KVM is what I use, since 2010 or so.  Virtualbox is fine for desktop-on-desktop needs, but it isn't nearly as efficient and stable as KVM.  

Just because a connection IP doesn't change, that doesn't mean it is static.  Email blocking happens for all DHCP subnets.  All of them.  If the network isn't marked as static, I don't know any email server that will accept it. None of mine will.  Server-to-server email has very different rules than client-to-server email agreements.

If you can keep the 100/10 connection with the static IP, it will most definitely meet your bandwidth needs, unless there is an article on a huge site that points at yours.  I've had that happen and it was a DDOS problem.  In the 1990s, our business had 128Kbps ISDN internet connections and we ran email, web, and remote access through that.

Beware that if you host from home, then you'll need much better network security to limit having your home network totally pwn'd.  I run 3 subnets with 2 routers controlling access to different parts of the network. The public-facing services are on a different network than home computers.  Wifi is treated like the internet. Gaming systems and wifi sit outside the network that I secure.

Apache passwords aren't exactly much security.  Sorta like a "Beware of Dog" sign when the dog is a puppy. Misconfiguration of apache can easily provide access to the passwords.

If you want better security, block access to the systems from people who don't need access.  If nobody in different countries need access, BLOCK THEM!  If you know where the access will come from, then block everyone EXCEPT those specific subnets.  Get system monitoring working, remote logging, and watch the logs for any issues.  Backups need to happen daily, since attacks happen daily too.  If you run a DBMS, don't allow systems to access it that don't need access. 

Never forget that with a public system, attackers see that box as a jump machine to the rest of your network.

BTW, I don't think my post are comprehensive.  Barely touched the issues - definitely less than 1% of what you should know. 
A few of my blog posts about this stuff: 
* [http://blog.jdpfu.com/2016/10/04/lamp-server-security](http://blog.jdpfu.com/2016/10/04/lamp-server-security)
* [http://blog.jdpfu.com/2014/02/28/1st-five-minutes-on-a-server](http://blog.jdpfu.com/2014/02/28/1st-five-minutes-on-a-server)

---

### Post by Paddy Landau on 2018-04-22
> **TheFu said:**
> I should say that I won't run any wordpress…
I hear you. Unfortunately, the biggest community website has 400 posts and over 100 pages, with just one volunteer (very much part-time) to run it. Converting it to a different CMS will be too large an exercise. It will just have to be WordPress. One good thing about WordPress is that it updates itself automatically; it doesn't rely on my needing to check that it needs it.

> **TheFu said:**
> I would never run a server on virtualbox.  KVM is what I use, since 2010 or so.
That's useful to know for the future. The VirtualBox is really just to experiment. It is not used for anything serious, or indeed for anyone other than me to experiment with.

> **TheFu said:**
> Just because a connection IP doesn't change, that doesn't mean it is static.  …  If the network isn't marked as static, I don't know any email server that will accept it.
I didn't realise that there were technical considerations there. I'll definitely check out a static IP address with my ISP if I go the home route.

> **TheFu said:**
> … unless there is an article on a huge site that points at yours.
Luckily, that is highly unlikely to happen. The sites all serve a local area of just 4,000 people, so no large site will find us useful!

> **TheFu said:**
> Beware that if you host from home, then you'll need much better network security to limit having your home network totally pwn'd.  I run 3 subnets with 2 routers controlling access to different parts of the network. The public-facing services are on a different network than home computers.  Wifi is treated like the internet. Gaming systems and wifi sit outside the network that I secure.
Whoa! That is useful information indeed, thank you. It's now sounding as though a home server is a non-starter for me, as I don't have that type of expertise — or spare cash!

> **TheFu said:**
> Apache passwords aren't exactly much security. … If you want better security, block access to the systems from people who don't need access.  If nobody in different countries need access, BLOCK THEM!  If you know where the access will come from, then block everyone EXCEPT those specific subnets.
Thanks for the heads-up.

Thanks also for the links.

I'm starting to think that running my own server will be a venture too risky for me. It's a pity that the internet is so dangerous — it's always the few who spoil it for the many, isn't it?

Thank you for taking all this time and effort to educate me. I appreciate it.

---

### Post by CharlesA on 2018-04-22
> **Paddy Landau said:**
> 

One good thing that I hadn't thought to mention is that there are no shopping carts or payment portals involved in any of the websites.

There are a few payment portals like Stripe or Paypal that would kick you out of scope for taking payments, but I wouldn't want to deal with the added headache of ensuring compliance with Payment Card Industries -Data Security Standard (PCI-DSS)..

> I presume that you mean [this Wordfence]("https://www.wordfence.com")? It looks quite expensive (for my needs, that is; it's cheap for a profitable business, and I'm not even a business much less profitable). I have been using [NinjaFirewall WP+ Edition]("https://nintechnet.com/ninjafirewall/wp-edition/"), which provides a pretty decent free version; again, the full version is too expensive for me.

Did you check out the free version? It looks like it has most of the features of the premium version and there are ways to block certain counties at a firewall level. I use [CSF]("https://configserver.com/cp/csf.html") for my firewall/IDS, but it can take a bit of tuning to get it set up.

> Point taken. I didn't realise that cPanel was a significant risk. I shall investigate using non-GUI for multiple websites &#8212; at the moment, I host a single website in VirtualBox for play-around only, so I don't (yet) know how to handle multiple sites.

I wouldn't run any sort of Web GUI on a personal site, even if it makes it easier to manage because of the added attack surface. But I'm also lazy and don't feel the need to deal with it since my web server's config doesn't change very frequently.

> Our websites aren't important enough to warrant the cost of 100% availability. I'll settle for "pretty good." Because of strengthening privacy laws in the EU (I live in the UK), I need an EU-based provider, which I believe that AWS and Google both provide. If you have suggestions for EU, especially the UK, I'd love to hear. I'll add [Vultr]("https://www.vultr.com") and [DigitalOcean]("https://www.digitalocean.com") to the list, because they both support UK servers.

I use [RamNode]("http://ramnode.com/"), myself, but they are US-based, but have a site in the Netherlands. I don't know if they adhere to the new EU privacy stuff.

> I can fully believe that! I already have two great habits: I back up all of the websites including databases weekly (they don't change fast), and I protect the back-end with Apache-level password security (in addition to the normal WordPress login security). I wonder what else I could do?

By backend, you mean the Wordpress Admin page, right? I've always tried to whitelist access to the admin section of a site, be it SSH, VPN or otherwise.

I wouldn't use an Apache password for that tbh, at best, it is security via obscurity even with a decent password. If you configure the web server to only allow access to certain areas of the site from a specific IP and then add that same list to the firewall, that should be more than enough to stop most brute force attacks.

> **TheFu said:**
> I should say that I won't run any wordpress or other php-based webapps on internet facing systems.  I think the risks are just too high. It (php) smells bad to me.  That is for a few reasons.  The php language team has shipped multiple major updates with known sev-1, critical, security bugs.  Also, because php is so easy to get started, it appears from the outside that 95% of the coding done using php is performed by non-experts.  That is a huge liability.  OWASP has an interesting article about every popular scripting language - their "Top 10" list is eye opening.

How would you rank a mostly static site written in 90% HTML and some PHP?

In any case, +1 to TheFu. Personally I wouldn't want to run something from home without it being totally isolated from the rest of my network, which is why I host my site on a VPS.

---

### Post by Paddy Landau on 2018-04-22
Charles, thank you for the extra information.

> **CharlesA said:**
> Did you check out the free version?
Oops — I missed that the first time I looked.

> **CharlesA said:**
> I use [RamNode]("http://ramnode.com/"), myself, but they are US-based, but have a site in the Netherlands. I don't know if they adhere to the new EU privacy stuff.
The Netherlands is part of the EU, so, yes, it would adhere to the new rules. Thanks for the recommendation.

> **CharlesA said:**
> By backend, you mean the Wordpress Admin page, right? … If you configure the web server to only allow access to certain areas of the site from a specific IP and then add that same list to the firewall, that should be more than enough to stop most brute force attacks.
I do mean the WordPress Admin, yes. Interestingly, NinjaFirewall seems to recognise and prevent brute force attacks. Trying to ascertain everyone's IP address, especially in a world where people can access the back-end from their home router, their work network, and their data plan, would be hard. Restricting access to just the UK would probably be the only way to go for someone with my limited skills.

---

### Post by CharlesA on 2018-04-22
> **Paddy Landau said:**
> 
I do mean the WordPress Admin, yes. Interestingly, NinjaFirewall seems to recognise and prevent brute force attacks. Trying to ascertain everyone's IP address, especially in a world where people can access the back-end from their home router, their work network, and their data plan, would be hard. Restricting access to just the UK would probably be the only way to go for someone with my limited skills.

How many people are going to need access to the admin page?

---

### Post by TheFu on 2018-04-22
> **CharlesA said:**
> How many people are going to need access to the admin page?

My blog admin page can only be access from the same LAN or localhost.  I see hundreds of attempts daily, mainly by bots seeking to find wordpress sites they can hack. ;)   Using nginx as a reverse proxy, it is easy to limit access to specific pages based on source IP.  I'm certain apache can do that too.

I recall a reader telling me that the login page was public ... which was true, but the admin page was blocked. I decided to remove logins and just switch to moderated commenting.  Also disabled comments for articles over 60 days old.
Those changes took away all the spam attempts, which were getting bad.  Now I see about 1 blog-spam attempt a year and it is never seen by the public. 

GeoBlocking isn't 100%, but it is probably good enough for non-business sites.  Just be certain to refresh the geo-DB yearly.  

Running multiple sites on a single VM is pretty easy.  Apache/nginx both have virtualhost facilities.  Pretty easy.  These days even using SSL certs on the same IP isn't all that hard.  I have 2 - nextcloud and wallabag on the same machine. The only trick for me is that the Let's Encrypt cert renewal has to be available from the internet. I don't allow either of those webapps to be available directly over the internet, except for the 3 minutes every 90 days during cert renewal. The rest of the time either a SOCK-ssh proxy or VPN connection to the LAN is needed.

---

### Post by TheFu on 2018-04-22
Last time I looked, wordpress updates required using  plain FTP.  That is a non-starter from a security standpoint.  Plain FTP should have died in 1995, IMHO.

I'm posting from a worst-case standpoint.  Hope for the best, but plan for the worst.  If the worst happens, what does that mean to your other networked devices?   

There are automated tools seeking out WP sites to hack.  I see at least 10 spam/phishing emails with links to pwn'd wordpress sites in the logs every day.  If you are staying with WP, have you looked at commercially supported wordpress solutions?

---

### Post by Paddy Landau on 2018-04-22
> **CharlesA said:**
> How many people are going to need access to the admin page?
Probably four active users (well, "active" is a relative term) and another four occasional ones. So, that's a good point — not many people to manage.

> **TheFu said:**
> … it is easy to limit access to specific pages based on source IP.  I'm certain apache can do that too.
Yes, Apache can do that from the [FONT=lucida console].htaccess[/FONT] file. It's a bit of manual operation, but with only a dozen people or fewer, not onerous.

> **TheFu said:**
> I decided to … switch to moderated commenting.  Also disabled comments for articles over 60 days old.
Our websites don't allow commenting at all. Spam was reduced to zero. Fortunately, we don't need comments at all.

> **TheFu said:**
> GeoBlocking isn't 100%, but it is probably good enough for non-business sites.  Just be certain to refresh the geo-DB yearly.
I wonder if one of the firewalls can do this automatically?

> **TheFu said:**
> Running multiple sites on a single VM is pretty easy…
Thanks. More complication for me to consider :)

---

### Post by Paddy Landau on 2018-04-22
> **TheFu said:**
> Last time I looked, wordpress updates required using  plain FTP.  That is a non-starter from a security standpoint.  Plain FTP should have died in 1995, IMHO.
Hmm, I can't comment on that, because I don't know how it works. If it really is insecure, that's plain stupid. When did you last check? I'll see if I can find out about the updates.

> **TheFu said:**
> I'm posting from a worst-case standpoint.  Hope for the best, but plan for the worst.  If the worst happens, what does that mean to your other networked devices?
Brr! That sends shivers down my spine.

> **TheFu said:**
> If you are staying with WP, have you looked at commercially supported wordpress solutions?
I'm unsure what you mean by "commercially supported wordpress solutions". My current host explicitly supports WordPress, so I presume that's a good thing. Is that what you meant?

---

### Post by TheFu on 2018-04-22
With just 4 users, I'd setup either a VPN or ssh-SOCKS proxy that only allows the proxy, no shell.
Then you can block the entire world from the admin page and only allow localhost (or the VPN exit node).  A VPN is easier for non-technical people.

I checked into the wordpress update today.  There are non-FTP methods, but those seem even worse since they leave the sites able to modify themselves. I thought the core security practice for all blog engines was to make everything read-only to the userid running the blog (www-data/apache/whatever) so it couldn't be modified by itself?    Perhaps I'm misreading ... or found an article written by a total Unix noob.  Hard to tell.

I have admin on 1 WP site.  I don't manage it.  The official admin doesn't really manage it either, since I login about once every 2 months to post something and there is always an update waiting to be installed.

virtualhosts is really simple in nginx and apache.   sites-available/ and sites-enabled/ are the directories.  Pretty simple to use name-based virtualhosts.  The hardest part about this is discussing "virtual" with people who mix web server and hypervisor in the same paragraph.   A virtualhost is used by both groups.

I don't know of any free firewalls that automatically update geo-blocking DBs. And the sub-$1000 firewalls which do have a long history of security failures.  I was watching a security conference demo today (about 4 months old) where they hacked Cisco and Sonos stuff and pointed out there were lots and lots of other issues available for exploit.

As to whether your current hosting provider "supports" wordpress or not, I would assume they provide a fresh install, but don't really maintain it for you.  What I'm suggesting are places that actively maintain the wordpress sites and use a multi-tenent install.  I think wordpress.com does that,but don't quote me.  I take an "assume the worst" stance when it comes to security.

And just to be very clear, my systems are hardly perfect either.  Some are extremely well-maintained.  Then I have 2 systems that it is very hard to keep them patched, current, maintained.  I'll end up wiping them at some point, when life slows down.

---

### Post by Paddy Landau on 2018-04-22
> **TheFu said:**
> I checked into the wordpress update today… they leave the sites able to modify themselves.
I could be mistaken, but I think that this is deliberate to allow WordPress to update itself. It's probably safer to do that, because security updates need to go in soon after release, and the majority of website maintainers don't do that.
> **TheFu said:**
> … I login about once every 2 months to post something and there is always an update waiting to be installed.
WordPress will update itself, in my experience, within a day of a new release. I connect my websites to my Jetpack login (easy to do, even for me!), and Jetpack automatically updates the plugins whenever they are updated. I never have to manually update either WordPress or plugins. However, I've noticed that themes and, occasionally, translations need to be manually updated.

---

### Post by TheFu on 2018-04-22
jetpack  
[https://wordpress.org/support/topic/my-site-got-hacked-2-times-via-jetpack-security-issue/](https://wordpress.org/support/topic/my-site-got-hacked-2-times-via-jetpack-security-issue/)

Just installing security addons don't remove the need to actually know a little about security.

Allowing a web-app to self-modify is bad news if it is on the internet.  Bad trade-craft. Smells funny.

IMHO.

---

### Post by Paddy Landau on 2018-04-23
Well, thanks for all the advice, information and education!

I have slept on this and come to the conclusion that I have nowhere near enough expertise to run my own server safely. Unfortunately, I don't have the time to learn, as much as I would love to.

Therefore, I shall either stay with my current host and try to figure out another way to get a certificate (unlikely), or change host to one that is cheaper and that provides an SSL at reasonable cost for charities and non-profits.

Thank you again for all of your time; let's hope that this also helps other aspiring hosts! I shall mark this thread as solved.

---

