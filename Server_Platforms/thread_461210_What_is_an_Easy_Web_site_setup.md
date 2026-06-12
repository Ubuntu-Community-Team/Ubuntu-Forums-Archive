---
title: "What is an Easy Web site setup?"
date: 2007-06-01
forum: Server Platforms
---

### Post by victory2007 on 2007-06-01
I am in over my head.  I have no idea what i am doing and am looking for some direction.  I have never setup a web site server before and realy need step by step instructions.  Can any one help me.  I am running ubuntu 6.06 server and would like to have my own local web server instead of paying some one else to host my web site.  Thanks

---

### Post by snoop on 2007-06-01
Try this guide: [http://ubuntuguide.org/wiki/Ubuntu_dapper#Apache_HTTP_Server](http://ubuntuguide.org/wiki/Ubuntu_dapper#Apache_HTTP_Server)

---

### Post by victory2007 on 2007-06-01
I already installed apachey and got the local host page, but now how do i get my web page that i created to display onto the web.  Can i set up a specific web address like ([www.webaddress.com](www.webaddress.com))  Thanks

---

### Post by dfreer on 2007-06-02
Check out DynDNS or no-ip. That will help you register a domain name, and if you have a dynamic IP address (you probably do), will provide the DNS servers and some tools to track your dynamic IP.

Also, if this is just a local server, you could make a DNS server so all local traffic looking for [www.google.com](www.google.com) or whatever name you want will be directed to your site. You can do this manually on each machine by editing /etc/hosts (linux), or C:\windows\system32\drivers\etc\hosts (windows)

---

### Post by obimeister on 2007-06-02
For a decent www site hosting you need to register domain name, your local ISP is good place to start asking. Then you need static public ip-address where to bind that domainname, again ask your ISP. Then do you plan to host your domain name on your own DNS server? If yes you also need to install and configure BIND. And then how much traffic moves on your www server, do you need faster internet connection? If you get all this you probably also need NAT firewall to get other computers in your network to internet.

---

### Post by yacine on 2007-06-03
I have similar questions about web servers. I installed the ubuntu server edition following instructions in this website: [http://www.howtoforge.com/perfect_setup_ubuntu704](http://www.howtoforge.com/perfect_setup_ubuntu704) for Dapper see: [http://www.howtoforge.com/perfect_setup_ubuntu_6.06](http://www.howtoforge.com/perfect_setup_ubuntu_6.06)
Everything works fine, including the ISPconfig, which I installed successfully.
Now, here are my questions:
1. How can I access a website I create from an outside network? From my network, I can access the ISPconfig through the ip address and port 81, but not the web page I create!
2. Is obimeister's solution a requirment or just to get a "decent www site"? I agree with victory2007: why pay someone else to host my website. But we are not out of the hoock as we have to pay to register a domain name. Am I right?
3. I have a router in my network and this might be causing trouble because I use the internal address. How can I find the public one?

Thanks in advance

---

### Post by dfreer on 2007-06-03
> **yacine said:**
> I have similar questions about web servers. I installed the ubuntu server edition following instructions in this website: [http://www.howtoforge.com/perfect_setup_ubuntu704](http://www.howtoforge.com/perfect_setup_ubuntu704) for Dapper see: [http://www.howtoforge.com/perfect_setup_ubuntu_6.06](http://www.howtoforge.com/perfect_setup_ubuntu_6.06)
Everything works fine, including the ISPconfig, which I installed successfully.
Now, here are my questions:
1. How can I access a website I create from an outside network? From my network, I can access the ISPconfig through the ip address and port 81, but not the web page I create!
2. Is obimeister's solution a requirment or just to get a "decent www site"? I agree with victory2007: why pay someone else to host my website. But we are not out of the hoock as we have to pay to register a domain name. Am I right?
3. I have a router in my network and this might be causing trouble because I use the internal address. How can I find the public one?

Thanks in advance

The problem with that howto is that it comes to the top of a lot of search results, and it is OVERKILL for setting up a web server. Major overkill. For some reason everyone around here refers to it, and although it is pretty good guide most if not all users will never need or use the stuff it covers (who here is an ISP?). if you don't know or need xyz software, why install it? you are only increasing your chances of getting hacked/exploited.

1. your website is now ISPConfig due to blindly following that above howto. You'll need to either modify it or apache to run on a different port, or uninstall it. 
2. Yes, you will need to either pay for a top-level domain name ([www.dfreer.org](www.dfreer.org) was $15 bucks a year for me, you can get them cheaper), or you can use a hosting service to get a nearly top-level domain name for free ([http://mysite.dyndns.org](http://mysite.dyndns.org) [http://mysite.no-ip.com](http://mysite.no-ip.com) etc). freedns will give you some free dns servers to point toward your static IP, or if you're like me and have a dynamic address you can use dynds.org or no-ip.com among others. Your router should already have NAT, and you don't need bind if you use freedns/dyndns
3. whatismyipaddress.com whatismyip.com ipaddressworld.com ip-address.com myipaddress.com ..... You'll need to enable port forwarding on your router so that it will let port 80 pass through to your server

---

### Post by yacine on 2007-06-03
Thanks for your quick answer, dfreer. Congrats for your beautiful website! I had to follow "blindly" one installation instrcution, to get to something... I happen to chose the wrong way according to you! Well it is giving me problems. I am considering removing it and follow any other instructions! Any suggestions?
I will examine more closely the the issue of top-level domain name. Thanks for sharing your experience.
I did found my external IP, I guess I have to run it through ipcalc command to find the details about my broadcast, gateway, and network ...

---

### Post by victory2007 on 2007-06-03
Wow, thanks for all the great responses.  Ok so I registered with freedns now what steps do I need to take to get my web page that I already have made up to display on the internet.  I have Ubuntu 6.06 server installed with apache.  I am just completely lost on where to put the web site on the server and then what settings do I have to set to get it out on the www.  Basically I really need some one to hold my hand threw the whole process form start to finish sitting next to me on the computer, but since i don't know any one who can do that I will keep looking around for help.   Does any one have a good how too.  Thanks

---

### Post by dfreer on 2007-06-03
Thanks for the compliments on the site! Although I can't really take the credit quite yet, as I my site is based on a template (kinda). Yeah, it's nowhere near done but I'm working on it. Although I generally code my sites by hand, I like to start with a basic CSS template and modifying it for my needs. You can find the two I based my site off of at:
[http://www.freecsstemplates.org/preview/enlight](http://www.freecsstemplates.org/preview/enlight)
[http://www.freecsstemplates.org/preview/atomohost](http://www.freecsstemplates.org/preview/atomohost)

I can help you get your site up and running, if you need it. So basically what you have done so far is:
Installed Ubuntu 6.06 Server with apache2.
Figured out your external IP Address.

You will need to find out if your ISP blocks port 80 or any other incoming ports, either by calling them or by running apache and see if a site like canyouseeme.org can see if port 80 is open. Calling your ISP is risky, but would be easier. The risky part is as soon as you mention that you want to run a server from home they will want to charge you business class service (for me, something like $30 a month I pay now to $200 a month for business). You could simply word your question right or use some acting/social engineering skills, maybe say something like "I like to play games online and I wanna know if you block any ports?" I dunno.
If they do, you can look into port 80 redirection, which would redirect any incoming requests for port 80 and route them to a port of your choice, transparently to the end user.

What you will need to do next is put some webpages in /var/www, which is the default web root directory for ubuntu. Once you do that, you can install lynx and browse to your website from the commandline:
```
sudo apt-get install lynx
lynx http://localhost
```
If you can see your website, or the default welcome page for apache, it is all working good.

You will then need to get either a top-level domain name, or register a free one at those sites I mentioned (dyndns or no-ip, there is plenty more to choose from but I have used these two the most). Top level domain names are pretty inexpensive, even .com's. Shop around if you are planning to buy a domain name, but if you have a dynamic IP I would deffinitely recommend using Dyndns and buy CustomDNS with your domain name, something like $45 USD a year.

Umm that's all for now, lemme know how you progress. I wouldn't worry about making a beastly website just yet, you can simply test your site by using the default apache welcome page until everything is set up.

---

### Post by yacine on 2007-06-14
I took the advice of dfreer and installed ubuntu 6.06.1 afresh! I changed the file /etc/network/interfaces and put my static address. Then I registered a subdomain name under no-ip.org the website linked my external ip to it (for free). Then I followed the steps in this link to setup no-ip in my server: [HTML]http://ubuntulinuxhowto.blogspot.com/2006/06/dynamic-dns-no-ip.html[/HTML]
I changed the file /etc/hosts to put my internal ip and the my new no-ip.org address.
The result: I can see my apache web page internally by typing my ip but not if I type my no-ip.org address. I cannot access anything from outside the network. Firefox yields this response:
```
The connection has timed out

The server at mywebsite.no-ip.org is taking too long to respond.
      
    *   The site could be temporarily unavailable or too busy. Try again in a few
          moments.

    *   If you are unable to load any pages, check your computer's network
          connection.

    *   If your computer or network is protected by a firewall or proxy, make sure
          that Firefox is permitted to access the Web.

      
```
I checked the port 80 with the command   ```
nmap -sT mywebsite.no-ip.org
``` and it showed that the port 80 is open. Any comments, suggestions are welcome! Can you, please, point me to what I am missing?!
Thanks dfreer for sharing with us your templates! I did not know this kind of thing exists! It makes life much easier! I will for sure use one of these and change it to my needs...
How about you Victory2007? Did you manage to get something done? Please, share with us your experience!

---

### Post by dfreer on 2007-06-14
@yacine
Ok, Let's try to figure this out. So your website can be accessed through the internal LAN ip address, but not by the domain name. Your website is not accessible from the internet at large, however.

First off, just wanted to mention freeproxy.ca really quick. It's a quick and easy way to test your website and see if it is available from the internet without having to get off your internal network. This particular proxy is located in canada, and there are tons of them around so feel free to pick the fastest one for ya.

Things to try from outside the LAN (internet):
Ping your domain name again, make sure that IS your external IP address. If you didn't run that port scan from outside the network, run it again now, see if port 80 is open. If it is the right address but you still cannot connect, try the below steps.

Things to try from the LAN:
Ping your domain name, see whether it points toward your internal or external IP address. If it points toward your external, make sure that you enabled port forwarding on your router so that port 80 is mapped to the static IP on your webserver, and the router isn't currently using port 80 itself (remote management often takes over it). Some routers do not let you access your website through the domain name INSIDE the LAN, that's another story.
If the external address is wrong, make sure your no-ip client is configured correctly. Umm, let me know how all this goes, but you probably already tried most of this already. Just wanted to make sure stuff is going right.

---

### Post by Cheese Sandwich on 2007-06-14
> **dfreer said:**
> 2. Yes, you will need to either pay for a top-level domain name ([www.dfreer.org](www.dfreer.org) was $15 bucks a year for me, you can get them cheaper), or you can use a hosting service to get a nearly top-level domain name for free ([http://mysite.dyndns.org](http://mysite.dyndns.org) [http://mysite.no-ip.com](http://mysite.no-ip.com) etc). freedns will give you some free dns servers to point toward your static IP, or if you're like me and have a dynamic address you can use dynds.org or no-ip.com among others. Your router should already have NAT, and you don't need bind if you use freedns/dyndns


I just viewed the page source of your website, and it was all there, unlike the scheme I see for mine using no-ip.com, where you get a no-ip page that opens the target page inside a frame... How did you do that?

---

### Post by dfreer on 2007-06-14
> **Cheese Sandwich said:**
> I just viewed the page source of your website, and it was all there, unlike the scheme I see for mine using no-ip.com, where you get a no-ip page that opens the target page inside a frame... How did you do that?

Hmmm. I'm using DynDNS with the CustomDNS option for my website. I purchased the domain name through them, and then purchased the CustomDNS option, you may want to look into that.
As for no-ip.com, when I used them about 6 months ago I never saw what you described, sounds like you are doing a port 80 redirect or maybe an website redirection (for example have [http://yosoko.no-ip.org](http://yosoko.no-ip.org) point to [http://www.google.com](http://www.google.com)), try checking your no-ip settings. Are you doing anything with your website out of the norm? (e.g. using a registered domain name with the free service, port 80 redirection, using one of the enhanced/plus services on the site)

---

### Post by Cheese Sandwich on 2007-06-14
> **dfreer said:**
> Hmmm. I'm using DynDNS with the CustomDNS option for my website. I purchased the domain name through them, and then purchased the CustomDNS option, you may want to look into that.
As for no-ip.com, when I used them about 6 months ago I never saw what you described, sounds like you are doing a port 80 redirect or maybe an website redirection (for example have [http://yosoko.no-ip.org](http://yosoko.no-ip.org) point to [http://www.google.com](http://www.google.com)), try checking your no-ip settings. Are you doing anything with your website out of the norm? (e.g. using a registered domain name with the free service, port 80 redirection, using one of the enhanced/plus services on the site)

Yep I'm doing port 80 redirection - that must be the reason.

---

### Post by yacine on 2007-06-19
Thank you dfreer for your help and advice! All I had to do is to enable port forwarding in my router, as you suggested and everything worked like a charm. I had to go through the documentation for my router and figure out how to do that... Also, I followed the directions given in [http://portforward.com/]("http://portforward.com/") very useful.
Now, I will experiment/read before I decide whether to buy a domain name or just stay with [http://www.no-ip.com]("http://www.no-ip.com") basic free service.
Thanks again! You made my experience with Ubuntu Server interesting, enjoyable and less painful...

---

