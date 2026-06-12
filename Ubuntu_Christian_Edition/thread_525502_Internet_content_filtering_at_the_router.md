---
title: "Internet content filtering at the router?"
date: 2007-08-14
forum: Ubuntu Christian Edition
---

### Post by tak1150 on 2007-08-14
Hi,

I'm helping a handicapped neighbor friend set up with a computer (he's 13 y/o). Since they can't really afford internet of their own, I'm trying to extend our wireless network to their house across the street. This person being a teenager and all, I see that it is imperative to not give him internet access without some kind of content filtering.

The reason I'm setting him up w/ a computer is for him to learn Linux and other things and therefore I'd like him to have root privilege on the machine, which means after some learning, he could disable any filtering software like Dansguardian installed on his machine.

So, I'm in need of an alternative. Any suggestion is welcome. I was thinking of activating the internet filter on my router, but I'm not sure how good it is and or whether it will interfere with other things.

Would I need to get another computer so that it will act as the router?
Thanks for your input!

God bless,
Tak

---

### Post by eentonig on 2007-08-14
I think the most flexible solution will indeed be to set up a cheap computer as a proxy.

Most secure will be to have it standing between the Lan and the router, so you can filter out ALL traffic. But you could also set it as a proxy on the LAN (besides the other machines) and configure your router to only allow traffic that is originated from the proxy.

---

### Post by az on 2007-08-14
"This person being a teenager and all, I see that it is imperative to not give him internet access without some kind of content filtering."

I'm a parent and I dissagree.

What do *his* parents think of that?

But to answer your question, the internet filter on your router probably only affects http traffic and as such should not affect anything else.  Usually, though, you need to purchase a subscription to the filtering service.

Dansguardian running on a box in between you and your neighbor should work fine and a free service is available.

---

### Post by tak1150 on 2007-08-14
Thanks for replying!

Do you know of a good how-to for setting up a proxy machine using Dansguardian?
> 
"This person being a teenager and all, I see that it is imperative to not give him internet access without some kind of content filtering."

I'm a parent and I dissagree.

What do *his* parents think of that?

The boy's parents don't seem to know exactly what internet is and it is somewhat difficult for us to talk to them (they don't speak English that well). They just simply seem very happy that we invest in their son.
Even if they were against internet filtering, it is fair for us to offer filtered internet since we don't owe them anything but Christ's love :) (they are not paying for anything)

Tak

---

