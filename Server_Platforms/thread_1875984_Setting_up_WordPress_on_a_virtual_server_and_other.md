---
title: "Setting up WordPress on a virtual server and other shenanigans"
date: 2011-11-05
forum: Server Platforms
---

### Post by sffvba[e0rt on 2011-11-05
Hi all,

_**PRE-PREQUEL**_

So I am very much a user of Ubuntu Desktop and while I have dabbled with CLI and some troubleshooting I am very much a newby when it comes to Linux, especially servers (I had been doing the MCSE track more than 10 years ago so yes, I know very little).

I have many questions, many issues so I guess the best would be to state my current situation, get some advice and then tackle specific issues as they arise.

**_PREQUEL_**

My current situation is as following:

I am using a HP530 Notebook running Ubuntu 11.10.  I have installed Virtual Box in it and installed Ubuntu 11.10 Server on it.  In this server I have installed apache, PHP, mySQL and also WordPress.  I have gotten to the point where I can edit WordPress etc. via my Browser on my Host system as well as a Windows box I have on my home network when I specify the IP address of my Server.

My home network connects to the Internet via the above mentioned Windows box that has Internet Connection Sharing enabled (just some info in case).

I have now bought a domain name through GoDaddy. (and even registered with DynDNS but I have no idea why yet :p)


_**QUESTIONS**_
[LIST=1]
[*]Will I me able to use my Server to host my blog with the current method that I am connecting to the Internet?
[*]Any links and advice on setting up my domain to work with Apache as I don't even know where to start and Google has just served to confuse me even further?
[*]I don't have a static IP address from my ISP, so I have heard about dynamic DNS, but as you can guess that just causes my brain to implode at this point, how would I go about incorporating that into my current situation?
[/LIST]

I am going to use this as my own*** Mini-Mega thread*** till I get this sorted out.

Answers will be posted as I get them set-up.


Cheers
404

---

### Post by Lars Noodén on 2011-11-05
> **not found said:**
> 
[*]I don't have a static IP address from my ISP, so I have heard about dynamic DNS, but as you can guess that just causes my brain to implode at this point, how would I go about incorporating that into my current situation?


I've been playing with DynDNS, too, lately.  Depending on your ISP, sometimes the DynDNS entry can get out of sync with your actual IP number.  In that case your domain points to he wrong address for less than 4 hours.

---

### Post by stephenmac7 on 2011-11-05
> **not found said:**
> Hi all,

_**PRE-PREQUEL**_

So I am very much a user of Ubuntu Desktop and while I have dabbled with CLI and some troubleshooting I am very much a newby when it comes to Linux, especially servers (I had been doing the MCSE track more than 10 years ago so yes, I know very little).

I have many questions, many issues so I guess the best would be to state my current situation, get some advice and then tackle specific issues as they arise.

**_PREQUEL_**

My current situation is as following:

I am using a HP530 Notebook running Ubuntu 11.10.  I have installed Virtual Box in it and installed Ubuntu 11.10 Server on it.  In this server I have installed apache, PHP, mySQL and also WordPress.  I have gotten to the point where I can edit WordPress etc. via my Browser on my Host system as well as a Windows box I have on my home network when I specify the IP address of my Server.

My home network connects to the Internet via the above mentioned Windows box that has Internet Connection Sharing enabled (just some info in case).

I have now bought a domain name through GoDaddy. (and even registered with DynDNS but I have no idea why yet :p)


_**QUESTIONS**_
[LIST=1]
[*]Will I me able to use my Server to host my blog with the current method that I am connecting to the Internet?
[*]Any links and advice on setting up my domain to work with Apache as I don't even know where to start and Google has just served to confuse me even further?
[*]I don't have a static IP address from my ISP, so I have heard about dynamic DNS, but as you can guess that just causes my brain to implode at this point, how would I go about incorporating that into my current situation?
[/LIST]

I am going to use this as my own*** Mini-Mega thread*** till I get this sorted out.

Answers will be posted as I get them set-up.


Cheers
404

First word of advice: Don't use Apache. Use cherokee.
Second word of advice: Although we all love Ubuntu :D if you're going to use Virtualbox you might as well use Arch (and no, I'm not asking to say, "That's it! I'm switching to Arch"

Now, for the real thing: Are your A records set up? Are you going to run something besides wordpress?

---

### Post by spy_1134 on 2011-11-05
I run a server of my own with Ubuntu 10.04.3 LTS and a GoDaddy domain name.

I host my own DNS with BIND as well, but that isn't required and will likely be a little confusing.

A drawback to hosting a server with a dynamic IP address is that DNS isn't intended for computers with dynamic addresses. Because of that, if your address changes then you will have to update all of your DNS records for your domain name as well.

The only service I know of that updates your DNS records automatically is DynDNS, and you have to pay for their service.


I haven't had much trouble with hosting a server on a dynamic address, personally. My address stays the same almost constantly. The only time it has changed was when I moved the server over to my new house recently. So long as you don't move the server or lose your internet connection for longer periods of time then you should be fine.

EDIT:
 Cherokee looks nice, but I would still stick with Apache. It looks like a somewhat new project and Apache has been around for about as long as the internet itself.

I read through your post again and saw that you are running Ubuntu Server within Ubuntu Desktop...

My question: Why?
You might as well just install the server packages to your native Ubuntu host. Also, why a notebook for a server? I picked up an old refurbished dekstop from a local volunteer program called Free Geek for about $150 and that has served me flawlessly ever since.

---

### Post by Dangertux on 2011-11-05
The answer is yes it can do all of this. That being said I would consider making a couple of changes if I were you.

Apache is fine, it's more mature, more secure and generally better maintained than cherokee.

