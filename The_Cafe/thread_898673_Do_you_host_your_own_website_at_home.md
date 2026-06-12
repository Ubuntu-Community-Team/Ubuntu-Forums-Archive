---
title: "Do you host your own website at home?"
date: 2008-08-23
forum: The Cafe
---

### Post by Kernel Sanders on 2008-08-23
I am interested in using a moderately decent computer I have lying around to host my own website on. As such, I was wondering what your experiences are, and how I should go about doing this (from a logistics point of view)?

At the moment I am on 3.5mb broadband with 400k upload from a standard home ISP. Since the upload is the key figure i'm assuming that it will be useless, although I am on a static IP.

So firstly, how do I go about getting a connection that will allow me to host my own website from home? I've tried google, but all I can find is home ISP's. Is this expensive? How much do I need to buy? 10mb upload etc?

As you can probably tell, I am pretty n00bish with all this, so any info on your experiences will be very helpful :)

---

### Post by hessiess on 2008-08-23
Unless you are getting huge amounts of traffic your connection speed is lickly a no issue, however hosting yourself can open you up to all sorts of security issues. so unless you absolutely HAVE to host from home, i.e. your website would take ages to upload. I recommend that you buy some hosting with a dedicated provider. I uset to host my own website, but I moved to payed hosting because it was a pain trying to keep it reasonably secure, and having this computer on 24/7 was using a lot of electricity.

---

### Post by sefs on 2008-08-23
Where I am from they are reputable institutions who host their websites themselves.  And they do this on a meager dsl service, and its not as fancy as what you have there. I wish we had access to 3.5 mbs here lol.

The highest plan we have is 2mb down / 512 k up.  and this is sold as a business solution.  Its the creme of the crop solution.  Most ppl here opt for the 1 mb down / 256 up,   and some ppl host their websites on this.  I would gather thought they are not extremely popular website, but what I can tell you is that these "homebrew" hosted solutions, the sites load at a reasonable speed.  In fact if i did not know that they were self hosted I would think they were on a outsourced hosting.  But again, they are probably not high trafficked websites.

---

### Post by 505 on 2008-08-23
It's not that difficult to host a web site from your home. I have an old laptop that I use as a web server/torrent downloader. If your site receives moderate traffic you can do it with your connection. If you want to proceed, you might want to look into Debian. Ubuntu is based on Debian, so they're similar, but Debian is the more stable and secure one if you have a server to run. Howtoforge has a great [guide](http://www.howtoforge.com/perfect_setup_debian_etch) on how to install all the software.

---

### Post by wdaniels on 2008-08-23
> **hessiess said:**
> Unless you are getting huge amounts of traffic your connection speed is lickly a no issue, however hosting yourself can open you up to all sorts of security issues. so unless you absolutely HAVE to host from home, i.e. your website would take ages to upload. I recommend that you buy some hosting with a dedicated provider. I uset to host my own website, but I moved to payed hosting because it was a pain trying to keep it reasonably secure, and having this computer on 24/7 was using a lot of electricity.

+1

You probably have enough upload bandwidth already, but it will likely cost you more than a decent shared hosting account in electricity alone, plus you lose some bandwidth and have to contend with all the security issues. If you want to do it as a learning experience then fine, but otherwise it's not a good idea.

---

### Post by stmiller on 2008-08-23
You don't need 10Mb up for hosting a website. :)

A ~512k up connection would be more than fine. Don't expect a home-hosted website running on a Pentium II to survive being posted to Digg, but hosting from home works fine for a website.

Some ISPs filter on port 80, so to not allow people to do this. But others do not care.

1and1.com has hosting for $4/month, FWIW. Hosting is cheap these days...

---

### Post by hessiess on 2008-08-23
> Some ISPs filter on port 80, so to not allow people to do this. But others do not care.

easy fix, use a different port :)

---

### Post by freebeer on 2008-08-24
I have a home-based web server running.  It's surprisingly easy to set up.  If you're comfortable with Ubuntu, then that's probably what you should use.  As your needs grow, then you can always change.

As for security, I've found Ubuntu just fine.  I've never had my site hacked or whatever, but I also don't have a ton of traffic and I don't advertise it's existance except to folks I want.  Your mileage may vary, of course.  I set mine up just for the learning experience.  I use it regulalry for various and sundry personal purposes and I'm glad that I have the resource available.

---

### Post by J.T. on 2008-08-24
The main thing you need to host from your computer is a static IP address. Most home ISP's give a dynamic IP address. In order to link a domain name you need a static one, so the IP is always the same.

---