### Post by pbcartwright on 2007-08-14
here is a good article on timyproxy & dansguardian:
[http://www.linuxjournal.com/article/9044](http://www.linuxjournal.com/article/9044)

and here is a good article on content filter:
[http://www.linuxquestions.org/linux/articles/Technical/What_is_content_filtering](http://www.linuxquestions.org/linux/articles/Technical/What_is_content_filtering)

they may gice you some ideas..

---

### Post by tak1150 on 2007-08-14
Thanks for the links!

I have set up Dansguardian and Tinyproxy on a few machines before, but I do not know where to start to set up a dedicated proxy server to put between the router and a computer.

I imagine you need a special piece of PCI card or something so that there'd be in-coming and out-going ethernet cables.

---

### Post by az on 2007-08-14
> **tak1150 said:**
> Thanks for the links!

I imagine you need a special piece of PCI card or something so that there'd be in-coming and out-going ethernet cables.

You need two ethernet cards.  Or if he will be connecting via wireless, a wireless adapter as the second network card.  The wired card is on the router's network, and the wireless is on a different network (which includes itself and the neighbor).    The computer itself is the router between those two networks.

---

### Post by az on 2007-08-14
You would also need to set up that box as an access point for wireless.

You should just set up content filtering for your whole network.  It's going to be a lot easier to put the dan's guardian box in the DMZ, between the net and your router.  That way your router will still be able to act as the wireless access point.

As well, check with your ISP.  It is usually prohibited to share your internet with your neighbor.

---

### Post by tak1150 on 2007-08-15
> As well, check with your ISP. It is usually prohibited to share your internet with your neighbor.

Goood point! I didn't even think of that. Thank your for pointing that out. I'll check with my ISP (Cox Comm.).

> 
You should just set up content filtering for your whole network. It's going to be a lot easier to put the dan's guardian box in the DMZ, between the net and your router. That way your router will still be able to act as the wireless access point.

That sounds like a good plan. Does the "filter box" need to have decent amount of RAM (and CPU) or can it be a really old computer (like from 1998 )?

---

### Post by az on 2007-08-15
> **tak1150 said:**
> 
That sounds like a good plan. Does the "filter box" need to have decent amount of RAM (and CPU) or can it be a really old computer (like from 1998 )?

If it's a pII or better, you are fine.  If it's a pentium one, you will need to install the server using the alternate cd.  The only difference you will have once you install your applications is that the kernel the server cd installs is the "server kernel" which does not run on a P1.  The desktop kernel (installed by the alternate or desktop cd) runs happily on a P1.

---

### Post by tak1150 on 2007-08-15
> If it's a pII or better, you are fine. If it's a pentium one, you will need to install the server using the alternate cd. The only difference you will have once you install your applications is that the kernel the server cd installs is the "server kernel" which does not run on a P1. The desktop kernel (installed by the alternate or desktop cd) runs happily on a P1.

In a few days time, I'm getting a free home-made computer from a colleague. I have only glanced at it, but it has AMD processor from ~2000-2001 (he said). So hopefully that'll be good enough. (I just found out about this free deal today! PTL!)

Good news!> 
As well, check with your ISP. It is usually prohibited to share your internet with your neighbor.

I have checked w/ Cox Communication and they said that I can do whatever I want w/ my broadband internet b/c I have ownership over it! I was surprised to get this answer, but now I can really go forward w/ this project!
I used to dislike Cox b/c they block TCP port 80 for web server, but I like them now!

Thanks for your help, az!

---

### Post by tak1150 on 2007-08-30
So I finally got the machine! I had to buy RAM and HDD though :(
It's AMD 1.1GHz, 256MB RAM, 40GB HDD

I could not install Ubuntu 7.04 b/c the default xorg setting does not work (memory dedicated to screen is too small); ie I couldn't get the live CD to work. Since I did not want to download alternate 7.04 CD, I went ahead and installed Debian Etch, which has text-based installation and I happen to have the CD already.

Before I put the machine in the DMZ b/w the modem and the router, I wanted to make sure that the network can be bridged.

The PC has one normal ethernet card and I have a USB-ethernet adapter thingy. When I connect the USB-ethernet adpater to the ethernet cable coming from the router, Debian detects the network fine. But when I try to activate both network interfaces (eth0 and eth2), it only connects to eth0 (the normal ethernet interface).

Then I did some Googling, etc, and was thinking "boy, there's more docs and forum support for Ubuntu"

Should I try to do what I'm wanting to do with Ubuntu 7.04 (possibly the server version)? The only thing I like about Debian is that distribution upgrade seems to be smoother (Edgy to Feisty broke a few things and I had to install Feisty fresh).
If so, how can I configure Feisty so that I can have bridged network?
Thank you!

---

### Post by cjm5229 on 2007-09-02
Hi,
I've been wanting to set up a wireless internet server also. I found this web page has a lot of information. [http://linuxgazette.net/141/lazar.html ]("http://linuxgazette.net/141/lazar.html")
I'm still looking for an old computer to use, so I haven't gotten to try it yet.
Carl

---

### Post by tak1150 on 2007-09-17
Hi all,

Good news! Well, besides that Jesus died for our sins and rose from the dead!

I got that "filtering server" set up in my home :)

I basically took az's idea and set up a proxy server in the DMZ of my network. In the process, I ended up writing a how-to article as well. I'll post it in another thread here, but if you don't like to click too many times, [here is the link]("http://taksuyama.com/?p=16#more-16"). I hope that this will be useful for some.

Off topic, but the only problem remaining now is that I have not been able to extend my wireless network across the street (see the posts above) despite the "cantenna" that I have made :(
I think that I have somehow set up the cantenna wrong; when I point it to my laptop, I hardly see any change in the signal strength. I know it's off topic, but if anybody has advice, I'll appreciate it!

God bless,
Tak

---

### Post by shane2peru on 2007-09-20
Tak  I have been reading this thread for the learning aspect of it.  Very interesting.  Now we are venturing off topic a bit and I apologize, but I didn't want to start a new thread just for this simple question.  In theory then with a proxy, everything that connects to the web through the proxy would be protected (as far as firewall, as well as content filtering)  am I correct in assuming this?  This would make a very secure setup for 3 computers in one house that connect to the web (2 linux computers and one windows computer)  as well as making it easier to have my home network all setup???  Because the proxy would eliminate any potential security threat of being attacked from the web side?  (of course nothing can protect stupidity and opening things that will mess your computer up on the user side)  I'm liking this solution as well as the filtering on a proxy level rather than an individual computer basis!  Very nice how to on your web page too, I'm still reading through it.  My only problem is finding a cheap computer here in Peru (I'm a missionary in Peru).  Very interesting.  Thanks for the info!

Shane

---

### Post by tak1150 on 2007-09-20
> **shane2peru said:**
> Tak  I have been reading this thread for the learning aspect of it.  Very interesting.  Now we are venturing off topic a bit and I apologize, but I didn't want to start a new thread just for this simple question.  In theory then with a proxy, everything that connects to the web through the proxy would be protected (as far as firewall, as well as content filtering)  am I correct in assuming this?  This would make a very secure setup for 3 computers in one house that connect to the web (2 linux computers and one windows computer)  as well as making it easier to have my home network all setup???  Because the proxy would eliminate any potential security threat of being attacked from the web side?  (of course nothing can protect stupidity and opening things that will mess your computer up on the user side)  I'm liking this solution as well as the filtering on a proxy level rather than an individual computer basis!  Very nice how to on your web page too, I'm still reading through it.  My only problem is finding a cheap computer here in Peru (I'm a missionary in Peru).  Very interesting.  Thanks for the info!

Shane

Thank you Shane.

I actually made [this thread]("http://ubuntuforums.org/showthread.php?t=553531") for questions like yours and I forgot to place the link in this thread; sorry.

So I will try to answer you question in that thread.

Tak

---

### Post by gwbennett on 2007-09-21
> **tak1150 said:**
> II have checked w/ Cox Communication and they said that I can do whatever I want w/ my broadband internet b/c I have ownership over it! I was surprised to get this answer, but now I can really go forward w/ this project!
I used to dislike Cox b/c they block TCP port 80 for web server, but I like them now! Emphasis is mine.


Some relevant portions of the COX TOS. (I too have cox, though often when speaking of them I spell it differently)
[i]

1) Prohibited Activities. You may not use the Service in a manner that violates any applicable local, state, federal or international law, order or regulation. Additionally, You may not use the Service to:
[/i][snip][i]
    * Resell or redistribute the Service to any third party via any means **including** but not limited to **wireless technology**.

