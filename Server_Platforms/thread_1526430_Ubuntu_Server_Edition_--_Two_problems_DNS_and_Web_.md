---
title: "Ubuntu Server Edition -- Two problems: DNS and Web Access"
date: 2010-07-08
forum: Server Platforms
---

### Post by reydempto on 2010-07-08
Okay. I literally just stayed up all night long installing/configuring Ubuntu Server Edition using this [handy guide]("http://www.howtoforge.com/perfect-server-ubuntu-10.04-lucid-lynx-ispconfig-2").

Pretty in-depth guide. The first time around I was careless and skipped a step or two, resulting in me having to start over from step one. So I reinstalled Ubuntu Server 10.04, and followed the guide to the letter. This time it went perfectly (I even installed the gnome desktop that I love so much), except for a couple things that I hope you can help me with.

I am no stranger to linux, and I also know how to admin a website. I've bought hosting/domains before, and etc. From what I THINK I understand, I am able to create my own DNS, and thus my own domain name, such as "imadethisdomain.com", hosted on my shiny new server. Am I correct?

So that's problem number one: I need a DNS so I can have my own domain (without having to resort to buying one) 

Problem Number 2: I can only access my 'site' (/var/www) via my local network. Basically on any of my 3 computers around the house I am able to type "192.168.0.240" into a browser and /var/www/index.html will show, confirming that I have done everything right locally speaking.


So how do I 

a) make my own domain name/DNS

and 

b) make that domain accessible outside my home network (I plan on hosting a small forum to archive some live concerts)



I've spent hours tonight attempting to configure bind9, ispconfig, phpmyadmin, mysql, and my router's port forwarding/DMZ functions, all to no avail. I have read countless tutorials and 'guides' in broken English from all over the internet, and I am at my wit's end! 

If you need any more info from me, let me know.

---

### Post by Lucky. on 2010-07-08
Way to go, but you probably went overkill on this!

I'm not sure if I'm reading you right, but it sounds like you want to make a public domain name yourself by having your own DNS server.  Unfortunately it's not possible.  You could definitely do it, but nobody would ever see your server from the net because it wouldn't be registered on any master servers that we all automatically check with.  There's a good reason that we have to purchase/register domain names with a qualified service.  If you created "myexamplesite.com" on your own domain server and and I created "myexamplesite.com" on my own domain server - which one is the real one that the public should go to?  These things have to be regulated, so we purchase domain names that the master DNS servers on the net update from.

HOWEVER!

Once you buy a domain name, you should be able to redirect that site to your own IP address rather than purchasing hosting.  So instead of buying hosting + domain name from a place like GoDaddy like most people do, you buy only a domain name (no hosting) and simply direct it to your personal IP address.

You'd think that would be cheaper, but many sites force you into buying a hosting package along with a domain name...even if you decide to point traffic to your own personal IP address.  Keep an eye out to avoid this if possible.

After you register a domain name, it's as simple as updating your domain registration info to point at your public IP address (the address of your router, not your personal server address at 192.168.etc.etc.)  You'll have to set your router up to forward port 80 to your server's address to work.  You don't even need a DNS server at your house...in fact it's kind of pointless unless you plan on using multiple public IP addresses and servers.  Just buy a domain name, register it to point to your IP address, tell your router to forward traffic to your server, and bam!  You're good.

Wait though!  Don't go buy a domain name yet!

If you're doing this all at home, your IP address is probably dynamic – so it will change over time.  So your web site might run for about a day, week, month, etc. until your IP address changes and nobody can see your server anymore.  Then you'll have to run to your domain registrar's site, update your IP address, wait a day or so until the master servers replicate this info, and THEN people can get back on your site...until you change IP addresses again.  People with dedicated web server pay extra to have static IP addresses, so they don't have this problem.  Hosting from a dynamic IP address at home is a big problem because of this.

The solution to this is to purchase a dynamic DNS service (and have a good router that will support it).  It works like this:  Instead of purchasing/registering a domain name through GoDaddy, Network Solutions, etc...You purchase/register a domain name through a dynamic DNS service like dyndns.org.  This is a neat service...they have a static IP address, so the domain name registration will always point to them.  But as long as they know your address, they'll redirect traffic to your IP address.  If your address changes, you can update it on their site and not have to wait 2 days for the info to replicate.  But even better yet, if your router supports Dynamic DNS (DDNS), you can rig it up to contact your DDNS service periodically and say “Hey!  My IP address has changed – forward to my new address now!”  If you get this set up correctly, it "just works" and you never have to worry about manually updating info yourself.

But even better – if you're still learning this stuff and don't want to shell out money until you know it works, you can register for a free account on dyndns.org or probably many other dynamic DNS services out there.  You don't get a very nice domain name (It's usually something like “yourcustomdomainname.dyndns.org”), but it will suffice until you are confident that this all works.

Again, none of this requires a DNS server at your own house.  In fact, a DNS server at your home won't work for the public at all unless you really really want people to point to your DNS server for a subdomain or something.

Once again, the steps:

1.Purchase/Register a domain name only (no hosting) via some service.  If you're hosting from home, try for a Dynamic DNS Service.  If you have a static IP, buy a domain name from any service that is inexpensive and reputable.

