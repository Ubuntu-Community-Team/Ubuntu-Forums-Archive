---
title: "DNS server and domain pointing"
date: 2022-08-09
forum: The Cafe
---

### Post by sairfan1 on 2022-08-09
**Let me explain the situation** 

I have three domains with godaddy that i want to host locally (at home), there are three computers for each domain ready for hosting websites.  I can port forward and make publically accessible one domain at a time. 

**What solution I found** 
While googling around i learned a method reverse proxy to use all 3 domains and hosting computers, but this method more looks like a workaround or hack, I want to know what method hosting companies use for it? 

**Solution I'm working on**
While further learning i came to know we need DNS server setup that make sense to me, I learned online about setting up DNS server and forward and reverse zones, I understand that in my scenario forward zone will be helpful 

but i do not understand how DNS server will interact with domain, like when my main router will receive a web page request from internet how that request will be listened by my dns server and then sent to related web server/computer ip. 

**Other route** 
Looks like an other rout could be, to have OPNsense firewall, through its unbound dns service i may also achieve this??

As I'm quite new, I understand there are great chances that i totally misunderstood it, please let me know what is best way to achieve it,

---

### Post by TheFu on 2022-08-09
I use a reverse proxy for a number of reasons, but really all yuou need is SNI capable clients and virtual hosts in your webapp server.

Why have 3 separate machines?  I bet all three websites could easily run off 1 system, or inside a VM or container if you need very different environments for each webapp.  Hosting providers use SNI on their shared hosts. Long ago, I used a shared host that had over 3000 domains on the same IP address and same server.  