4) User Content. You are solely responsible for any information that is transmitted from your IP address or your account on the web or other Internet services. You must ensure that the recipient of the content is appropriate and **must take appropriate precautions to prevent minors from receiving inappropriate content**. Cox reserves the right to refuse to post or to remove any information or materials from the Service, in whole or in part, that it, in Cox's sole discretion, deems to be illegal, offensive, indecent, or otherwise objectionable.

5) Commercial Use. The Service is designed for personal, non-business related use of the Internet and may not be used for commercial purposes. You may not resell or otherwise charge others to use the residential Service. You agree not to use the Service for operation as an Internet service provider, or for any other business enterprise, **including**, without limitation, [b]_IP address translation_ or similar facilities intended to provide additional access[b]. Cox Business Services offers commercial Internet services.

6) Servers. You may not operate, or allow others to operate, **servers of any type or** any other device, equipment, and/or software providing **server-like functionality** in connection with the Service, unless expressly authorized by Cox.
[/I]

---

### Post by tak1150 on 2007-09-21
> 
Some relevant portions of the COX TOS. (I too have cox, though often when speaking of them I spell it differently)


1) Prohibited Activities. You may not use the Service in a manner that violates any applicable local, state, federal or international law, order or regulation. Additionally, You may not use the Service to:
[snip]
* Resell or redistribute the Service to any third party via any means including but not limited to wireless technology.

4) User Content. You are solely responsible for any information that is transmitted from your IP address or your account on the web or other Internet services. You must ensure that the recipient of the content is appropriate and must take appropriate precautions to prevent minors from receiving inappropriate content. Cox reserves the right to refuse to post or to remove any information or materials from the Service, in whole or in part, that it, in Cox's sole discretion, deems to be illegal, offensive, indecent, or otherwise objectionable.

5) Commercial Use. The Service is designed for personal, non-business related use of the Internet and may not be used for commercial purposes. You may not resell or otherwise charge others to use the residential Service. You agree not to use the Service for operation as an Internet service provider, or for any other business enterprise, including, without limitation, [b]IP address translation or similar facilities intended to provide additional access[b]. Cox Business Services offers commercial Internet services.

6) Servers. You may not operate, or allow others to operate, servers of any type or any other device, equipment, and/or software providing server-like functionality in connection with the Service, unless expressly authorized by Cox.

Wow. Is this true? Is this printed on one of the paperworks you get when you sign up?

I will have try to dig out my papers now. Thanks for the tip.
The information in my post:
> I have checked w/ Cox Communication and they said that I can do whatever I want w/ my broadband internet b/c I have ownership over it!
Comes from a chat conversation with one of the tech support representatives. I am somewhat confused now, but I'll find my papers and contact Cox again.

