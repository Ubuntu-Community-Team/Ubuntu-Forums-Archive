---
title: "Thinking about setting up a web server, a few questions"
date: 2007-11-24
forum: The Cafe
---

### Post by mysticrider92 on 2007-11-24
I have been looking at setting up a server in my home to host a small website for a group I am a part of, and have a few questions about it. 

1) I can set up a LAMP server with no problem, but am very confused about accessing it outside of our router. What do I have to do to set it up with a domain name? I found VirtualHost, will this do what I want?

2) Do I need to pay for a domain name? Or could it be set up with Virtual Host, and just register the name somewhere? I don't think the names I would use are taken, but don't know if it is okay to just use them. 

3) Are there any guides for setting up the router for accessing this, or how hard is it? I want to do this without allowing any access to our other network computers.. 

The website would mostly be meant for people I know personally, so it does not need most of the features of large servers.

Thanks in advance for any ideas or help. 

Sorry if this has been asked before or is in the wrong place, but I can't seem to find the answers anywhere (at least in a way I can understand).

---

### Post by sajro on 2007-11-24
Hey. I can give a quick bit of advice as far as what I know.

To use a domain name, you have to either get a static IP or a dynamic dns service account. The first one is usually offered by your ISP for a small monthly fee. It gives your connection (and consequently network) a unique IP instead of doing the normal thing and giving a new one with each modem reboot.

Dynamic DNS services ask your modem what the new IP address is when you start the modem up (w/o a static IP). It then sets its system up to forward any requests to your domain to your IP. 

As for not accessing other comps on the network, I have limited knowledge. I believe it has something to do with putting incoming HTTP and FTP requests on a certain port and then configuring your router to only allow that port access to the one computer (server).

Domain names do need to be paid for. You can register it at any registrar but use an ICANN accredited one. Then you use the registrar's control panel to make the DNS point to either your static IP or the IP for the dynamic DNS service.

I don't know many guides but check out: [http://www.aboutdebian.com/](http://www.aboutdebian.com/) and (even though I hate Fedora and RH in general it's a good guide) [http://brennan.id.au](http://brennan.id.au) . I suggest a web search for "host your own site" or something similar.

Hope I helped!

PS - Also proud to be a Christian!

---

### Post by HermanAB on 2007-11-24
The main problem is that your ISP will likely block port 80 - the default web server port.  In order to get them to unblock it, you would have to pay about $10 per month more for a business 'server' account.  They will then give you 2 or more static IP addresses.  You can then go to godaddy and buy a domain name and configure their DNS to point to your IP address.  Another advantage is that you will likely get a much faster connection for the extra money.

However, if this is a limited private thing, then you can run Apache on a non-standard port such as port 8080.  Forward this port in your home router and then simply tell your friends to go to the IP Address of your router and port 8080 like this:
[http://w.x.y.z:8080/](http://w.x.y.z:8080/)

The address assigned to your home router will likely remain static for several months at a time.  You could use a free dyndns service, but that may be too much hassle.

Cheers,

Herman

---

### Post by p_quarles on 2007-11-24
There are actually a lot of free domain names available, provided you're okay with a third-level name. Unless you're trying to look professional, one of these should be fine. DynDNS ([link]("http://www.dyndns.com/")) provides both dynamic DNS servce as well as free domain names. 

If you go that route, you'll need to install the ddclient package (in the repos) and then configure it for the service you're using. DynDNS gives you a cut-and-paste config file for their service. 

The difficulty of setting up the router depends on the router's interface. I doubt it will that difficult, regardless of what you're using. All you need to do is make sure that the computer hosting the site has a static LAN IP address, and then configure your router's port forwarding options to send requests on port 80 to that IP address.

---

### Post by mysticrider92 on 2007-11-24
Hmm, I think the static IP or DNS should be easy enough.. 

Finding a low price for domain name registration will be hard though...
Thanks for your help.

[edit] HermanAB: That might be just what I am looking for. I might just try to set that up, since I don't need anything fancy. 

Also, if it helps, the setup would be a DSL router (bellsouth is our ISP) > a Linksys router > actual server. I can set the router up easily enough, but I don't know how our DSL service is set up (my dad is the one who purchased all that, so I can ask him about it..).

---

### Post by sajro on 2007-11-24
I have bellsouth and it's pretty well made for a server. It's DSL Ultra (756Kbps) and can serve most of my things. I only use it to host a MP3 server as a collection of mine and my friends' music so it doesn't consume much bandwidth but neither should your simple HTTP/FTP LAMP setup if only for a few people.

Actually, if you think about it, the normal domain price for a .com, .org, or such is quite reasonable at around $10 US a year.

---

### Post by p_quarles on 2007-11-24
> **mysticrider92 said:**
> Also, if it helps, the setup would be a DSL router (bellsouth is our ISP) > a Linksys router > actual server. I can set the router up easily enough, but I don't know how our DSL service is set up (my dad is the one who purchased all that, so I can ask him about it..).
In my experience, DSL providers are the least likely to block port 80, so you'll probably be fine with that. 

The problem with DSL, though, is that they usually implement separate channels for upstream and downstream connections. My connection is ~1,500 kpbs down, but only 384 kbps up. Depending on the size of the web site, that upload speed won't handle more than a couple visitors at a time with any kind of smoothness. 

There are several sites that will provide free bandwidth tests, too. I don't have any links handy, but I believe one of them was on C|Net. 

Finally, you almost certainly don't have a static IP address unless you (or your family) specifically asked and paid for it. The easiest way to be sure, though, is to give the ISP a call. This is one of the very few questions that won't lead to massive confusion on their end. And, whatever you do, don't tell them you're using Linux (seriously).

---

### Post by mysticrider92 on 2007-11-24
p_quarles: I  have noticed that our download speed (3000+kbps) is much higher than our upload speed (~380kbps) according to speedtest.net. I am not looking for serious performance, and only a few users, so this should be fine. We might look into something different later, but for now... I doubt people would randomly type IP addresses and ports into their browsers, so I think it will be fine. 

I need to figure out what service plan we have, but I think they offer a static IP for free with the plan we were originally looking at (still have to figure this out). 

Thank you for all of your help so far.

---

### Post by andhar on 2007-11-25
I have a server setup on my roadrunner on Port 80 running apache with torrentflux , I used no-ip as the dyndns service and port forwarded the ip of the server after making its IP static. 

It was actually quite easy to do.  You may want to check this out 
[http://www.bit-tech.net/bits/2007/06/05/build_your_own_server/1](http://www.bit-tech.net/bits/2007/06/05/build_your_own_server/1) 

Theres a part 2 at the end of the first one that discusses making availible outside your lan.
good luck.

---

