---
title: "questions about hosting webistes ect."
date: 2007-06-16
forum: Server Platforms
---

### Post by hockey97 on 2007-06-16
Hi I was woundering I seen in apache the the name server option, and could use that name in my insternal network,  is it possible to do the same with the outside world,  like instead of the ip address you would use example  as the name of the server so if the perosn on the web type 

example they would go to your website ect,  so their is no [www.example.com](www.example.com) it's just a name you type.

can that be done so you can avoid domain name register??

---

### Post by dupa on 2007-06-16
> **hockey97 said:**
> Hi I was woundering I seen in apache the the name server option, and could use that name in my insternal network,  is it possible to do the same with the outside world,  like instead of the ip address you would use example  as the name of the server so if the perosn on the web type 

example they would go to your website ect,  so their is no [www.example.com](www.example.com) it's just a name you type.

can that be done so you can avoid domain name register??

you can setup a DNS server on your machine, so that in your LAN you can use everykind of domain name you want, but if you want that your domain name will be accesible from outside the LAN, you should register a true domain name.

---

### Post by Frosty Cold Drink on 2007-06-16
> **hockey97 said:**
> Hi I was woundering I seen in apache the the name server option, and could use that name in my insternal network,  is it possible to do the same with the outside world,  like instead of the ip address you would use example  as the name of the server so if the perosn on the web type 

example they would go to your website ect,  so their is no [www.example.com](www.example.com) it's just a name you type.

can that be done so you can avoid domain name register??

No.

The various server name options in Apache are only for self-refrence, certian headers, and virtual host lookup.

---

### Post by hockey97 on 2007-06-16
Ok.. then in my router I have 2 static dns ip's what does that do??

So I need to have raw access to the internet to have my DNS to be seen outside my network??

I see these companies that host website's that they offer to host domain names how are they able to do so if you only could if your a registar??

---

### Post by Frosty Cold Drink on 2007-06-16
> **hockey97 said:**
> Ok.. then in my router I have 2 static dns ip's what does that do??
Those IP addresses are there to tell any computer hooked up to your router what servers to contact if they want to look up domain names.

> So I need to have raw access to the internet to have my DNS to be seen outside my network??
I don't know what you mean by "raw". I will tell you that you will need a staic IP address, and the assistance of your ISP in order to host a public DNS server. (This isn't entirely true, but if you want to have a DNS server be authoritive for a domain, it is.) If you host DNS for your domain name, you still have to get the domain to begin with, and therefore have to register.

> I see these companies that host website's that they offer to host domain names how are they able to do so if you only could if your a registar??
They are either registrars themselves, or use an upstream services like OpenSRS to re-sell domain registration to customers. They have properly set up public DNS servers which can be authrotive for a domain.

