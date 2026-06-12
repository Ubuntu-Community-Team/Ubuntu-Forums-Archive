---
title: "Picking the umpteenth hosting site..."
date: 2007-11-28
forum: The Cafe
---

### Post by Vadi on 2007-11-28
So, I want to get myself a website. Not too small, since I plan on expanding it later, but not too big either, since well there's always a thing called budget (:().

However, after digging around in the market some, I'm completely confused. Each website seems to offer different prices, but with that, there's also a link of like 20 things they do and don't do. Especially the languages part - as I was told I wouldn't be able to install new ones, so if I get a site that doesn't have some language, and I want to install something that does need it, I'm screwed.

The one site that I'm leaning at is godaddy.com right now, but their site is a bit odd since I've been told people from china & germany can't access it. :/.

So, since I'm completely confused about the whole deal, does anyone have suggestions on a good hosting site?

---

### Post by matthew on 2007-11-28
Well, since you mentioned budget, take a look at [Site5's latest deal]("http://www.site5.com/in.php?id=43539").

---

### Post by akiratheoni on 2007-11-28
While I like Dreamhost because of their really lax policy and my site is based around freedom of expression, the uptime is terrible. I hear HostGator is really good, though.

---

### Post by Vadi on 2007-11-28
I can't seem to find out what site5 is using for their web servers :/.

Right now I'm between godaddy.com and the hostgator.com then... but godaddy's site is very confusing and I've yet to understand their plans.

Another question... I want to install Enano on my laptop to test it out how it works. I suppose I should getstarted with Apache first - I searched it in the help docs, but there are so many articles on it! Can anyone recommend me one too?

---

### Post by matthew on 2007-11-28
> **Vadi said:**
> I can't seem to find out what site5 is using for their web servers :/.I just looked and it isn't stated on their website. Weird. Anyway, they use Linux (CentOS, to be precise) with Apache. They run a typical LAMP stack with all the usual stuff available.

EDIT: these look pretty informative from their wiki...
[http://wiki.site5.com/Pre-Sales](http://wiki.site5.com/Pre-Sales)
[http://wiki.site5.com/Resource_Usage_Policies](http://wiki.site5.com/Resource_Usage_Policies)
[http://wiki.site5.com/Linux](http://wiki.site5.com/Linux)

Most of the other suggestions have been pretty good, too.

---

### Post by Vadi on 2007-11-28
" Processes

Processes invoked by the web server, cron, shell or any other method should not exceed the following limitations:

    * Consume more than 16 MB of RAM.
    * Utilize in excess of 15 seconds of CPU time.
    * Number of open files should not exceed 64.
    * Create core dumps.
    * Number of simultaneous processes should not exceed 5.
    * Execute a script/binary that forks in a way to create a fork bomb.
    * Programs may not run in the background or listen on a network port. If you require a bot, service or daemon, you should consider a dedicated server, as very few shared web hosts allow this type of program. "

I don't quite understand. Only 16mb?

---

### Post by matthew on 2007-11-28
> **Vadi said:**
> "Processes invoked by the web server, cron, shell or any other method should not exceed the following limitations:

    * Consume more than 16 MB of RAM. "

I don't quite understand. Only 16mb?
That is per process...since you won't be running an xserver or any graphics-intensive processes on the server, but rather just serving web pges with Apache and probably making database connections, this isn't going to be an issue.

---

### Post by Vadi on 2007-11-28
Ah okay.

What worries me though is that apparently there is a restriction on what you can install... and since I have no idea yet what I will, it's hard to pick!

---

### Post by hkgonra on 2007-11-28
Looking at the site5 deal has got me to thinking. 
Is there any reason why you couldn't , or shouldn't be able to use a hosting account for off-site backups of data ? 
Can it be setup securely ? 
Just looking at the prices it is MUCH cheaper to buy storage space from a hosting account than from a place setup to do backups.

---

### Post by az on 2007-11-28
Hostmonster has lower prices for a comparable plan.
[http://hostmonster.com/](http://hostmonster.com/)

If you want to have some really inexpensive hosting (if you don't need all that much bandwidth and storage), check out:
[http://www.247-host.com/plans.html](http://www.247-host.com/plans.html)


See also:
[http://drupal.org/node/110531](http://drupal.org/node/110531)

Drupal is quite demanding.  If a Drupal site runs well on a hosting provider, they are doing a pretty good job.

P.S.  Stay away from godaddy for hosting.  They don't offer the best performance and have a reputation for not being honest.

---

### Post by cyclefiend2000 on 2007-11-28
we have godaddy's lowest level plan right now (i forget what it is called). no idea whether people in china or germany can access the site. i am mainly using it for playing around with right now. 

godaddy let's you choose whether to go with a windows or linux server. we chose linux of course. our package allows for 10 mysql databases and has php installed (not sure what else. i was mainly interested in mysql and php). through the "go daddy hosting connection" you can install a number of different web applications. right now i have joomla, zencart, gallery2.0, and simple machine forums installed. there are quite a bit of others that can be installed though. i am pretty sure that you can manually install just about any forum software, cms, etc.

that said, godaddy's main site is confusing and hard to navigate. once you figure out where you want to go though it isnt too bad.

good luck with whatever you choose.

---

### Post by Vadi on 2007-11-28
I don't know. This isn't even funny. Ever post says they had problems with the old one and recommend a different one.

...

I think I'll start looking at the refund policies.

---

### Post by hkgonra on 2007-11-28
fwiw I have been using godaddy for business ( 20 sites ) and personal for over a year and have been nothing but pleased with them.

---

### Post by matthew on 2007-11-28
> **az said:**
> Drupal is quite demanding.  If a Drupal site runs well on a hosting provider, they are doing a pretty good job.
FYI, I have two Drupal installations on the same account with Site5 (matthewhelmke.com, a private site, and derbyandwehttam.com, a small business site). I set them up using subdirectories with domain pointers, but they are both hosted on the same account.
> **Vadi said:**
> I don't know. This isn't even funny. Ever post says they had problems with the old one and recommend a different one.

...

I think I'll start looking at the refund policies.I don't work for Site5 and I get nothing in return for saying this (unless you sign up using one of my links...but even then it's just a nice kickback for next time my renewal comes up). They do give a 60 day, no questions asked, happiness guarantee.

---

### Post by matthew on 2007-11-28
> **hkgonra said:**
> Is there any reason why you couldn't , or shouldn't be able to use a hosting account for off-site backups of data ? 
Can it be setup securely ? 
Just looking at the prices it is MUCH cheaper to buy storage space from a hosting account than from a place setup to do backups.Most shared hosting providers have a clause in their resource usage policies forbidding this for different reasons. You can secure your backups, but if you get caught using most shared-resource accounts this way, your account will probably be canceled, and you won't get a refund. Read the policy of the provider before you try this...oh, and since you mentioned it, I know Site5 does not allow this. I wanted to do it myself and researched it.

---

### Post by Vadi on 2007-11-28
Well, thanks for the solid words, I'll give it a try then (from your link). At least I know how to bug now ;)

---

### Post by hkgonra on 2007-11-28
> **matthew said:**
> Most shared hosting providers have a clause in their resource usage policies forbidding this for different reasons. You can secure your backups, but if you get caught using most shared-resource accounts this way, your account will probably be canceled, and you won't get a refund. Read the policy of the provider before you try this...oh, and since you mentioned it, I know Site5 does not allow this. I wanted to do it myself and researched it.

Well that stinks. 
At least I know I am not the only one that had this idea. :)

---

### Post by matthew on 2007-11-28
> **Vadi said:**
> Well, thanks for the solid words, I'll give it a try then (from your link). At least I know how to bug now ;)Cool. I hope it works out well for you.

They also have [a good forum]("http://forums.site5.com/").

---

### Post by Warpnow on 2007-11-28
Most standard web hosts won't let you install anything on the server or run any processes at all beyond what they have the control panel using.

But, just running a website, you don't need to.

If you need to install applications look into a VPS or a dedicated server. Shared hosts don't allow it.

---

### Post by frup on 2007-11-28
I've found that the income from adsense I make off my sites is essentially how much I need to pay for hosting. Right now I am paying $320 per month for 2 dedicated servers with a massive amount of bandwidth being used. Very soon We will need to upgrade both servers but are waiting for larger Hard drives from the host. Recently we have been making ~$250 per week from adsense. The bulk of this is firefox referrals. Ad impressions are around 25,000 per day which with a very low cpm at the moment (around $0.39) results in only $10 (which is similar to what we were getting with only 2000 impressions per day oddly.

We are wanting to consolidate the files (ie downloads) on the 2 servers to 1 server (hence why we need more disk space) and move to storing scripts and pages on a VPS. We haven't done enough research on how effective this would be yet though. We moved to dedicated after using too much resources on VPS. Considering we are trying hard to get to 100,000 impressions per day so we can use the adsense API (I'm not exactly sure we can do this), our exact plans for the future are blurry.

---

### Post by Vadi on 2007-11-28
Unfortunately site5 doesn't accept paypal, which is the method I was gonna pay with.

So I'm back to square one.

This is all giving me a headache, so I decided to start on the actual site instead. I got the Apache web server running on my laptop (yay!), and installed Enano CMS. I'm playing around with it right now.

---

### Post by Grey Box on 2007-11-28
I got my website running on Godaddy, just because they provided fairly straightforward hosting plans with MySQL and PHP and all that. But also because I bought the domain name from them and the SSL cert, but overall the whole thing was cheap. The site is always up - haven't had any downtime or 12 months. I don't know if they take Paypal though.

---

### Post by Vadi on 2007-11-28
They do take it.

These are the requirements for Enano CMS though, which I've really come to like:

> Requirements for Enano on shared hosting services

Your webhost of choice should meet these requirements:

    * The host provides support for PHP scripts
    * You have access to at least one MySQL database
    * The server supports writing files
    * The server is running PHP version 4.3.0 or later
    * The server is running MySQL 4.1 or later
    * Optional: The server is running Apache Web Server, version 1.3.22 or later
    * If the server is running Apache, it should preferably provide support for mod_rewrite. Ask your host for more information.
    * FTP or SSH access


Do you know if godaddy fills them?

---

### Post by cyclefiend2000 on 2007-11-28
godaddy will allow you to choose either php 4 or php 5. 

the latest app i installed uses mysql 5.0 database.

i know they allow ftp access. not sure about ssh.

edit: you have to have a "dedicated server" account to have ssh access.

---

### Post by Vadi on 2007-11-29
Don't need a dedicated one yet.. when I do, it probably won't be with them. Okay, so I'll give them a try later on if I don't get anything else.

---

### Post by bwallum on 2007-11-29
I always use Fasthosts, never had a problem. 

[http://www.fasthosts.co.uk/](http://www.fasthosts.co.uk/)

They are very scaleable, start off lite and go to whatever you need.

---

### Post by Vadi on 2007-11-29
Scalable. Now there's a winning word. I'll give it a look, thanks!

---

### Post by timcredible on 2007-11-29
i have 3 sites with hostmonster.com.  $6/month for 300GB of storage, 3TB/month of bandwidth.  they seem to be fine, but there are plenty like them out there.  they offer php4 and 5, and have joomla available if you want to use it for your website - here's [my article]("http://linux--help.org/joomla2/index.php?option=com_content&task=view&id=48&Itemid=57") on joomla.

---

### Post by ivia77 on 2007-11-30
> **bwallum said:**
> I always use Fasthosts, never had a problem. 

[http://www.fasthosts.co.uk/](http://www.fasthosts.co.uk/)

They are very scaleable, start off lite and go to whatever you need.

:shock: Fasthosts are well known for being flakey.

Today they have reset all passwords, including ftp, sql, and user control panel passwords with no warning. Leaving sites no database access and no way of changing the situation until the new passwords turn up VIA ROYAL MAIL!!!

As you can imagine, this hasn't gone down too well.

---

### Post by bwallum on 2007-11-30
Just picking up on iVIAs comment. I can confirm that Fasthosts logon servers are down at the moment. If the above is true please ignore my pointer to them.

---

### Post by bwallum on 2007-11-30
Fasthost's log on servers were down this morning but I can log on to all areas ok now. Rgds, bob

---

### Post by v8YKxgHe on 2007-11-30
[TextDrive/Joyent]("http://www.textdrive.com") are really good, a bit expensive than some ... most, ok probably all :) but they are amazing! They really give you a lot of freedom and offer a lot, I think if you have to host many sites, the cost of Textdrive/Joyent will then seem quite cheap.

They've got great support and community support as well, really is the best host I've ever been with.

---

### Post by Vadi on 2007-11-30
Does anyone have experience with Network Redux ([click]("www.networkredux.com"))?

I like that in their "Why Network Redux" page they list their open-source sponsorships :)

---

