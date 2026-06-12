---
title: "Ubuntu cloud proxy, server, dansguardian, squid3, Apache"
date: 2014-11-20
forum: Server Platforms
---

### Post by squarethumps on 2014-11-20
Hello, I'd like to set up an ubuntu server, running in the cloud, with dansguardian, so that the laptop computers that my young daughters travel with can always have relative safety from the horrible things on the internet.  :)
I would, after that, like to set up an actual web server with Apache to serve up my own custom home page and point my domain(s) to it and all that happy web server jazz. 

I currently have a virtual machine running Ubuntu x64 13.10 in the "cloud".

I've installed squid3 and dansguardian according to this : 
[https://help.ubuntu.com/community/DansGuardian](https://help.ubuntu.com/community/DansGuardian)

but obviously it's not working or else I wouldn't be here :) 

Admittedly I've got some things to learn about proxy servers, dansguardian, squid and Apache.

At the moment I believe that squid3 is running and dansguardian is running from ps -ef commands grepping for processes with those names, which is successful.  When I setup a browser to use my cloud IP address as the proxy server, I'm getting the "proxy server is refusing connections" error message.

I'd like some direction as to where I should look first to correct these issues and help me accomplish my goals.

Many Thanks.

---

### Post by nerdtron on 2014-11-20
First off Ubuntu 13.10 is no longer supported. If you are using a server, better install 14.04 or the older one 12.04

Next. What you would like to do is a bit complicated if you don't have much experience and understanding on the components you want to put up together. That being said I haven't configured everything myself so you can disregard my opinion.

Now my question is are your kid's laptop using windows? And the sole purpose you want is to have some kind of web filter for not accessing suspicious/malicious sites?
I used [http://www1.k9webprotection.com/](http://www1.k9webprotection.com/) in the past and it's quite effective. Even blocking some virus ridden sites.

---

### Post by squarethumps on 2014-11-20
Thank You for the response ! 

hmmm .. I didn't realize that 13.10 was not supported.  I will probably upgrade to 14.04, since I know of no reason why I should require the older version.

Let's then pretend for this thread that, no one in my house uses Windows.  Edubuntu is the preferred OS for my kids.  Let us also pretend that I actually have to some degree used all of those programs in the past successfully, albeit within my own network.  I guess we can actually stop pretending on all of that. 

My smallest kids have only ever used ubuntu, and my teenagers are being weened off of Windows.   My previous network was a smoothwall firewall with a dmz, where I ran my home "server" that was really a desktop running some server apps.  I'd followed instructions in the past to set up squid, dansguardian and Apache and had them all running successfully and numerous other PC's ( linux and Windows both ) configured to use that machine as a proxy to the internet.   I was able to monitor each static IP address and I knew exactly which computers had tried to look up "Jonas Brothers no shirt", much to my disapproval.   I had dansguardian setup to basically block everything except what I explicitly allowed, and I ran it on the dmz to allow myself ( without having to set up pinholes ) to configure any new sites that were needed, even while I was away from the house through remote access via ssh. 

It's been about 6 years since I had set all of that up, and obviously I've forgotten some of it, but I think I still have the general idea of how it all works.  If I was to have the proxy running in the cloud as I've suggested, I realize that I wouldn't have the granularity of knowing exactly which computer was visiting which IP address, but I was trying to get this up and running for the temporary.  I've moved houses which is why I don't have the same network setup as I used to, but I do intend to setup another firewall and have a similiar setup to what I'd had previously.  I just wanted to try running the proxy in the cloud so the laptops would work when they had them out.   Maybe have different proxy configurations for different network connections, and run one of these setups at home and one out in the cloud.  

So I suppose I can do a little more digging and see why squid3 isn't accepting the connections and maybe come back with a bit more specific questions. 

As far as some 3rd party proxy .. not really interested .. I'll keep thumping away at this since I view it as not only a necessary thing for my kids, but a honing of my skill set as well.

---

### Post by houstonbofh on 2014-11-21
Once you start over with 14.04 you will find some problems have gone away.

But when you finish, make sure you secure your proxy.  Open proxies are actively sought on the Internet, and usually for not so good reasons.

---

### Post by squarethumps on 2014-11-24
I have started over with 14.04.  

squid3 and dansguardian are up and running, but I don't think they are playing nice with each other yet, and I'm sure that's because I haven't quite learned how to configure squid3 to use dansguardian.  

my first goal was to get squid up and functioning as a proxy and then to start to use dansguardian as the filter.  I thought this would be a more useful learning process.

I'm getting Access Denied from my squid proxy when I try to navigate to any webpage.   

The error message, at the bottom, says that the message was generated ( date ) by myproxy ( squid/3.3.8 ).

So I know that squid is at least responding to the request.

I'm now investigating the rest of the tutorial and trying to see what I need to finish to have squid allow the requests, but I wanted to say that yes, with 14.04, at least the processes are running.

> But when you finish, make sure you secure your proxy.  Open proxies are  actively sought on the Internet, and usually for not so good reasons.


secure your proxy .. what exactly do you mean by this ?

---

### Post by houstonbofh on 2014-12-15
If I can connect to your proxy from my IP address I can do all kinds of things that only trace back to you...

---

### Post by squarethumps on 2014-12-15
> *If I can connect to your proxy from my IP address I can do all kinds of things that only trace back to you...*

but won't the proxy logs have a record of your connecting to it from your IP address ?

---