If you use apache (I do not): [https://httpd.apache.org/docs/2.4/vhosts/name-based.html](https://httpd.apache.org/docs/2.4/vhosts/name-based.html)
Also, you can use different ports on the same IP to access different virtual hosts, that's where a reverse proxy comes in handle ... plus a reverse proxy can filter 95% of the bogus requests before they waste CPU in your webapps.
[https://blog.jdpfu.com/2011/08/18/readers-ask-about-reverse-proxy-servers](https://blog.jdpfu.com/2011/08/18/readers-ask-about-reverse-proxy-servers) tries to explain more.

You probably don't want to host your own DNS.  Over the decades, I've been hacked 3 times. 1 of those times was through DNS that was public, when it didn't need to be.

How DNS, domain registration and a web server are connected: [https://blog.jdpfu.com/2009/08/18/internet-hosting-setup](https://blog.jdpfu.com/2009/08/18/internet-hosting-setup)  At least I think that's what that article does. If it doesn't or isn't clear, I can try to update it.

---

### Post by sairfan1 on 2022-08-10
Its a learning project, I have to setup 3 websites on 3 separate PCs and access them through one Public Static IP what's what I'm trying to learn, for sure good practice and security is important.

> but really all you need is SNI capable clients and virtual hosts in your webapp server.
If i go this route, how can i setup everything, like what i need to install on what hardware?

Just for curiosity how hosting companies handle these kind of situations like do they also use reverse proxy or there are some options in firewall to direct each request? 

I have OPNsene firewall can I configure it to use single ip for multiple hosts?

---

### Post by SeijiSensei on 2022-08-10
Web server software like Apache and nginx use "virtual hosts" to handle requests for multiple names. If you install Apache ("sudo apt install apache2"), it will default to serving up the page /var/www/html/index.html. If you study /etc/apache2/sites-available/000-default.conf, you'll see the configuration file for the default host. The key field is "ServerName". You can have multiple virtual hosts with different server names. 

It sounds like you're just getting started here. There are countless guides on the Internet for these tasks. This one looks pretty straighforward: 

[https://www.arubacloud.com/tutorial/how-to-configure-apache-virtual-hosts-on-ubuntu-20-04.aspx](https://www.arubacloud.com/tutorial/how-to-configure-apache-virtual-hosts-on-ubuntu-20-04.aspx)

---

### Post by TheFu on 2022-08-10
> **sairfan1 said:**
> Its a learning project, I have to setup 3 websites on 3 separate PCs and access them through one Public Static IP what's what I'm trying to learn, for sure good practice and security is important.
If the websites are hosted on 1 system, with a single IP public address, the SNI sorta "just works" with pretty much any browser and any current  (last 15 yrs) web server.
If you insist on using separate hardware, then you'll be the one mandating the use of a reverse proxy.  That reverse proxy can be run on 1 of the systems. All inbound traffic would hit that single box, then be forwarded to the name-based backend .... very much like SNI does, but with different IPs involved for the backend systems.

> **sairfan1 said:**
> If i go this route, how can i setup everything, like what i need to install on what hardware?
I don't understand the question.  What is "everything?"  What "hardware?"  Most webapps will easily run on a minimal system.  It isn't really about the number of websites, unless they aren't static and have bloated requirements.  Something like nextcloud will run easily on a raspberry pi v2 system.  Almost any single Pentium system - like a G3258 from 2015, can easily support hundreds of virtual hosts. It is mostly about storage requirements and bandwidth (your VPS or ISP) will limit things more.  I had 5 huge webapps running on a 2015 Webapp - jellyfine, plex server, wallabag, nextcloud, and calibre.  Nextcloud and wallabag were running inside a single VM. That pentium (dual core) box had 8GB of RAM.  See what I mean by pretty much anything can be used?

If you post an **inxi -Fxxz** for each system along with the webapps running, and traffic loading, we can probably make good suggestions.  I've been running web servers since 1995 at work and home.  Scaling at work has been for about 25K concurrent users with nearly 100 servers involved.

> **sairfan1 said:**
> Just for curiosity how hosting companies handle these kind of situations like do they also use reverse proxy or there are some options in firewall to direct each request? 
Hosting companies can mix and match based on their needs and limitations. There isn't 1 answer.  I mix and match for my home LAN too.  Some websites are direct access using SNI and others are behind a reverse proxy because I needed multiple DBMS and web front-end systems that were load balanced.  For me, the main limiting factor is ISP bandwidth, not system performance.

> **sairfan1 said:**
> I have OPNsene firewall can I configure it to use single ip for multiple hosts?
It doesn't matter what a firewall can do. You should use it.  Extra, non-core features on a WAN firewall are a trap.  Firewalls have bugs and more code means even more bugs, so don't use any of those extra features.  Extra features like a VPN, reverse proxy, storage sharing, are all traps.  I use OPNSense for my WAN firewall-router.  It does 3 things and only those 3 things.
* routing of my public IP addresses with 1-for-1 NAT forwarding
* firewall blocking
* separate management of different subnets.

It is the first line of defense for all my LANs. No way would I use it for anything extra.

Now, if you like, setup OPNSense on a virtual machine inside your LAN and use all the extra features that you like.  Go for it.  I do something similar for my VPN to make it availble to untrusted subnets AND to the internet, but my WAN router is a single-purpose, hardware device.  Simplicity and security usually go together.

---

### Post by sairfan1 on 2022-08-10
Incase I'm using reverse proxy, do i have to add new domains manually by hand or I can use some API to programmatically add new domain?

---

### Post by TheFu on 2022-08-10
> **sairfan1 said:**
> Incase I'm using reverse proxy, do i have to add new domains manually by hand or I can use some API to programmatically add new domain?

By hand.  That's the Unix way.  

Get used to editing text config files on servers and never expect a GUI editor to work.  You'll learn this, eventually. Best to just learn it now and start using vim.  I tried not to use vi for as long as I could when I started in a Unix-centric job.  I'd been a programmer on multiple non-Unix platforms and had the editors I liked and new well.  After 6 months of avoiding vi (we didn't have vim back then), I found myself using the 'vi-mode' in emacs to get work done all the time.  Eventually, I just stopped using emacs and learned vi ... then vim.  It takes an hour to be productive in vim and a lifetime to master.  The sooner you start, the better.  vim is cross-platform and runs on everything.  EVERYTHING.  I've never seen anything except vim on routers, so some minimal knowledge is mandatory.

---

### Post by sairfan1 on 2022-08-15
What if I have requirement to add new domains to reverse proxy programmatically, it does not look practically possible whenever someone point new domain to my server i add it manually by hand, i want to do it programmatically so that i do not have to add it by myself.

that's why i want to learn how hosting companies do it? do they setup dns server? then how that dns server listens to web page request on public ip? 

incase of reverse proxy, does SSL certificates works good?

---

### Post by TheFu on 2022-08-15
Google "Perfect Server"  ... that shows, step-by-step, what one guy things is the perfect ISP server.
> This tutorial shows the installation of an Ubuntu 20.04 (Focal Fossa) web hosting server with Apache 2.4, Postfix, Dovecot, Bind, and PureFTPD to prepare it for the installation of ISPConfig 3.2. The resulting system will provide a Web, Mail, Mailinglist, DNS, and FTP Server.
I use nginx, not apache.
I run bind internally and replicate the records to a paid external DNS. About 20 yrs ago, my DNS server was hacked. It was a minor inconvenience, but ... 
There is no reason since 2002 to run a plain FTP server. This is a huge security failure.
For email, my setup is a little more complex than postfix+dovecot, but my email gateway does run postfix for all in/out SMTP needs.  The real email server that clients use is a monster. That's why I get paid the big bucks.  I used to run a mailing list using slist, but haven't done that in decades. The mailing lists to which I'm subscribed all use mailman. I'm less than impressed based on what the admins running those lists say.
I've never used ISPConfig that I know.  When I put stuff on the internet on someone else's computers, I get a VPS and setup things using my scripts and Ansible.  I suspect there are competitors to ISPConfig.  Google "ispconfig vs" to see comparisons.

But at least you can find an example. Whether that is what you need, what you want, or secure with the suggested settings is a completely different question.

ISPs are built around thousands of custom scripts.  Keeping DNS updated is just 1 of those custom scripts.  Unix/Linux have 50+ text processing tools built-in, which is why we like text config files. Modifying them is really easy.  Learn to use sed, awk, perl, cut, grep, and you'll be well on your way to automating lots of things.  

When you have lots of things, you might want to switch from custom scripts to DevOPS and the tools for that.  I use Ansible.  This lets me manage 1 or 20000 servers. They can be all identical or each a snowflake.  But none of these things gets you passed actually knowing how to manage the DNS records for the DNS server you choose.  See, their isn't just 1 option, there are 20 commonly used DNS servers.  I've used BIND, but for many people, that's overkill, so they choose others.  Sometimes "new" catches their eye or they looked at BIND and decided that modifying the forward AND the reverse lookup files was just too hard (it isn't, but whatever). There's no accounting for taste/preferences. We are all different.

A "good enough" script is 15-30 minutes of work and will run for years.  A better script for use by the world is months of work for a single environment and about a year for multiple environments and OSes.  We all start with "good enough", and as new issues arise, we fix those and do a little cleanup.  Over time, the script gets better and better and better. But no way would anyone start out with the script we have after 10 yrs of improvements. 

We also tend not to share the little scripts that work in our specific environments because making them work for 1 setup is really easy, but making them work for any setup is hard.   TMTOWTDI - [https://en.wikipedia.org/wiki/There%27s_more_than_one_way_to_do_it](https://en.wikipedia.org/wiki/There%27s_more_than_one_way_to_do_it)  While I think my way is brilliant, you would probably find it too complex or too ridged.  See the problem?  

On Unix/Linux, scripting is extremely common, especially for admins.  My system backups happen through scripting, because I wanted some things to happen just before backups and just after backups happened.  I also have the backup command built by the backup script, based on the system.  It is the same basic script for all my systems, but with slightly different directories, commands, logins, and a few other things for each system.  Sometimes I use LVM snapshots. Sometimes I don't.  Sometimes I "pull" the backups and I have some legacy systems that still "push" - which isn't as good for corporate security.

---

### Post by sairfan1 on 2022-08-31
While I was learning reverse proxy, it looks like it can use only one SSL certificate? in that case again i will not be able to use multiple domain

---

### Post by TheFu on 2022-08-31
> **sairfan1 said:**
> While I was learning reverse proxy, it looks like it can use only one SSL certificate? in that case again i will not be able to use multiple domain

Not true.  I have about 20 different certs in use with my reverse proxy.

---