### Post by klange on 2008-08-24
[My site](http://oasis-games.com) runs off of a server sitting three inches to my right, and gets quite a bit of traffic - never had any problems with it. My ISP doesn't block anything - so everything I host works (web server, email, ftp, etc.)

I have Road Runner, $40/month consumer plan with unlimited bandwidth (I hope their Texas experiment fails miserably, I enjoy my unlimited bandwidth). Domain names are run off of GoDaddy, and I use a free name server. My server runs Hardy (desktop, actually, but I've recently stopped actively using it as such, I tend to use my laptop for general use), with Apache, PHP, MySQL, etc. I monitor my network with Snort, use Dovecot w/ Postfix for mail, and even run my own instant messaging service. Every time I'm asked to provide an email address, I use one for my server.

I have constant and complete access to everything, be it from an SSH connection, or by sitting at my desk.

I also host some small projects for other people, nothing that gets much of any traffic.

Speaking of traffic, my forum gets up to a hundred (unique) visitors a day (averaging around 50).



So what are the specs on this "moderately decent" machine you want to us? My server is 1.3Ghz Athlon XP w/ 512MB of DDR RAM and a 40GB HDD (but it's also constantly running a complete Gnome session with Compiz off of an ATI Radeon x800). You should be fine with actually running the server, and hopefully your ISP is lenient enough to let you through.

---

### Post by freebeer on 2008-08-24
> **J.T. said:**
> The main thing you need to host from your computer is a static IP address. Most home ISP's give a dynamic IP address. In order to link a domain name you need a static one, so the IP is always the same.

Um, not quite.  I have a dynamic IP.  You can use a service such as DynDNS.org offers (free) that will take care of that little issue for you.  There are scripts that you can run that checks to see if your IP addy has changed, then will make the appropriate change to DynDNS.org's database.  Conversly, there are some routers that will do this for you as well.

---

### Post by J.T. on 2008-08-24
> **freebeer said:**
> Um, not quite.  I have a dynamic IP.  You can use a service such as DynDNS.org offers (free) that will take care of that little issue for you.  There are scripts that you can run that checks to see if your IP addy has changed, then will make the appropriate change to DynDNS.org's database.  Conversly, there are some routers that will do this for you as well.

That's good to know.

---

### Post by mr_brefast on 2008-09-22
> **WindowsSucks said:**
> 

I have Road Runner, $40/month consumer plan with unlimited bandwidth (I hope their Texas experiment fails miserably, I enjoy my unlimited bandwidth). Domain names are run off of GoDaddy, and I use a free name server. My server runs Hardy (desktop, actually, but I've recently stopped actively using it as such, I tend to use my laptop for general use), with Apache, PHP, MySQL, etc. I monitor my network with Snort, use Dovecot w/ Postfix for mail, and even run my own instant messaging service. Every time I'm asked to provide an email address, I use one for my server.

I have constant and complete access to everything, be it from an SSH connection, or by sitting at my desk.

I also host some small projects for other people, nothing that gets much of any traffic.

Speaking of traffic, my forum gets up to a hundred (unique) visitors a day (averaging around 50).



So what are the specs on this "moderately decent" machine you want to us? My server is 1.3Ghz Athlon XP w/ 512MB of DDR RAM and a 40GB HDD (but it's also constantly running a complete Gnome session with Compiz off of an ATI Radeon x800). You should be fine with actually running the server, and hopefully your ISP is lenient enough to let you through.


Not to totally ask a noob question, but this is basically exactly what I want to do with a desktop I have around my place.  2.4 GHz CPU, 2 gn RAM, onboard video, etc - perfect for setting up and running my own website.  So I suppose I will actually ask 2 noob questions:

1)I am good with Java, familiar with 16- and 32-bit C, familiar with Ruby on Rails, and as a result I have been introduced to HTML.  Does any of that do me any good to set up a site similar to yours, or not?  What language(s) should I expect to need to learn instead?

2)If this website were to be used for the purposes of a small business, is there any restriction to using a home internet connection to run it, or the like?  In fact, is there any registration necessary whatsoever, or is it good to go once it is up?

My thanks in advance, and assuming this all works out, the site will be posted in this thread in about 2 weeks or less.

-Mr. Brefast

---

### Post by kevin11951 on 2008-09-22
used to, until my ISP found out :(

---

### Post by klange on 2008-09-22
> **mr_brefast said:**
> Not to totally ask a noob question, but this is basically exactly what I want to do with a desktop I have around my place.  2.4 GHz CPU, 2 gn RAM, onboard video, etc - perfect for setting up and running my own website.  So I suppose I will actually ask 2 noob questions:

1)I am good with Java, familiar with 16- and 32-bit C, familiar with Ruby on Rails, and as a result I have been introduced to HTML.  Does any of that do me any good to set up a site similar to yours, or not?  What language(s) should I expect to need to learn instead?

2)If this website were to be used for the purposes of a small business, is there any restriction to using a home internet connection to run it, or the like?  In fact, is there any registration necessary whatsoever, or is it good to go once it is up?

My thanks in advance, and assuming this all works out, the site will be posted in this thread in about 2 weeks or less.

-Mr. Brefast

I myself have never used Ruby, but if you're looking to do dynamic pages (or just about anything worth using that you want to build yourself), your knowledge of it should be quite useful.

Your ISP may restrict use for business purposes, even if it isn't for profit. I run my site as an organization rather than a business - we have no employees, we're not registered anywhere, we don't pay taxes - so I'm within my ISP's limits. You may want to look a commercial service, or if you're a risk taker, just go with it, as the commercial service is usually exactly the same but costs magnitudes more (RR is a perfect example, it's hundreds of $ a month for business service, which is generally slower than the standard consumer service)

---

### Post by mr_brefast on 2008-09-22
> **WindowsSucks said:**
> 

Your ISP may restrict use for business purposes, even if it isn't for profit. I run my site as an organization rather than a business - we have no employees, we're not registered anywhere, we don't pay taxes - so I'm within my ISP's limits.

As I understand it, doing no business through the site itself, and merely offering a method of contact and a list of services doesn't qualify as a business, right?  Won't be any commerce done on the website directly, merely a catalog of the services offered by my small, side business.  Think they will have issues with this?


And, slightly unrelated to what I just said,

[http://www.howtoforge.com/perfect-server-ubuntu8.04-lts](http://www.howtoforge.com/perfect-server-ubuntu8.04-lts)

That is what I am going to use to set this all up, for other people looking at this thread.



Also, how do I go about checking if I have dynamic vs static ISP?

---

### Post by Dr Small on 2008-09-22
I do, but my connection is sluggishly slow. So, the website in for the network, and for remotely accessibly webmail.

---

### Post by smartboyathome on 2008-09-22
I'm thinking of hosting my own server, but what I need to know is if a paid hosting server can install eyeos and go-oo. I'm wanting to use those when I am at college and need them, though I can't do local because sometimes I am on the college's computers.

---

### Post by klange on 2008-09-22
Just noticed the information I have posted is horribly outdated.

Finally stripped all the desktop packages from my server. Took the time to properly set up my SMTP with authentication, so I could switch on outgoing mail (my ISP blocks incoming mail from IPs on the DUL, but I don't really care as Gmail, etc. don't - just need to use an alternate method to email my mother). Installed SpamAssassin, decreased minimum point value to 3, enabled prepending of ***SPAM*** to the front of subject lines (because it's easy to filter in Thunderbird).
In other news, my site itself has undergone some renovations. Reorganized our forum boards this past weekend, and we're exploring different variations on a new logo.

My perfect server is:
Web: Apache 2.*
Database: MySQL
Scripting: PHP 5, Python, mod_mono (which I don't have set up for lack of use)
Email: Postfix/Dovecot

---

### Post by david_lynch on 2008-09-22
I've been hosting my own mail, dns and website for some years. I started out on cable modem, but that got really hard, with their policies being what they were, so I went to speakeasy dsl. My connection isn't all that fast but I have 3 fixed IPs and I can do whatever I want. It's all running on modest hardware powered by ubuntu server 8.04.1 these days.

---

### Post by Dr Small on 2008-09-22
> **smartboyathome said:**
> I'm thinking of hosting my own server, but what I need to know is if a paid hosting server can install eyeos and go-oo. I'm wanting to use those when I am at college and need them, though I can't do local because sometimes I am on the college's computers.
You probably can.

---

### Post by wdaniels on 2008-09-22
> **smartboyathome said:**
> I'm thinking of hosting my own server, but what I need to know is if a paid hosting server can install eyeos and go-oo. I'm wanting to use those when I am at college and need them, though I can't do local because sometimes I am on the college's computers.

I'm sure I remember installing eyeos on my servage shared-hosting account not so long ago and it worked ok. But afaik go-oo is not a web application so you would need something like a (virtual) private server with some form of thin-client access (e.g. VNC or NX) with an appropriate client on the college machine to use that remotely. Or is there a go-oo that I don't know about?

---

### Post by smartboyathome on 2008-09-23
> **wdaniels said:**
> I'm sure I remember installing eyeos on my servage shared-hosting account not so long ago and it worked ok. But afaik go-oo is not a web application so you would need something like a (virtual) private server with some form of thin-client access (e.g. VNC or NX) with an appropriate client on the college machine to use that remotely. Or is there a go-oo that I don't know about?

I meant OpenGoo, not Go-oo. Stinking thinking of multiple things at once. :p

---

### Post by Sporkman on 2008-09-23
> **505 said:**
> If you want to proceed, you might want to look into Debian. Ubuntu is based on Debian, so they're similar, but Debian is the more stable and secure one if you have a server to run.

I run my website on Ubuntu Server, it is quite stable & secure.

---

### Post by wdaniels on 2008-09-23
> **smartboyathome said:**
> I meant OpenGoo, not Go-oo. Stinking thinking of multiple things at once. :p

Ah, I see. I had not heard of this OpenGoo before- it looks really nice so thanks for the pointer :D

---

### Post by eentonig on 2008-09-23
> **hessiess said:**
> easy fix, use a different port :)

Sure, and how would the world know how to reach your website?

---

### Post by wdaniels on 2008-09-23
> **Sporkman said:**
> I run my website on Ubuntu Server, it is quite stable & secure.

Agreed, there's no need to switch to Debian, especially not for more casual, personal uses.

---

### Post by Corfy on 2008-09-25
> **kevin11951 said:**
> used to, until my ISP found out :(

I would host my own email/web server in house, but my ISP forbids it, at least without upgrading to a commercial package, which is a lot more expensive than getting a paid hosting plan.

My last ISP also prohibited me from hosting my own server, as does the only other ISP in my area.

---

