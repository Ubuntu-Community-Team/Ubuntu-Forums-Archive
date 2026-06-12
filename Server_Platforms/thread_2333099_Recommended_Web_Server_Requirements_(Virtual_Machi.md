---
title: "Recommended Web Server Requirements (Virtual Machine)"
date: 2016-08-06
forum: Server Platforms
---

### Post by Curlyp on 2016-08-06
Hi.  I am looking for a general recommendation on virtual web server requirements (more specifically, ram and virtual processors).  I am running Ubuntu Server 16.04.1 with LAMPS and WordPress and might add Drupal in the future.  The server is going to have minimal traffic.  

I have a general idea of what I need, but would like to get some advice from those who currently run their own.  The web server is running on a AMD A10-7700K 3.40GHz with 16GB RAM.  Right now I have 2 virtual processors and 4GB RAM dedicated to the VM.  Is that overkill?  Would one virtual processor and 2GB RAM be efficient enough?

Thanks!

---

### Post by TheFu on 2016-08-07
512MB of RAM.
1 vCPU.

Setup monitoring with Munin or Monit or Cacti, or NMS, or ... something else. See how much is actually used. Tune for that.  More RAM is generally used for "disk buffers" on Linux.  **free -mh** will show that. Definitely make decisions based on facts. Guesses are often wrong.

BTW, I don't use php, but with Perl, that would be overkill. I think php is a little lighter.  Also, if this is internal website, great, have fun. If it is external facing, be certain to stay patched, keep themes up-to-date and be aware of the OWASP Top 10 list for Php.

---

### Post by Vegan on 2016-08-07
Azure's cheapest VM is 768MB of RAM which is overkill. You get 25% of a server CPU which is overkill.

I ran Linux on a Pentium III-733 with 768MB of memory and that was overkill.

My advise, use the cheapest VM and focus on growing your site

---

### Post by Curlyp on 2016-08-07
> **TheFu said:**
> 512MB of RAM.
1 vCPU.

Setup monitoring with Munin or Monit or Cacti, or NMS, or ... something else. See how much is actually used. Tune for that.  More RAM is generally used for "disk buffers" on Linux.  **free -mh** will show that. Definitely make decisions based on facts. Guesses are often wrong.

BTW, I don't use php, but with Perl, that would be overkill. I think php is a little lighter.  Also, if this is internal website, great, have fun. If it is external facing, be certain to stay patched, keep themes up-to-date and be aware of the OWASP Top 10 list for Php.

TheFu - thank you very much for the detailed information. Are the monitoring tools (Munin or Monit or Cacti, or NMS,) used within LINUX server or can I use them on the Windows10 machine or on a Unbuntu Desktop machine to monitor the server?

Yes, the site will eventually be external facing, so I appreciate the tip on OWASP Top 10 list for Php.

> **Vegan said:**
> Azure's cheapest VM is 768MB of RAM which is overkill. You get 25% of a server CPU which is overkill.

I ran Linux on a Pentium III-733 with 768MB of memory and that was overkill.

My advise, use the cheapest VM and focus on growing your site

Vegan - thank you for the information as well.  Based on both responses, 1vCPU and no more than 1GB of ram will do.  Of course as recommend I will need to monitor as the sites gets more traffic.

---

### Post by TheFu on 2016-08-07
If you are looking for cheap hosting, Chicago VPS isn't bad. Not premium, but good uptimes.  The big names tend to spend more money on advertising.

Can't say anything good/bad about Win10. Don't use it. NEVER plan to use it .... ever.  Won't allow it on my network ... so that link won't work with Win10. Sorry, it is my political choice NOT to support it.

OWASP is just the tip of the knowledge needed to run a secure server. We all start somewhere and I honestly believe that php is the hardest sort of webapp to secure. [http://www.bbc.com/news/technology-29846539](http://www.bbc.com/news/technology-29846539)  just be aware. That link is a few years old and pretty much **every** popular webapp tool will have some similar risks. This is NOT a setup and forget effort.  If internet-facing, weekly server patching is mandatory and patching for the webapp tool is constant/daily. If you write any of the code, you'll want to watch all the patches to the language and any 3rd party libraries you use to know if they impact your site or not.  Plus if you use a reverse proxy to filter out all the bad requests and prevent admin access except through a localhost ssh tunnel, that will help too.  I see thousands of attempts on my domains/admin daily. Best to block that access completely from the internet.

Of course, the best way to learn is by doing and after you've been hacked a few times and figured out how to recover, you'll get better and better.  I was hacked twice between 2002. Taught me a bunch.  #1 tool for all of this - versioned backups.  Daily, automatic, versioned, backups.  For high risk servers I keep 120 days. For low risk systems - only 60 days.

Be very careful with 1-stop shops which sell domains, dns and hosting. Don't get burned. I run each with different providers. Bundling is easier to get started, but harder/impossible to de-couple later when you want. I've hear horror stories about almost all the major names in hosting when people tried to break up their bundles.

Have fun. Try some stuff. Don't get screwed over. ;)  You can pay $120/month for the same stuff that others sell for $5/month.  Just sayin'.

---

### Post by Curlyp on 2016-08-07
> **TheFu said:**
> If you are looking for cheap hosting, Chicago VPS isn't bad. Not premium, but good uptimes.  The big names tend to spend more money on advertising.

Can't say anything good/bad about Win10. Don't use it. NEVER plan to use it .... ever.  Won't allow it on my network ... so that link won't work with Win10. Sorry, it is my political choice NOT to support it.

OWASP is just the tip of the knowledge needed to run a secure server. We all start somewhere and I honestly believe that php is the hardest sort of webapp to secure. [http://www.bbc.com/news/technology-29846539](http://www.bbc.com/news/technology-29846539)  just be aware. That link is a few years old and pretty much **every** popular webapp tool will have some similar risks. This is NOT a setup and forget effort.  If internet-facing, weekly server patching is mandatory and patching for the webapp tool is constant/daily. If you write any of the code, you'll want to watch all the patches to the language and any 3rd party libraries you use to know if they impact your site or not.  Plus if you use a reverse proxy to filter out all the bad requests and prevent admin access except through a localhost ssh tunnel, that will help too.  I see thousands of attempts on my domains/admin daily. Best to block that access completely from the internet.

Of course, the best way to learn is by doing and after you've been hacked a few times and figured out how to recover, you'll get better and better.  I was hacked twice between 2002. Taught me a bunch.  #1 tool for all of this - versioned backups.  Daily, automatic, versioned, backups.  For high risk servers I keep 120 days. For low risk systems - only 60 days.

Be very careful with 1-stop shops which sell domains, dns and hosting. Don't get burned. I run each with different providers. Bundling is easier to get started, but harder/impossible to de-couple later when you want. I've hear horror stories about almost all the major names in hosting when people tried to break up their bundles.

Have fun. Try some stuff. Don't get screwed over. ;)  You can pay $120/month for the same stuff that others sell for $5/month.  Just sayin'.

Thanks for the info!  

I don't plan on writing much (if any code), since I will mainly use a WordPress theme.  PhP might be non-existant since I will be using WP, but when I installed LAMP, it came with it.  I don't plan on making the site public facing until I have all my ducks in a row.  I still more plenty more research do to in order to make sure it is secure.  Great tip on the reverse proxy, I will look into that as well.

Which provides do you personally recommend to purchase the domain and dns?  Since this is not going to be a heavy traffic site, I am going to host it myself, so this way I won't need to pay for hosting.

BTW, no problem on Win10; I have many friends that don't use Windows!

---

### Post by TheFu on 2016-08-07
I've only used a few hosting providers and none have impressed me.  My history has been internal webapp stuff, not interent.  Have been hosting services from my business connection for about 18 yrs. In that time, the methods I use to _secure_ any webapp have drastically changed. Many more security layers these days.  Plus my servers facing the internet are NOT on the same subnet as any other systems I run.  TiVo, Roku Wifi subnets are different from VoIP subnets which are different from desktop subnets. Each is firewalled from the others.  If they hack a server, it doesn't mean they get to any desktops or other devices.

---

### Post by Curlyp on 2016-08-07
> **TheFu said:**
> I've only used a few hosting providers and none have impressed me.  My history has been internal webapp stuff, not interent.  Have been hosting services from my business connection for about 18 yrs. In that time, the methods I use to _secure_ any webapp have drastically changed. Many more security layers these days.  Plus my servers facing the internet are NOT on the same subnet as any other systems I run.  TiVo, Roku Wifi subnets are different from VoIP subnets which are different from desktop subnets. Each is firewalled from the others.  If they hack a server, it doesn't mean they get to any desktops or other devices.


Very good info.  I will look into separate subnets.  Thanks again.

---

### Post by SeijiSensei on 2016-08-07
> **Curlyp said:**
> I don't plan on writing much (if any code), since I will mainly use a WordPress theme.  PhP might be non-existant since I will be using WP, but when I installed LAMP, it came with it.

WordPress is written in PHP so you need that to run WP.

My primary line of defense for WordPress installations is to only allow Apache to write into wp-content/uploads.  This makes it impossible for WP to update itself automatically, though, so I run a pair of scripts in the wordpress directory, one that grants write-privileges to enable updates, and one that removes them after the update is complete.

> Which provides do you personally recommend to purchase the domain and dns?  Since this is not going to be a heavy traffic site, I am going to host it myself, so this way I won't need to pay for hosting.

Your Terms of Service may prohibit running servers if you have a residential connection.

I've used [directnic.com]("http://www.directnic.com/") for my DNS provider for well over a decade now.  Decent prices and good support.  I run virtual servers in the cloud that I lease from [Linode]("http://www.linode.com/").  For simple web hosting their basic $10 machine with 2 GB of memory and 24 GB of storage is plenty.

---

### Post by Vegan on 2016-08-08
WordPress is what I use and that needs PHP 5.6 so check your web host to be sure it is available. I tested PHP 7 and WP did not work at all. So I am not sure what will happen if they retire PHP 5.6 etc

I use Azure and basic linux boxes are low cost, which means swarms are possible as needs grow.

I created a new [WP site yesterday for Linux]("http://linux-guru.azurewebsites.net/") posts. The server I make last week for MySQL powers it, and every other project I have.

This very forum uses vBulletin which would likely run well with my server. I use Ubuntu 16.04 LTS only until the next LTS release surfaces.

---

### Post by Curlyp on 2016-08-11
> **SeijiSensei said:**
> WordPress is written in PHP so you need that to run WP.

My primary line of defense for WordPress installations is to only allow Apache to write into wp-content/uploads.  This makes it impossible for WP to update itself automatically, though, so I run a pair of scripts in the wordpress directory, one that grants write-privileges to enable updates, and one that removes them after the update is complete.



Your Terms of Service may prohibit running servers if you have a residential connection.

I've used [directnic.com]("http://www.directnic.com/") for my DNS provider for well over a decade now.  Decent prices and good support.  I run virtual servers in the cloud that I lease from [Linode]("http://www.linode.com/").  For simple web hosting their basic $10 machine with 2 GB of memory and 24 GB of storage is plenty.


Thank you for the information.  Since WP is using PhP and it seems this is the most vulnerable code for websites, what code do you recommend?  Or is allowing Apache to write into wp-content/uploads make it less vulnerable?


> **Vegan said:**
> WordPress is what I use and that needs PHP 5.6 so check your web host to be sure it is available. I tested PHP 7 and WP did not work at all. So I am not sure what will happen if they retire PHP 5.6 etc

I use Azure and basic linux boxes are low cost, which means swarms are possible as needs grow.

I created a new [WP site yesterday for Linux]("http://linux-guru.azurewebsites.net/") posts. The server I make last week for MySQL powers it, and every other project I have.

This very forum uses vBulletin which would likely run well with my server. I use Ubuntu 16.04 LTS only until the next LTS release surfaces.

Thanks for the information.  I will check out your site.  The guide for WP I saw, had me setup a MySQL database for it.

---

