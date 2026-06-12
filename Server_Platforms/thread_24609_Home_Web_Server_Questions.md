---
title: "Home Web Server Questions"
date: 2005-04-07
forum: Server Platforms
---

### Post by darthsabbath on 2005-04-07
Hi,

This may not be the most appropriate place, but as I'm considering using Ubuntu for this project, I figured it may be as good as any.

I'm wanting to learn how to use Linux as a server, particularly a file, web, and mail server.

I'm considering setting up a small server (maybe an old P3 w/around 256MB RAM) to play on, and am looking into purchasing a domain name.

My questions are basically:

1. Let's say I setup a mail server to send and receive email... when I purchase a domain, will there be anything I will need to look into (when I am registering the domain) to be able to setup mail.domain.com as my mailserver (or ftp.domain.com for FTP)?  Or is all this done on the server itself?

2. As a small web server, would there be any serious hit in my DSL bandwidth?  Basically it might host a personal page/blog, maybe offering web design services as well.  In other words, would the few visitors my site will get experience any massive lag, on both my end and theirs?

Hope I've been clear on this, I'm still very much a newbie, both with Linux and as an admin, but I do want to learn more.  I've tried Googling question 1, but I'm really not sure what keywords I would even need to search for.

Thanks,
Phil

---

### Post by HungSquirrel on 2005-04-07
> 2. As a small web server, would there be any serious hit in my DSL bandwidth? Basically it might host a personal page/blog, maybe offering web design services as well. In other words, would the few visitors my site will get experience any massive lag, on both my end and theirs?
My site I use to host forum images doesn't use very much of its allotted DSL bandwidth at all.  However, downloading large files is kind of slow because I think the max download speed is 60KB/s or something like that.

---

### Post by dataw0lf on 2005-04-07
Answers:
1)  Yes, you'll have to either: run your own Bind nameserver, or (I think it'd be a better idea for someone new to DNS) setup on afraid.org (Free DNS nameservers).  I suggest doing some reading up on DNS and Bind for more information, although afraid.org is pretty self explanatory.
2) Not unless you get slashdotted ;)  Seriously, though, I run my home server (dataw0lf.org) on a 1.5/1.5 up and down line, get a fair amount of traffic, and experience no problems.   Really, unless you're going to be doing some hardcore file serving, that DSL will be just fine.

---

### Post by darthsabbath on 2005-04-11
Thank you guys very nuch for your help! :-)  Very much appreciated!

Phil

---

### Post by bcnstony on 2005-04-13
If you want to keep costs low, you can use dynamic dns, where you get something like yourspecialname.dyndns.org for free. It's what I use for the Ubuntu server in my basement. Read more on dyndns.org.

---

### Post by dataw0lf on 2005-04-13
_if_ your ISP doesn't give you a static IP (which, if they're DSL, they should).  If you're on cable though, you might want to look into DynDns (and most cable modems nowadays have support for them).

---

### Post by az on 2005-04-13
[QUOTE=dataw0lf]_if_ your ISP doesn't give you a static IP (which, if they're DSL, they should).  If you're on cable though, you might want to look into DynDns (and most cable modems nowadays have support for them).[/QUOTE]

Actually, I have had both and they generally are both dynamic.  You need to pay a much higher premium for a static IP.

My DSl provider gave me unlimited bandwith, but there was a little lag in resolving my dynamic dns.  I thought this was normal, but when I switched to cable, using the same dyndns service I had an almost instant connection.  Too bad they blocked port 80!

I was running on port 8080 for a while...

"This may not be the most appropriate place, but as I'm considering using Ubuntu for this project, I figured it may be as good as any."

This is the perfect place for such a question.


"I'm wanting to learn how to use Linux as a server, particularly a file, web, and mail server."

Again, perfect choice.


"I'm considering setting up a small server (maybe an old P3 w/around 256MB RAM) to play on, and am looking into purchasing a domain name."

I had really impressive results with a P1 200Mhz 64 meg ram system running in my basement.  Some CMSs take up a lot of ressources, while ithers take up less.  I was _really_ impressed with Drupal (drupal.org).  It was easily twice as fast as the fourteen others I tried.  (cmsmatix.org)

---

### Post by dataw0lf on 2005-04-13
Huh.  Every DSL ISP I've had provide me with a static IP upon request at no extra charge.  It sounds like you're getting ripped off.