I suppose at least I'm meeting some of their requirements like "no inappropriate content for minors" thanks to Dansguardian. Nevertheless, I'm quite saddened by this if it's true. I am not totally surprised though. As I said in my post I was surprised to get the response I got from Cox. End of my mourning. Thanks gwbennet.

Tak

---

### Post by Soarer on 2007-09-21
I think they 'expressly authorized' you when you asked the question & they answered it. It doesn't seem to say you have to have it in writing :)

Mind you, IANAL

---

### Post by mikkebe on 2007-09-21
I happily use opendns on my router. (lynksys wrt54g) It was easy to set up and claims to filter 4million sites. I also have dansguardian on the computer. ( [www.opendns.com](www.opendns.com)) REMEMBER NO FILTER IS PERFECT.
Bruce

---

### Post by shane2peru on 2007-09-21
> **mikkebe said:**
> I happily use opendns on my router. (lynksys wrt54g) It was easy to set up and claims to filter 4million sites. I also have dansguardian on the computer. ( [www.opendns.com](www.opendns.com)) REMEMBER NO FILTER IS PERFECT.
Bruce

Bruce   THANK YOU :KS THANK YOU :KS THANK YOU!!! :KS This is great!!!  I went immediately to  [www.opendns.com](www.opendns.com) and set up and account and setup my computer on that account!  Not so much for the filter aspect I was having some serious problems with my DNS settings and couldn't access my own web site because the DNS here in Peru was messed up.  People in the USA could access it fine, so I changed my DNS on my computer and wonderful, now I can access my web page again!!!  The filtering and extras are an added bonus that protect all my computers on my network!  Wow that is great.  Still plan on setting up my proxy server in the future when I get a spare computer but this was just in time for me!  Thanks.

Shane

---

### Post by eric.duveau on 2008-05-11
I have found 2 routers that seems be very effective in content filtering + accountability (monitoring by a partner or parent)

**ZyWALL 2WG**

_[http://www.zyxel.com]("http://www.zyxel.com")_

**iphantom**

_[http://residential.iphantom.com/]("http://residential.iphantom.com/")_

**ZyWALL 2WG: ~$200 Eur + ~$70 per year**
PRO: 
[LIST]
[*]very accurate url database (Bluecoat.com)
[*]real time alerting when blocked sites are accessed
_[p 479 of the user guide]("http://www.zyxel.com/web/support_download_list.php?indexflag=20040906173729&ModelIndexflags=0,420060717102012#")_
[/LIST]

**iphantom: ~$129.95 + ~$59.95 per year**
PRO:

[LIST]
[*]cheaper
[*]easier to configure
[/LIST]

---

### Post by ASquared21 on 2008-05-20
Hi,
I don't pretend to be a disability specialist, but I am a disability advisor, working with the Online BC Provincial School for the Blind primarily. What is your neighbour's disability? I may be of assistance.
Thanks,
Alex A.

---

### Post by tak1150 on 2008-05-23
Something happened to him when he was little (I cannot remember what) and he has very limited use of his legs and somewhat limited use of his hands. Other than that, he is a perfectly healthy teenager. Thanks for inquiring about my neighbor.

God bless,
Tak

---

### Post by hengl on 2010-05-26
Content filtering for him may not be your only problem. He might use up too much of your internet. I suggest a linux based router such as Linksys WRT54GL with third party [Gargoyle ]("http://www.gargoyle-router.com")Firmware. This allows you to setup an internet quota for him and also filter out nasty website for key words, just for him and not hinder your use. If it's too much hassle to get another router, I suggest OpenDNS as an Internet Filter. I have written a review on [OpenDNS as an Internet Filter]("http://www.internet-homedynamics.com.au/blog/opendns-internet-filter-review/")

---

### Post by piston9 on 2010-05-29
Just adding to the many votes for opendns.

We have a server in our house running squid (standard proxy software), and it has it's DNS set to opendns which I manage the access for our kids. 

This allows me as a parent to ensure they can access what I am comfortable with, without restricting everything. For example, my wife can access social sites (facebook, etc), but the kids cannot, as they are through the opendns. I know I can trust my wife :D

If you want to restrict the whole network, just change the DNS settings on the router. Though of course people can get around both of these if\when they wanted it they knew enough (change local DNS settings, done), so the only total way would be to have a server between the internet and the network, which proxied everthing based on your desires - but something like basic opendns filtering is a great place for many people. 

I know as my kids get older I might have to get more complex with the lockdown, but right now it does the job perfectly.

---