(There are a couple of holes in what I have said above, and I'll leave it to someone else to fill in if they feel like its necessary.)

In short, if you want some random person to be able to type a name in a web browser and get your web site without any special configuration, you are going to have to pay somewhere.

---

### Post by hockey97 on 2007-06-16
It's not the money I don't want to pay it's having less control, I mean if I advertise my website and spend big $$$ on that public dns thing breaks down or the people that run it get's bribed from one of my competitors, and then shut off my service without informing me can cost alot.

I am basicly saying If I have to spend then it better be worth it and I mean like if I have my companie's website made and I find out that the people that host my dns got bribed from a company that does that same thing, and want to stamp me out,  so I would hate to find

something like that out.

I mainly want full control over my whole webpages ect.

well I have been looking around to start an ISP business.

---

### Post by Frosty Cold Drink on 2007-06-16
> **hockey97 said:**
> It's not the money I don't want to pay it's having less control, I mean if I advertise my website and spend big $$$ on that public dns thing breaks down or the people that run it get's bribed from one of my competitors, and then shut off my service without informing me can cost alot.
This would be against registrar accreditation requirements. As far as I know, only one registrar has ever lost accredidation. Your own solutions are FAR more likley to break than the rest of the DNS system. No offense, but the fact that you ask about this means you don't have the knowlege or ability to pull of something comprable.

What is likley to break (and breaks often) are ISPs (sometimes regional) DNS servers. These are for use by thier customers and there is nothing you can do about it.

> I am basicly saying If I have to spend then it better be worth it and I mean like if I have my companie's website made and I find out that the people that host my dns got bribed from a company that does that same thing, and want to stamp me out,  so I would hate to find something like that out.
Well I suppose its possible. Only a lousy web host would let that happen.

> I mainly want full control over my whole webpages ect.
So get a decent registrar, colo a DNS server and a web server (or put them on the same box if you must) in a datacenter somewhere. That is about as much control as you can safeley get. You can set up your own datacenter, but if you are so concerend with problems you'll obviously want multiple redundant guarenteed-bandwidth internet connections, backup power generation, security, and so on... If you really want to do that on your own, go ahead, but a decent data center already has that ready to go.

---

### Post by NeoGreen on 2007-06-17
You can use dynuDNS, they offer free domain name services.

---

### Post by chris.zeman on 2007-06-17
If you simply want reliable hosting, then your best bet is to find a reliable web host with redudant connectivity. I use DreamHost and have had very little trouble. I've had others that had absolutely terrible service. I won't mention them, though, as I've been a satisfied DreamHost customer for several years and those other hosts MAY have improved in that amount of time. I see no reason to make an attempt at tarnishing their reputations NOW in this forum.

It sounds, though, that control is what you're after. You only have 2 static I.P. addresses. Unless you plan on using a third-party DNS service, you'll need to get yourself a third address. You could run your own primary nameserver and use a third-party service to act as your secondary nameserver. If you're up to the task of configuring and maintaining your own local server, and have sufficient bandwidth for your application, then do it! :) I don't mean to make it sound difficult; it really isn't once you get the hang of it. Otherwise, you might want to consider renting a dedicated server with a web host. 

I operate a web server at work and at home. I'm not an expert, but I follow how-to's, tips, and tricks I find online. I use a third-pary Dynamic DNS service (DNS Park) with my dynamic IP addresses. Everything seems to work great for me. I have a PHP-enabled web server, mail server, and all the good stuff. Sure, it isn't done by a professional, but it doesn't really need to be so long as it works. I'm learning more all the time, and I document every step of my setup process. I enjoy doing it because I learn a lot about Linux and some of the apps that run on it. I enjoy operating my own server where I have full control and the ability to deploy applications wouldn't do me any good on my DreamHost account, such as VPN and what-not. 

Good luck!
Chris

---

### Post by NeoGreen on 2007-06-18
Hey Chris,
You don't happen to have any of those links handy?  I am just finished installing Ubuntu 7.04 LAMP, phpmyadmin, and webmin.  I want to be able to remote connect to my server from outside and view my website from outside my network.  any advice would be appreciative.

thanks

---

### Post by chris.zeman on 2007-06-18
Sure thing!

There are three sites I mainly use:
THIS ONE!!! :D
[http://howtoforge.com](http://howtoforge.com)
[http://ubuntugeek.com](http://ubuntugeek.com)

I just Google for anything else I want to do that isn't covered by any of those sites. 

My project right now is re-doing my home server. I have used 2 how-to's at howtoforge.com to configure my servers, but each one offers something the other doesn't. I need a combination of the two, so I'm making a list of everything I need, doing it, and writing my own how-to. I can then publish it and get feedback from others on what I could or should do differently. I think that's the best for me to learn anyways. I can also easily replicate what I've already done in case I really foul things up along the way somewhere and start over. :) 

My goal is to come up with something useful for the home or small-business user to go by. I fall into both categories. Some of what I want to incorporate are:
LAMP Server
Mail Server
VPN Server
SAMBA Server
Jabber Server
Streaming Media Server
Redundant Internet Connectivity
Internet Sharing

It'll take me a little time to get it done, but at least I'll learn some more. :p I've been learning more by being nit-picky than simply following a how-to and deploying the server.

Chris

---

### Post by chris.zeman on 2007-06-18
I forgot to ask...

What specifically are you having a problem with? Is your server connected directly to the internet or through a router? You'll need to forward the appropriate ports through a router, or make your server a DMZ host.

Chris

---

### Post by hockey97 on 2007-06-18
I am right now trying to get apache2 to work, I am using webmin, but I got 2 apaches one is ver 1.3 and the other is ver 2  the ver 2 dosen't work at all, I get an error message in webmin 

saying that the server is not already running,  that's when I click the button to turn on the server,

and it's not on in my computer.

the ver 1.3 works no error's just that I can't see it on my other computers only on my computer with the server.

on the other computers I type in the internal ip of that computer with the server and it then 

takes to me google or msn search searching the ip address.

I can't access anything really even webmin I can't access it on other computers on my network.

I type in myip:10000 for webmin on the other computers and then it takes a while looking and then put's a error page of my ie  the basic one where when you don't have internet or a good connection that page.

I been playing with apache for a month trying to get it to work.

but never did, that's why yesterday I got frustrated and deleted apache and installed it again 

but didn't work,  this is where I got the 2 different versions.

I once had it working a long time ago, the thing's really started when after I installed squid

proxy and cvs server.

I deleted squid proxy and cvs server however I still think their is  some files left.

I think when I installed cvs it said something about it may conflict with apache do you want to continue the install.

I think I seen this, not fully sure.

I know either it's the installation or the config's I had to do for the installation.

but I knew after I installed the  apache worked just didn't see it on my other computers.

---

### Post by chris.zeman on 2007-06-18
Hmmmmmm....I wonder if it would just be easier at this point for you to start over with a fresh LAMP install. 
I've never messed with squid, so I'm not entirely positive what effect it might be having.

Chris

---

### Post by tdrusk on 2007-06-18
Well, I can't help that much, because when I set up my server I just followed a guide and worked and worked.

My only tip for you is to keep on trying. It took me almost a full day to get what I wanted. In the end you will be happy with the outcome. So, I guess as motivational help, just keep on truckin' you will get it!

---

### Post by NeoGreen on 2007-06-18
Awesome sites Chris.  thanks.

---

### Post by hockey97 on 2007-06-18
Hi thanks for the comments.

I started all over, and now it works, I tested it and I can see it on my network.

squid proxy did some type of config on my system, that's what screwed it up.

Now Going  to  work on getting an e-mail service going.

---