---

### Post by HungSquirrel on 2005-04-14
That's nice of them.  I don't think the major ones do, or if they do, they have a policy against using their service to run servers.  (And asking for a static IP is kind of a giveaway...)

---

### Post by dataw0lf on 2005-04-14
I go through XMission / Qwest DSL.  XMission is quite large (it's the same ISP Maddox uses).  I guess you just have to find the 'good guys'.  Xmission even mirrors the Ubuntu repos (huge Linux advocates over there)

---

### Post by rich on 2005-04-14
Here is my tuppence, or at least the "it worked for me" story.

Mail routing is achieved with an MX record, and URL routing with an A record. When you buy a domain name, what you're actually buying (renting) is the placement of these resource records in a public DNS server. This is something done by your ISP. When you sign up for the account they will ask you what you want the records to resolve to, i.e.

I have a domain name "mydomain.co.uk"
I only have one server, so both MX and A records resolve to
server.mydomain.co.uk which is on IP 62.63.64.65

Obviously you have to tell the box that it's name is "server" and it lives in domain "mydomain.co.uk"

(running your own DNS server [there is one called BIND] will allow resources on your local network to know how to route traffic locally. It will not be queried by someone across the world because (a) you're not trusted and (b) you're not trusted)


Onto the practical side of things : I'm in the UK and I use Zen internet for ADSL with static IP. They're great, although far from cheapest. They also do my hosting, although for a while I used One and One for mail. I wouldn't recommend those guys - people with strong spam filtering used to block their IP because they weren't strict about spammers using their accounts. 

Clearly, this type of decision is about how serious you are, and how the finances stack up. There is a kind of snobbishness I've detected in business about people using mybusiness.freemail.com type addresses. 

As far as learning, I can also recommend the Linux network administrators guide (back when O'Reilly books were quality). It absolutely nails all the core bits. Of course, I may be a bit dull in that I like to know the "how stuff gets from A to B" before I learn how to do eye candy.



Good luck & enjoy.


Rich

---

### Post by dataw0lf on 2005-04-14
The [Linux Administration Handbook](http://www.amazon.com/exec/obidos/tg/detail/-/0130084662/104-3812299-1944727?v=glance) is probably the best reference, by far,  for serious Linux administration.  I highly recommend it to just about anyone who 'wants to figure out how things get from A to B'.

---

### Post by dewey on 2005-04-14
[www.no-ip.com](www.no-ip.com) is another dynamic dns service I've liked.

---

### Post by jdonnell on 2005-04-15
I think there are a few issues that I think should be summed up for you.

Most ISP's I've every had block port 80 so you can't run your webserver on port 80. This means that instead of going to yourdomain.com you'll have to go to something like yourdomain.com:8080.

Most registrars these days allow you to configure your dns on their name servers. I use pairnic.com and I use their control panel to point my domains at my servers ip addresses (btw, these aren't home servers). Basically, you don't need to run a dns server. Free services like dyndns.org are great for home servers. My home server is bloc.homelinux.org which was setup for free on dyndns.

You probably don't have a static IP address with cable or dsl. However, my ip only changes when I reboot my cable modem which isn't often and it's usually because my cat stepped on the surge protector :)

Btw, ubuntu is the best distro for home servers. You get recent versions of software and you can easily upgrade to new versions of ubuntu. I used redhat for years, and I still do at work, but I'm so glad that I have ubuntu now. It's much easier to maintain.

---

### Post by 44922035 on 2006-08-03
I realise this is probably more of an apache question, I just haven't been able to find a good place to ask this question.

I run a few name based virtual webservers.  What I've always wondered is if there is a way to drop requests to just my IP address via port 80, yet have all the other port 80 traffic to my various domain names still function.

I've often wondered this because many ISP's frown on running webservers from a non business account.  This would prevent basically anyone from being able to tell there is a server on port 80 of a said IP.  The only way they'd know is if know the domain name and request it that way.

That's what an ISP guy will check to see of port 80 is open. So do nosey people on the internet.  The best I've done so far is made a fake "page cannot be displayed" page, as I've defined direct connects, without associated names to point to that in my virtual hosts section.  (First virtual host  entry is the default host)

I don't want apache to report a 404 or anything else with a request to the direct IP address.

---