Ubuntu server is also fine. Arch is cute, but it's also not mature enough to be a server OS (IMO) if you are going to run a server it needs to be one of the following (again this is opinion) : Debian, RHEL, CentOS, Slackware, Gentoo or Ubuntu. My reasoning here, they are actually on top of it with security patches.

Also I would suggest against using a notebook as a server. You can get a used desktop machine for 40 bucks off ebay. Use that instead. 

If you're going to virtualize it on anything, don't use Virtual Box. I would recommend Xen or KVM personally.

Also for DNS I actually like no-ip.com if you're going to run that, they offer really cheap domain names and the client is much more reliable then the dyndns client (it's in repos)

---

### Post by stephenmac7 on 2011-11-05
I agree with not running it on a laptop, you might even be better off using wordpress.com (with their DNS). Although Apache MAY be more secure it is much easier and faster to use cherokee. Arch is actually faster with security pathches.

---

### Post by sffvba[e0rt on 2011-11-06
> **Lars Noodén said:**
> I've been playing with DynDNS, too, lately.  Depending on your ISP, sometimes the DynDNS entry can get out of sync with your actual IP number. ** In that case your domain points to he wrong address for less than 4 hours.**

I think that something like that would be the least of my worries at the moment.

> **stephenmac7 said:**
> Second word of advice: Although we all love Ubuntu :D if you're going to use Virtualbox you might as well use Arch (and no, I'm not asking to say, "That's it! I'm switching to Arch"

Now, for the real thing: Are your A records set up? Are you going to run something besides wordpress?

Arch as a server... not thanks (but thanks for the suggestion)

Records? All I have at the moment is apache server running and I have registered a domain... I have not set up anything on either side yet.  

The initial idea is for a blog but then it can and will expand for sure.

> **spy_1134 said:**
> The only service I know of that updates your DNS records automatically is DynDNS, and you have to pay for their service.

I read through your post again and saw that you are running Ubuntu Server within Ubuntu Desktop...

My question: Why?
You might as well just install the server packages to your native Ubuntu host. Also, why a notebook for a server? I picked up an old refurbished dekstop from a local volunteer program called Free Geek for about $150 and that has served me flawlessly ever since.

I don't mind shelling out a few $ if it works (then again if I don't have to so much better :))

The only reason I have the setup on my laptop is to test it and to play and to see if I could.  Now that I have WordPress working I thought I would continue playing and learning and see if I could actually get it working as intended over the Net...

> **Dangertux said:**
> If you're going to virtualize it on anything, don't use Virtual Box. I would recommend Xen or KVM personally.

Also for DNS I actually like no-ip.com if you're going to run that, they offer really cheap domain names and the client is much more reliable then the dyndns client (it's in repos)

The only reason I use VBox is because it is known to me and like stated above, this is all for learning a bit about servers, WordPress and just seeing what I am able to do.

no-ip.com, I will have a look... Thanks for the link.

> **stephenmac7 said:**
> I agree with not running it on a laptop, you might even be better off using wordpress.com (with their DNS). Although Apache MAY be more secure it is much easier and faster to use cherokee. Arch is actually faster with security pathches.

I will stick to Apache and Ubuntu for now (the learning phase) but thanks for the input!


To all responders thanks thus far.  As it stands I am still stuck at the same position I was at time of the OP...


Cheers
404

---

### Post by sffvba[e0rt on 2011-11-06
Crawl before you can walk... walk before running...

I think I jumped in on the deep end without the fundamentals in place :/

I will keep checking this threads for any more pearls of wisdom but think I will start this experiment over and take it a bit slower and try to understand more :)


Cheers
404

---

### Post by Dangertux on 2011-11-06
Since you're saying your still stuck at the point in the Original post , I'll try to answer those questions more clearly.


1. Yes, port forward the desired ports (80 and 443 I presume) to the VM running the apache (note the VM's network adapter has to be in bridged mode)

2. As long as you're running one domain the port forward should work fine. Make sure that the Apache server is bound and listening to the right ip (not localhost) but 192.168.1.5 or whatever or 0.0.0.0 (all interfaces). After that just make sure your dns is updated via your dynamic dns update client. At that point whatever.dyndns.com should point to your VM and webserver.

3. This was pretty well covered in 1 and 2.


As far as Apache configuration goes, it's pretty decent out of the box if you're not using virtual hosts (which you shouldn't need to if you only have one domain for your blog at this point). You can do more to secure it, by using mod-security, hardening your apache install or your php and mysql installs. However, I would focus on getting it working before doing this since you said it's a learning curve for you.

I hope this helps answer your questions.

---

### Post by sffvba[e0rt on 2011-11-06
> **Dangertux said:**
> Since you're saying your still stuck at the point in the Original post , I'll try to answer those questions more clearly.


1. Yes, port forward the desired ports (80 and 443 I presume) to the VM running the apache (note the VM's network adapter has to be in bridged mode)

2. As long as you're running one domain the port forward should work fine. Make sure that the Apache server is bound and listening to the right ip (not localhost) but 192.168.1.5 or whatever or 0.0.0.0 (all interfaces). After that just make sure your dns is updated via your dynamic dns update client. At that point whatever.dyndns.com should point to your VM and webserver.

3. This was pretty well covered in 1 and 2.


As far as Apache configuration goes, it's pretty decent out of the box if you're not using virtual hosts (which you shouldn't need to if you only have one domain for your blog at this point). You can do more to secure it, by using mod-security, hardening your apache install or your php and mysql installs. However, I would focus on getting it working before doing this since you said it's a learning curve for you.

I hope this helps answer your questions.

Thanks.  Will give it a go and report back.


404

---