2.If you go with DDNS, make sure your router supports it or you'll still have to manually update IP addresses once in a while when yours changes.

3.Set up your router to either forward port 80 to your web server, or set up a DMZ/NAT to it, or whatever terminology your brand of router uses to open your web server to the public.

4.You're good!

Good luck!

---

### Post by spynappels on 2010-07-08
I am afraid you will still have to buy a domain and use the registrar to point it's DNS entries to your Public IP if it is Static, and your DynDNS domain if it is not.

The you need to port forward port 80 from the router to your server's (static) LAN IP and your site should be world accessible.

---

### Post by reydempto on 2010-07-08
First off, THANKS FOR THE ANSWER! You have no idea how much I appreciate such a lengthy response. I have a few questions about your post though, so I'll try to break it down into quotes.

> If you're doing this all at home, your IP address is probably dynamic &#8211; so it will change over time. So your web site might run for about a day, week, month, etc. until your IP address changes and nobody can see your server anymore. Then you'll have to run to your domain registrar's site, update your IP address, wait a day or so until the master servers replicate this info, and THEN people can get back on your site...until you change IP addresses again. People with dedicated web server pay extra to have static IP addresses, so they don't have this problem. Hosting from a dynamic IP address at home is a big problem because of this.

I already configured a static IP address in ubuntu, does that solve this problem?

I've acquired a free "ath.cx" domain from dyndns already, before I read this. I kind of gave up on the whole make-your-own-dns venture, even if it DID work i didn't care anymore. Too many sleepless hours :P I have a static IP, my router has NAT enabled. I have plenty of security installed besides the router, so DMZ is surely an option...the only problem is I simply can NOT get it to work!

This IP you say I am supposed to have dyndns point to...its the IP that you get from whatismyip.com, right? Because that's the IP I used, and it just gives me a login popup that has nothing to do with my computer whatsoever. it appears to be the login for my ISP's technicians or something... WTF!? Some 'access denied' page powered by "Allied Data Technologies"...it now has a cool domain! the only reason I am pointing out this stuff is because I know for a fact that stuff is not a part of my server. I think I am pointing in the wrong place. This is such a headache...too bad I never give up.

Also, this will only point to that location when I am connected locally. ONce I connect to my neighbor's wifi to try it, or even go on hidemyass, its not found.

HELP!


Also...I have a brand new wireless router. I have forwarded hundreds of ports in my day, but for some reason I can NOT get it to work on this particular model! Its not necessarily port forwarding either. Its DMZ too, in fact-- Any kind of access option just doesn't work. I have tried forwarding ports over and over and over, and testing each one, and still, can't get a single one to open. not for transmission, utorrent, anything.



I don't even need to host a website on this server. I just need a place to put a ton of mp3s (no copyrighted material, all live recordings of local bands), so that I can use my current free hosting to link to them. So all the phpmyadmin and mysql stuff wasn't totally necessary, but it was fun. If there's a better way of making this happen, I am all ears.

---

### Post by noway2 on 2010-07-08
Your doing all the right things and certainly have the right idea.  
Your dnydns should work.  You will undoubtedly have this working shortly and are probably facing a simple error.  Try this: log in to dyndns and there will be an area for your services.  You should see a link or section for your hosts or your domains.  If you select that, it should point you to a page that indicates what IP your accessing dyndns from and what your domain is currently pointing to.  It will also have an update button which will change your domain to point to your address.

Yes, you should be able to get your IP from the whatismyip website and yes this is the one (its the public one) that needs to go to dyndns.  Making your local LAN IP static will help simplify port forwarding, but a LAN IP isn't routable on the public networks so it won't help get traffic to your server.  

The fact that you tried to go to your page via IP and got something else is a little troubling.  Try the step above and if you still have this problem, you may be running into a service blockage on port 80 and may need to contact your provider.

Ultimately, you will want to get port forwarding on your router to work, or get a different router.  You can get around this in the short run by bypassing the router and plugging your PC in directly.  This would at least allow you to test the configuration.  I have never tried running a server on wireless and I understand it is doable, but has some extra difficulties.  You may want to search for info specifically on that subject.

I assume you have Apache installed from the server guide.  You can do a quick check by running "netstat -nta" | grep 80 to see if anything is listening on port 80, if you haven't already.

---

### Post by reydempto on 2010-07-08
Hey, Well I decided to give it a break, my brain is fried for now. And if the site is going to go down repeatedly due to IP changes, then its just not worth it, even for storage. I *will* however continue trying to set this up, just to see if I can. 

Basically I have like 23 year's worth of live shows from one band, and the total size is well over a TB, I figured I could use my large (2x 500gb, 1x320gb) hard drives to help take some of the load, just to host the files, and have the links on my free hosting site... But like I said, due to the random downtimes, I don't see how it would be a solution worth spending the time on. Nothing more annoying than having your ddl cut off at 98% because of some stupid connection error lol!

Do you have any other online mass storage suggestions or way's of distributing these files that would work for me (i.e. cheap to free)? I want my archive to run completely on donations, so free hosting for now, until I build up a decent community. But I am gonna need some storage soon, otherwise this whole archive project is pointless.

---

