---
title: "VPS Timeouts/Solus VM unresponsive"
date: 2019-06-02
forum: Server Platforms
---

### Post by jordan1987 on 2019-06-02
Hi all,

Brand new to the forums -- I hope I've posted this in the right place. I did some searching on here beforehand, but couldn't find a thread that matched my issue.


[LIST]
[*]Here's my problem: Random and unpredictable VPS server downtime, which I can't rectify myself through the Solus VM control panel, and which only the host tech support can fix. I monitor my site through Uptimerobot, so I see when it goes down, and how often. Can be five times a day, or a single time, no rhyme, no reason. 
[*]Here's my aim: I'm trying to launch an ecom site using the Odoo 12 CMS platform, on Ubuntu Server 16.04 Xenial, served with Nginx, all with latest updates applied. 
[*]My configuration: The VPS, through HostedSimply.com, has 1TB bandwidth, 60GB SSD, 4GB ram, and dual core VCPUs, so while Odoo is resource intensive, I'm confident the hardware specs are more than enough to run the system with a single user. 
[/LIST]

Being a linux newb, I expect for there to be occasional downtime; maybe something I'm doing on the server causes it to hang. But I'd expect that even if this is the case, I should be able to reboot the server and start again from SolusVM, and y'know, inspect log files. The problem is that when my site goes offline, this also affects Solus. The GUI loads as usual, but whenever I issue reboot or shutdown commands, it returns with a status of Unknown, and declares the host to be unavailable. A screenshot is attached.

So, I can't access the site via the browser, via SSH, or via SolusVM. I reach out to HostedSimply's tech support, and they do something to get the site back online, but that's it. Log files don't seem to return anything suspect, and worse, the technicians refuse to answer any questions I have as to how they're fixing the problem, or why I'm experiencing it. As I suspect it's a host problem and nothing to do with my installation, I've complained to management, only to be brushed off by the same technician who repeated says "my problem is fixed" despite it continuing to occur. 

My question to you knowledgeable folk, is does this sound like a "me problem" or a provider problem? I reckon even if it were me causing the issue inside Ubuntu, I should at the very least be able to reboot my VPS, but then, like I say, I'm a newb. Is it normal for user-generated server issues to cause SolusVM to hang as well?

Many thanks in advance, and any recommendations are welcome.

---

### Post by TheFu on 2019-06-03
No VM should fail, ever.   Definitely not 5x a day. Not once a month or once every 6 months either.  It should work and work and work. A server should run until you take it down yourself.

As for the software stack you are using, I cannot say anything. Never heard of them, much less used them.

If you are trying to run a VM hypervisor within a VM hypervisor.  Don't.
Just because something is possible, that doesn't make it a good idea.

Why 16.04 and not 18.04?  Especially if you are new, 18.04 will save you multiple days of migrations in 2 years and you aren't warped, like me, from decades of prior knowledge which makes 18.04 something I want to avoid as long as possible.  But that's me. If you don't know how things worked previously, 18.04 is definitely the way to go without some extremely compelling reason(s).

---

### Post by jordan1987 on 2019-06-03
Hi TheFu -- thanks for chiming in. Yeah, the stack is a little unusual; Odoo is just a specialized open-source alternative to Wordpress that had a lot of ecommerce features I appreciated for my business. It's a Bootstrap-based system with a page-builder and native html prompt, full support for LESS, and has a backend capable of running a manufacturing component -- all without the bloat of a billion plugins. Apparently Toyota uses it in their French operations. As for Nginx (and not Apache) Odoo just seems to play nicer with it. Here's the [Wikipedia page]("https://en.wikipedia.org/wiki/Odoo") for it if you're curious.

Not trying to run a VM inside a VM either. It's a php based reverse proxy site running on a root installation. I just got a heck of a deal on an unsupervised VPS ($35 a year) with great bandwidth and specs, and tried to keep the install as minimal as possible. Seems like that price comes with it's shortcomings though, if indeed the downtime isn't something I'm causing -- especially if the sole tech also answers management emails.

I thought you might ask why not 18.04. It's sadly not an option with my host. 16.04 is the latest version of Ubuntu they offer; it's that or Centos, but I find Ubuntu just a little more intuitive at the command line level. 

Apart from constantly emailing tech support for answers (or migrating to another provider), any advice I could follow as a new server admin, with word to downtime?

---

### Post by TheFu on 2019-06-04
Sometimes a "deal" isn't a deal.
If you are using php, I have nothing to say. Sorry. Our security team won't allow it onto the internet.

I use nginx for all sorts of needs, including as a reverse proxy. Not much to say about that, besides to enable micro-caching and block all requests that cannot come from paying customers.

If you are doing this for a business, then you need 2 other setups - development, pre-production/DR to go with your production setup.  All three should be in different locations with different providers.

If you are new to Unix systems, I think you are in over your head if there is any money going through these systems.  Host some cat videos for a year, see how many times you get hacked. I suspect you don't have that option, but please explain the problem to upper management.  

I've had to set down with a few CEOs and explain what our plan was WHEN their main website was hacked a few times.  WHEN, not if.  All of them were pissed. Clearly, if we knew the website would be hacked, then we should be able to prevent it, right?  We laid out a plan to have most of the site backup and static content accessible in a few minutes, but also explained that the dynamic parts would probably take at least a day to figure out the issue and mitigate, perhaps a week.  We got everything in place and did a full test early on a Sunday morning to be certain that plan worked.  Then we spend the next 3 yrs maintaining the capability. It wasn't fun or sexy and we never did get hacked, on that site.

---

