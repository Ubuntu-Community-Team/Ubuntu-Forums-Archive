---
title: "How do I set up a LAMP if the domain name is already hosted elsewhere?"
date: 2009-09-16
forum: Server Platforms
---

### Post by HighlyDubious on 2009-09-16
I'm attempting to build a LAMP web-server.

I've assembled a PC from spare parts, and installed Ubuntu Server 9.04 (x64). I'm a newbie to Linux, so to make my life a little easier, I also added the xubuntu-desktop package. Eventually I'll use SSH for my primary access, but for now the GUI is convenient, and a comforting 'Security Blanket'.

As far as server related packages go, thus far I've only installed OpenSSH, and done a full update/upgrade of all packages suggested by apt-get. Beyond this I plan to follow whatever HOWTO's and tutorials I can find online to help me get up and running. (Any suggestions for especially good ones would be greatly appreciated.)

I think I know how to set-up my 2-Wire DSL-modem/router (technically, it calls itself a "gateway"), so that it will allow this PC to be a server. I've already configured my 2-Wire to assign the static IP of 192.168.0.100 to my server PC. But I'm a little lost when it comes to editing '/etc/network/interfaces'.

Now to the real heart of my confusion. When finished, I will use a domain name that I already have (SloeTechnologies.co.cc). That domain is currently active and hosted by a free hosting service. So I'm totally confused about the following:

[LIST=1]
[*]How can I set-up, properly configure and locally test this server, while my domain is currently hosted elsewhere?
[*]When the server is fully functional, how do I get the rest of the Internet to know my domain is at my IP instead of the IP of the hosting service?
[*]On the 2-Wire, should I try to open only the ports that my server needs? Or should I just DMZ the whole thing and add a firewall to the server?
[*]What is The Answer to The Eternal Question of Life, The Universe, and Everything?
[*]I've named this PC "sloe-server", and my domain is "sloetechnologies.co.cc". Which "name" I should use when setting up my files in '/etc/hosts', and '/etc/hostname', and any other config files. And how will this be affected by the domain being currently hosted elsewhere?
[/LIST]
Since my domain name is from a free provider I'm concerned they may delete it if its not assigned to someplace that's live and online. Sure, there would be some grace period (a couple of days?). But since I've never done this before, I have no idea how long it will take me to get the server fully functional. So for now I've been keeping the domain hosted elsewhere and planned to transfer it to my own IP when I know the server is fully functional.

This whole thing needs to be up and running faster than ASAP. I need it for a work related project that was due LAST week. And unfortunately there is no budget for hiring a professional. As a result, this is all on me, and I'm depending on whatever resources I can find out on the net.

Any advice, pointers, suggestions, links, etc will be VERY appreciated.

---

### Post by Ms_Angel_D on 2009-09-16
You will need DNS.

I purchased my domains from Godaddy but I pointed the name servers to [http://freedns.afraid.org](http://freedns.afraid.org) they will in turn allow you to point your domain to your ip address.

What you need to do is sign up for a free account, once that's done and you have logged in select Domains from the main menu, then click add. You'll see the nameserver listed. 

You'll have to login to your domain registar and update the nameservers on your domain.

I'm not exactly sure how this works with .co.cc domains as I've never had one, but this is how I've done it with .com, .info, .net, and .org domains.

the free DNS services I have used are as follows:

[LIST=1]
[*][http://www.dyndns.com](http://www.dyndns.com)
[*][http://www.everydns.com](http://www.everydns.com)
[*][https://www.editdns.net](https://www.editdns.net)
[*][http://www.zoneedit.com](http://www.zoneedit.com)
[*][http://freedns.afraid.org](http://freedns.afraid.org)
[/LIST]

the two which I found to be the best are #3 & #5

---

### Post by windependence on 2009-09-16
> **Ms_Angel_D said:**
> You will need DNS.

I purchased my domains from Godaddy but I pointed the name servers to [http://freedns.afraid.org](http://freedns.afraid.org) they will in turn allow you to point your domain to your ip address.

What you need to do is sign up for a free account, once that's done and you have logged in select Domains from the main menu, then click add. You'll see the nameserver listed. 

You'll have to login to your domain registar and update the nameservers on your domain.

I'm not exactly sure how this works with .co.cc domains as I've never had one, but this is how I've done it with .com, .info, .net, and .org domains.

the free DNS services I have used are as follows:

[LIST=1]
[*][http://www.dyndns.com](http://www.dyndns.com)
[*][http://www.everydns.com](http://www.everydns.com)
[*][https://www.editdns.net](https://www.editdns.net)
[*][http://www.zoneedit.com](http://www.zoneedit.com)
[*][http://freedns.afraid.org](http://freedns.afraid.org)
[/LIST]

the two which I found to be the best are #3 & #5

You didn't have to do this if you use Godaddy for registration. You can use their DNS servers and just point the domain at your external static IP address. You do NOT need any other DNS service whatsoever to properly host your site. You simply go into your DNS control panel and point your A records and CNAMEs to where you want them to point. See below:

-Tim

---

### Post by Ms_Angel_D on 2009-09-16
> **windependence said:**
> You didn't have to do this if you use Godaddy for registration. You can use their DNS servers and just point the domain at your external static IP address. You do NOT need any other DNS service whatsoever to properly host your site. You simply go into your DNS control panel and point your A records and CNAMEs to where you want them to point. See below:

-Tim

I'm aware that this can be done for a static IP address however I do not have a static IP.

---

### Post by theozzlives on 2009-09-16
> **Ms_Angel_D said:**
> I'm aware that this can be done for a static IP address however I do not have a static IP.

I was not aware you could host your own site with a dynamic IP. If I knew that I wouldn't have signed a 3 year contract with my ISP.

---

### Post by windependence on 2009-09-16
> **HighlyDubious said:**
> I'm attempting to build a LAMP web-server.

I've assembled a PC from spare parts, and installed Ubuntu Server 9.04 (x64). I'm a newbie to Linux, so to make my life a little easier, I also added the xubuntu-desktop package. Eventually I'll use SSH for my primary access, but for now the GUI is convenient, and a comforting 'Security Blanket'.

As far as server related packages go, thus far I've only installed OpenSSH, and done a full update/upgrade of all packages suggested by apt-get. Beyond this I plan to follow whatever HOWTO's and tutorials I can find online to help me get up and running. (Any suggestions for especially good ones would be greatly appreciated.)

I think I know how to set-up my 2-Wire DSL-modem/router (technically, it calls itself a "gateway"), so that it will allow this PC to be a server. I've already configured my 2-Wire to assign the static IP of 192.168.0.100 to my server PC. But I'm a little lost when it comes to editing '/etc/network/interfaces'.

Now to the real heart of my confusion. When finished, I will use a domain name that I already have (SloeTechnologies.co.cc). That domain is currently active and hosted by a free hosting service. So I'm totally confused about the following:

[LIST=1]
[*]How can I set-up, properly configure and locally test this server, while my domain is currently hosted elsewhere?
[/LIST]
Simple. Just assign an internal, non-routeable static IP to the server:

```
$sudo nano /etc/network/interfaces]
```Make it look like this:

```
iface eth0 inet static
address 192.168.0.100
netmask 255.255.255.0
gateway 192.168.0.1
```This is the way to set a static IP for your server behind your router. the address you set in your router above is on the external interface, and you re trying to use a non-routeable (internal) IP address which will not work from the outside. If you can get a static IP from your ISP, that's great, and that would be the best way to configure the outside interface address (DSL or Cable side). If not, you will have to use a dynamic IP service such as no-ip.com.

Once you have this internal IP set, you can simply access your site for testing by going to the IP address [http://192.168.0.100](http://192.168.0.100). When you are ready to go live, you will have to use network address translation to forward your port back to your server

[http://support.2wire.com/?page=view&article=222](http://support.2wire.com/?page=view&article=222)
> **HighlyDubious said:**
> 

[LIST=1]
[*]When the server is fully functional, how do I get the rest of the Internet to know my domain is at my IP instead of the IP of the hosting service?
[/LIST]
You will need to go into your REGISTRAR's DNS control panel (the people you registered your domain with) and set up your DNS to point to the EXTERNAL address of your Home Portal (router).
> **HighlyDubious said:**
> 

[LIST=1]
[*]On the 2-Wire, should I try to open only the ports that my server needs? Or should I just DMZ the whole thing and add a firewall to the server?
[/LIST]
Best practice is to open only the prts you need and forward them back to your server. Running a firewall on your server is dangerous because your server can be taken down simply by flooding it with traffic, thereby overloading the CPU and other resources without even cracking your password.
> **HighlyDubious said:**
> 

[LIST=1]
[*]What is The Answer to The Eternal Question of Life, The Universe, and Everything?
[/LIST]
:-)
> **HighlyDubious said:**
> 

[LIST=1]
[*]I've named this PC "sloe-server", and my domain is "sloetechnologies.co.cc". Which "name" I should use when setting up my files in '/etc/hosts', and '/etc/hostname', and any other config files. And how will this be affected by the domain being currently hosted elsewhere?
[/LIST]
In order for this to work on your local network, you will need to set up your /etc/hosts as follows:

```
127.0.0.1           localhost
192.168.0.100    sloetechnologies.co.cc
```> **HighlyDubious said:**
> 

Since my domain name is from a free provider I'm concerned they may delete it if its not assigned to someplace that's live and online. Sure, there would be some grace period (a couple of days?). But since I've never done this before, I have no idea how long it will take me to get the server fully functional. So for now I've been keeping the domain hosted elsewhere and planned to transfer it to my own IP when I know the server is fully functional.

I would recommend transferring it to a paid registrar like GoDaddy. It's only about $8 per year and you can then point it where you want using their DNS control panel.

> **HighlyDubious said:**
> This whole thing needs to be up and running faster than ASAP. I need it for a work related project that was due LAST week. And unfortunately there is no budget for hiring a professional. As a result, this is all on me, and I'm depending on whatever resources I can find out on the net.

Any advice, pointers, suggestions, links, etc will be VERY appreciated.

Unfortunately, my assessment is that you need to do a little reading to understand how the web and web hosting, along with basic networking works. here are some resources:

[http://www.zeromillion.com/ebiz/domain-website-basics.html](http://www.zeromillion.com/ebiz/domain-website-basics.html)

[https://help.ubuntu.com/8.04/serverguide/C/](https://help.ubuntu.com/8.04/serverguide/C/)

Hope this helps. Good luck!

-Tim

---

### Post by Ms_Angel_D on 2009-09-16
> **theozzlives said:**
> I was not aware you could host your own site with a dynamic IP. If I knew that I wouldn't have signed a 3 year contract with my ISP.

It's possible, freedns.afraid.org has a dynamic update script that can be used so that if your IP changes it's updated. though my Ip doesn't change often enough to warrant me going through setting one up, I can see how it would be quite helpful to others.

[http://freedns.afraid.org/scripts/freedns.clients.php](http://freedns.afraid.org/scripts/freedns.clients.php)

The do provide a Programmer's XML API also. I'm sure it would be quite easy for someone with the know-how to write up a simple updating script.

---

### Post by windependence on 2009-09-16
> **Ms_Angel_D said:**
> I'm aware that this can be done for a static IP address however I do not have a static IP.

This can also be done with a dynamic IP service such as no-ip.com. You simply point your domain at no-ip's servers, and then set up a redirect with no-ip.

You should be aware that using a dynamic IP is not the best way to do this, and that not everyone will be able to access your site with a redirect or dynamic IP service. There are quite a large section of servers who block any of this traffic, especially if your audience is browsing from work, which is at least 80% of my traffic of 5 million hits per month. If users can give feedback, they will complain that they cannot reach your site, however, if you do not run a forum or blog as I do, you will probably never know that a good part of your traffic cannot reach you.

-Tim

---

### Post by windependence on 2009-09-16
> **theozzlives said:**
> I was not aware you could host your own site with a dynamic IP. If I knew that I wouldn't have signed a 3 year contract with my ISP.

You set up your site the proper way, and as such, all your traffic will be able to reach your site. there are also ISPs like mine who only charge a nominal fee for an IP ($5.95 per month).

-Tim

---

### Post by Ms_Angel_D on 2009-09-16
> **windependence said:**
> This can also be done with a dynamic IP service such as no-ip.com. You simply point your domain at no-ip's servers, and then set up a redirect with no-ip.

You should be aware that using a dynamic IP is not the best way to do this, and that not everyone will be able to access your site with a redirect or dynamic IP service. There are quite a large section of servers who block any of this traffic, especially if your audience is browsing from work, which is at least 80% of my traffic of 5 million hits per month. If users can give feedback, they will complain that they cannot reach your site, however, if you do not run a forum or blog as I do, you will probably never know that a good part of your traffic cannot reach you.

-Tim

I wasn't aware of the restrictions, however I don't have a real home server, I only have a lamp server running for test purposes. My actual websites are hosted.

---

### Post by lvlint67 on 2009-09-16
> **Ms_Angel_D said:**
> I wasn't aware of the restrictions, however I don't have a real home server, I only have a lamp server running for test purposes. My actual websites are hosted.


I'm not sure i believe this....

To my understanding a traditional dynamic dns setup uses a script to get the proper ip address for the pc running the server and then modifies it's A record for the domain...

There shouldn't be a redirect involved to the outside it should appear exactly the same as a site hosted on a server with a static ip in a datacenter....

(Although I don't have a 'mastery' of DNS systems... just a bit of experience working with them.)

---

### Post by Ms_Angel_D on 2009-09-16
> **lvlint67 said:**
> I'm not sure i believe this....

To my understanding a traditional dynamic dns setup uses a script to get the proper ip address for the pc running the server and then modifies it's A record for the domain...

There shouldn't be a redirect involved to the outside it should appear exactly the same as a site hosted on a server with a static ip in a datacenter....

(Although I don't have a 'mastery' of DNS systems... just a bit of experience working with them.)

I'm not sure I understand your misunderstanding...lol

As dynamic DNS works exactly as you stated, though I personaly don't use a script, if My ip changes (it doesn't happen often) I just go the website and manually update my IP address. The redirect is that The register points my domains to freedns.afraid.org via nameservers who in turn points the site my own IP. The website appears as normal to the rest of the world. It loads up just the same as my hosted websites.

---

### Post by lvlint67 on 2009-09-16
> **Ms_Angel_D said:**
> I'm not sure I understand your misunderstanding...lol

As dynamic DNS works exactly as you stated, though I personaly don't use a script, if My ip changes (it doesn't happen often) I just go the website and manually update my IP address. The redirect is that The register points my domains to freedns.afraid.org via nameservers who in turn points the site my own IP. The website appears as normal to the rest of the world. It loads up just the same as my hosted websites.

sorry for the confusion... I was responding to windepence's aside about certain servers blocking redirects.

---

### Post by HighlyDubious on 2009-09-16
> **Ms_Angel_D said:**
> You will need DNS.

I purchased my domains from Godaddy but I pointed the name servers to [http://freedns.afraid.org](http://freedns.afraid.org) they will in turn allow you to point your domain to your ip address.

What you need to do is sign up for a free account, once that's done and you have logged in select Domains from the main menu, then click add. You'll see the nameserver listed. 

You'll have to login to your domain registar and update the nameservers on your domain.

I'm not exactly sure how this works with .co.cc domains as I've never had one, but this is how I've done it with .com, .info, .net, and .org domains.

the free DNS services I have used are as follows:

[LIST=1]
[*][http://www.dyndns.com](http://www.dyndns.com)
[*][http://www.everydns.com](http://www.everydns.com)
[*][https://www.editdns.net](https://www.editdns.net)
[*][http://www.zoneedit.com](http://www.zoneedit.com)
[*][http://freedns.afraid.org](http://freedns.afraid.org)
[/LIST]

the two which I found to be the best are #3 & #5

First, to all you good folks who responded, WOW! Y'all are amazing! I figured that posting my question in the middle of the night, I'd have to wait until sometime mid-tomorrow before I got much in the way of useful responses. But here it is just 3 hours later, and I've already got some amazing and valuable information. WOW! \\:D/

Second, what a coincidence, Ms Angel, just before coming back here to check to for responses, I was over on dyndns and no-ip seeing what they had to offer, and if I could benefit from it. Based on what I've read, I have a similar situation to you. My IP does change, but not very often. And for the most part, this server will be for mostly small stuff, not for mass-consumption. So, I'm definitely going to look into your suggestion about [http://freedns.afraid.org]("http://freedns.afraid.org/"). :)

Thanks so much for the suggestion, and for the list of options beyond just that one.

(as for co.cc domains, it was just someplace I found that offered free domain registration. And since I (currently) don't need a .com, I went ahead and signed up. My best guess is, they can be used in exactly the way you suggested)

---

### Post by HighlyDubious on 2009-09-16
> **windependence said:**
> Simple. Just assign an internal, non-routeable static IP to the server:

```
$sudo nano /etc/network/interfaces
```Make it look like this:

```
iface eth0 inet static
address 192.168.0.100
netmask 255.255.255.0
gateway 192.168.0.1
```This is the way to set a static IP for your server behind your router. the address you set in your router above is on the external interface, and you're trying to use a non-routeable (internal) IP address which will not work from the outside. If you can get a static IP from your ISP, that's great, and that would be the best way to configure the outside interface address (DSL or Cable side). If not, you will have to use a dynamic IP service such as no-ip.com.

Once you have this internal IP set, you can simply access your site for testing by going to the IP address [http://192.168.0.100](http://192.168.0.100). First, Thanks so VERY much for such an in-depth and very helpful response. I'm still trying to figure things out, and having to re-read things 3-10 times before they all make complete sense. So I've not yet had time to fully digest everything you've written. I'm sure I'll be coming back to re-read each part as I'm setting this all up.

Ok, now. I understand that there are 2 IP addresses. There's the IP that the whole rest of the world sees (99.2.xxx.xxx), and there's the internal addresses assigned by my modem/router - the LAN IP. (After posting my above, I did some more research, and have learned that technically my modem/router is called a "Residential Gateway", or RG for short). When I wrote above that I'd assigned a static IP to the server PC, I meant that I'd told my RG to always use 192.168.0.100 as the LAN IP for my server. To be more exact, I told my RG to only offer 192.168.0.100 when my server does it's DHCP request. This has the effect of locking my server to a static IP.

However, I can see that the entries you advised for /etc/network/interfaces will have the same effect. And since you know what you're doing (while I obviously don't!), I will make the above changes to /etc/network/interfaces. I'm just curious though if doing it via /etc/network/interfaces makes the changes in the RG superfluous? (neither a benefit, nor a detriment). Or is there a specific reason I should remove the restriction in the RG?
> When you are ready to go live, you will have to use network address translation to forward your port back to your server

[http://support.2wire.com/?page=view&article=222](http://support.2wire.com/?page=view&article=222)I'm guessing you mean that I'll need to tell my RG to forward all inbound requests on Port 80 to my server, right? If that's what you mean, I've already made that change in my RG. (And btw, thanks for the link. I've needed something like that for a while)

> You will need to go into your REGISTRAR's DNS control panel (the people you registered your domain with) and set up your DNS to point to the EXTERNAL address of your Home Portal (router).I've done this once before when I pointed the domain to the free hosting site. So I believe I know how to do it again. But also, as I recall, they asked for 2 different server URL's, so (for now), I'm not sure how I'd tell them only my single IP.

Then again, if I will follow your and Ms Angel's suggestion, then I can use a service like freedns.afraid.org, or godaddy.com as a 'middleman' to handle DNS issues for me. Is that right?

> Best practice is to open only the prts you need and forward them back to your server. Running a firewall on your server is dangerous because your server can be taken down simply by flooding it with traffic, thereby overloading the CPU and other resources without even cracking your password.Of course I've read about DOS and DDOS attacks against various sites. But I never thought about someone attacking my insignificant little site. Even so, I agree with you, it certainly makes more sense to let my RG shield me, rather than run the potential risk of someone taking down my server with a malicious flood.

> In order for this to work on your local network, you will need to set up your /etc/hosts as follows:

```
127.0.0.1           localhost
192.168.0.100    sloetechnologies.co.cc
```Ok, I can do that. Do I also need to make the same change to /etc/hostname? Will I need to change it anywhere else? And, will using the domain names in these files cause me problems since the site is live somewhere else? 

I guess the big question here is this: While I'm setting things up, if I configure everything to use my domain name, will it pose a problem during testing? -- Or, do I avoid these potential problems during the testing phase, by only accessing my site from it's LAN IP and not it's URL?

> I would recommend transferring it to a paid registrar like GoDaddy. It's only about $8 per year and you can then point it where you want using their DNS control panel.$8 is certainly well within my budget for this project (I spent more than that on dinner last night! LoL). So I've got no problem with using GoDaddy. 

At this minute though (since I've not yet been to their site), I'm not quite sure what they will offer me that someplace like freedns.afraid.org doesn't? Oh, sure, I know they offer many many things. But for my particular needs -- which is basically just a way for the outside world to know that sloetechnologies.co.cc points to my external IP address -- then I'm not sure where GoDaddy offers me any benefit over a free service doing the same thing?

Or am I missing some very important point here?

> Unfortunately, my assessment is that you need to do a little reading to understand how the web and web hosting, along with basic networking works. here are some resources:

[http://www.zeromillion.com/ebiz/domain-website-basics.html](http://www.zeromillion.com/ebiz/domain-website-basics.html)

[https://help.ubuntu.com/8.04/serverguide/C/](https://help.ubuntu.com/8.04/serverguide/C/)Yes, I agree 100%! I am in very deep need of more reading and learning. At the same time, I need to get this thing up ASAP. So, what I expect I'll do is read what I can in the links you provided (which, btw, **THANKS** for the links! I **REALLY** appreciate them!). Then actually dive in with both feet and try to make this happen as soon as I can. Then, once I'm actually up, I can take the time to go back and do more in-depth reading and try to understand the why's and how's of what I've done.


> Hope this helps. Good luck!

-TimYou've already been a HUGE help! Hopefully with what you've told me, I'll be able to get this up and running later tonight (It's bedtime for Bonzo right now). And if not, then you can be assured I'll be back posting my next round of newbie questions! :biggrin:

---

### Post by windependence on 2009-09-16
> **lvlint67 said:**
> I'm not sure i believe this....

To my understanding a traditional dynamic dns setup uses a script to get the proper ip address for the pc running the server and then modifies it's A record for the domain...

There shouldn't be a redirect involved to the outside it should appear exactly the same as a site hosted on a server with a static ip in a datacenter....

(Although I don't have a 'mastery' of DNS systems... just a bit of experience working with them.)

Yes, it does, but the filters still know the IP address blocks of the dynamic seervices. Because they provide a way for people to cloak their attacks, many corporate firewalls block this traffic.

Trust me, after I got to about 250,000 hits, I started to get posts on my board saying other members had contacted them and told them they could not get on the site. I also got calls from users who are friends of mine with the same complaint, and not just one or two of them either. As soon as we went to static IPs, no more problems. I now own a block of 8 IPs.

Dynamic IP services are great for testing and if you are a home user and want to run a small site on your ISP, but you would not want to do this on an important site or a production site. not inly do I run a site with 5 million hits a month and 12,000 page views per day, but I have also worked in numerous companies and ran their server farms for their web sites. When we do a professional site, we use a static IP, pure and simple.

-Tim

---

### Post by windependence on 2009-09-16
> **Ms_Angel_D said:**
> I'm not sure I understand your misunderstanding...lol

As dynamic DNS works exactly as you stated, though I personaly don't use a script, if My ip changes (it doesn't happen often) I just go the website and manually update my IP address. The redirect is that The register points my domains to freedns.afraid.org via nameservers who in turn points the site my own IP. The website appears as normal to the rest of the world. It loads up just the same as my hosted websites.

If you do it this way, you could still have a problem if you are using dynamic DNS servers. In your case, you don't have to do what you are doing, just point your GoDaddy domain directly to your outside IP using the domain control panel. It's not necessary to use any other DNS as GoDaddy actually has one of the fastest DNS presences on the web. They make sure their DNS propgates directly to the main backbone.

-Tim

---

### Post by windependence on 2009-09-16
> **HighlyDubious said:**
> First, Thanks so VERY much for such an in-depth and very helpful response. I'm still trying to figure things out, and having to re-read things 3-10 times before they all make complete sense. So I've not yet had time to fully digest everything you've written. I'm sure I'll be coming back to re-read each part as I'm setting this all up.

Ok, now. I understand that there are 2 IP addresses. There's the IP that the whole rest of the world sees (99.2.xxx.xxx), and there's the internal addresses assigned by my modem/router - the LAN IP. (After posting my above, I did some more research, and have learned that technically my modem/router is called a "Residential Gateway", or RG for short). When I wrote above that I'd assigned a static IP to the server PC, I meant that I'd told my RG to always use 192.168.0.100 as the LAN IP for my server. To be more exact, I told my RG to only offer 192.168.0.100 when my server does it's DHCP request. This has the effect of locking my server to a static IP.

Yep, what you were doing is called reserved DHCP IP addressing. That's fine, I just like to set it statically on the box. That way, you eliminate any possible problems with the DHCP server

> **HighlyDubious said:**
> However, I can see that the entries you advised for /etc/network/interfaces will have the same effect. And since you know what you're doing (while I obviously don't!), I will make the above changes to /etc/network/interfaces. I'm just curious though if doing it via /etc/network/interfaces makes the changes in the RG superfluous? (neither a benefit, nor a detriment). Or is there a specific reason I should remove the restriction in the RG?

Yep, once you set the address this way, you don't need to have the router reserve the address. In fact, I usually set my static IPs to some IP outside the DHCP range so there are no conflicts.

> **HighlyDubious said:**
> I'm guessing you mean that I'll need to tell my RG to forward all inbound requests on Port 80 to my server, right? If that's what you mean, I've already made that change in my RG. (And btw, thanks for the link. I've needed something like that for a while)

Yep, you'll need to forward your ports back to your server so that it can handle the incoming requests........and you're welcome! :-)

> **HighlyDubious said:**
> I've done this once before when I pointed the domain to the free hosting site. So I believe I know how to do it again. But also, as I recall, they asked for 2 different server URL's, so (for now), I'm not sure how I'd tell them only my single IP.

Actually, with the two IPs you are thinking of DNS. Usually they ask you for two DNS servers to use. With a registrar like GoDaddy, you can use their DNS servers, no need to run your own or use someone else's. In the DNS control panel, you have something called an 'A' record, and also a CNAME. The 'A' record points to your server's outside IP. Then, you set up the CNAMES to point to your 'A' record for things like www. or ftp. or mail. so that the request for say [www.yourdomain.co.cc](www.yourdomain.co.cc) points to your server, and ftp.yourdomain.co.cc also points to your domain.

> **HighlyDubious said:**
> Then again, if I will follow your and Ms Angel's suggestion, then I can use a service like freedns.afraid.org, or godaddy.com as a 'middleman' to handle DNS issues for me. Is that right?

If you use someone like GoDaddy, you don't need a "middleman". You can use their DNS.

> **HighlyDubious said:**
> Of course I've read about DOS and DDOS attacks against various sites. But I never thought about someone attacking my insignificant little site. Even so, I agree with you, it certainly makes more sense to let my RG shield me, rather than run the potential risk of someone taking down my server with a malicious flood.

It has nothing to do with taking down your "little" site. These attacks are occuring 24/7/365, every minute and every second of every day. If your gateway has logging, check it out, people are trying to get in ALL the time. They use automated bots to search the web for IP addresses that respond to queries no matter how big the site. If they can get into a machine, they will set up a backend FTP server or turn the machine into a zombie that send out even MORE requests looking for other open IPs. Once they find an IP, they can launch a DDOS, or try to hack your box if they want. If you are behind a firewall, it's OK, the firewall can take the brunt of the attack. If you really want to be safe, turn off response to pings, although there are other ways they can find you.

> **HighlyDubious said:**
> Ok, I can do that. Do I also need to make the same change to /etc/hostname? Will I need to change it anywhere else? And, will using the domain names in these files cause me problems since the site is live somewhere else?

the hostname of your box is just that - the name of your box, so lets say the name of your box is "penguin". That would be your hostname. Now, the fully qualified domain name FQDN would be penguin.yourdomain.co.cc, got it? It's probably not necessary to change your hostname.

> **HighlyDubious said:**
>  

I guess the big question here is this: While I'm setting things up, if I configure everything to use my domain name, will it pose a problem during testing? -- Or, do I avoid these potential problems during the testing phase, by only accessing my site from it's LAN IP and not it's URL?

You can test it from the URL but just don't point your domain at your server until you are ready to go live. That way, you can still acces it from the inside (because your /etc/hosts provides DNS inside your box) without messing up the outside access.

> **HighlyDubious said:**
> $8 is certainly well within my budget for this project (I spent more than that on dinner last night! LoL). So I've got no problem with using GoDaddy. 

At this minute though (since I've not yet been to their site), I'm not quite sure what they will offer me that someplace like freedns.afraid.org doesn't? Oh, sure, I know they offer many many things. But for my particular needs -- which is basically just a way for the outside world to know that sloetechnologies.co.cc points to my external IP address -- then I'm not sure where GoDaddy offers me any benefit over a free service doing the same thing?

Or am I missing some very important point here?

Well, most free hosting doesn't have fancy features like using their DNS or even a nice control panel and most put ads on your site that you can't take off. not much for free anymore.

> **HighlyDubious said:**
> Yes, I agree 100%! I am in very deep need of more reading and learning. At the same time, I need to get this thing up ASAP. So, what I expect I'll do is read what I can in the links you provided (which, btw, **THANKS** for the links! I **REALLY** appreciate them!). Then actually dive in with both feet and try to make this happen as soon as I can. Then, once I'm actually up, I can take the time to go back and do more in-depth reading and try to understand the why's and how's of what I've done.


You've already been a HUGE help! Hopefully with what you've told me, I'll be able to get this up and running later tonight (It's bedtime for Bonzo right now). And if not, then you can be assured I'll be back posting my next round of newbie questions! :biggrin:

No problem, if you need more help just yell, this is what I do for a living.

-Tim

---

### Post by HighlyDubious on 2009-09-17
> **windependence said:**
> Yep, what you were doing is called reserved DHCP IP addressing. That's fine, I just like to set it statically on the box. That way, you eliminate any possible problems with the DHCP server

Yep, once you set the address this way, you don't need to have the router reserve the address. In fact, I usually set my static IPs to some IP outside the DHCP range so there are no conflicts.

Yep, you'll need to forward your ports back to your server so that it can handle the incoming requests........and you're welcome! :-)Ok, done all that. Mission Accomplished! We Have Lift Off. The Eagle Has Landed. And All That Jazz! In fact, with a little (ok, a LOT) of help from HowtoForge, I managed to get the LAMP up, running, and looking like an actual real life server. 

Of course, it currently lacks any worthwhile content, and I'm struggling with issues related to moving files around and permissions, etc. But those are general linux learning curve issues, and I'm sure I'll get the hang of it before too long.

> **windependence said:**
> Actually, with the two IPs you are thinking of DNS. Usually they ask you for two DNS servers to use. With a registrar like GoDaddy, you can use their DNS servers, no need to run your own or use someone else's. In the DNS control panel, you have something called an 'A' record, and also a CNAME. The 'A' record points to your server's outside IP. Then, you set up the CNAMES to point to your 'A' record for things like www. or ftp. or mail. so that the request for say [www.yourdomain.co.cc]("http://www.yourdomain.co.cc/") points to your server, and [ftp.yourdomain.co.cc]("ftp://ftp.yourdomain.co.cc/") also points to your domain.More out of curiosity than anything else, I went ahead and looked at what freedns.afraid.org had to offer. Right away I saw that the UI ain't too fancy. It looks like something a programmer put together -- in other words it makes perfect logical sense to him, and so naturally he just assumes it will make sense to his users. Unfortunately, as you probably know, very often end users are neither logical, nor sensible. So, anyway, all I'm saying is, it took a little while to figure things out there.

But, by the time I had, I decided to just go ahead and take the plunge. I had already gotten my LAMP up far enough to accept inbound traffic. And so I went to the free hosting site and deleted my account. Moving it to freedns.afraid.org was relatively painless. I had to go back to where I originally got the domain name, and tell them the nameservers for f.a.o, but that was just a few clicks and cut-n-pastes. Then I had to tell f.a.o my own external IP (99.2.xxx.xxx), and within a few minutes I was 'live'. 

By the way, just for general information, although the UI for f.a.o might not be as intuitive or slick as GoDaddy, they offer the same functionality in their control panel. It took only a few seconds to figure what to do in order to point my ftp., irc., [www.,]("http://www.,") and mail. subdomains at my IP. So, basically, except for the UI requiring some effort to figure out, the actual process of setting up my account, and the DNS stuff was fairly simple and painless. 

(I should probably clarify, there is nothing explicitly "bad" about the UI at f.a.o. It just took me a bit of time to figure out what I was supposed to do. There were no guided step-by-step instructions for complete newbies. If I were to guess, I'd say a large percent of their users are people who've done all this set-up before at other places, and who don't require the hand-holding that give us newbies a warm fuzzy feeling. So, for a more experienced user, no doubt their approach would be simple, direct, and fast.)

Anyway, all I'm saying is, based on what you've described that GoDaddy offers, I seem to be getting much the same results with f.a.o. Of course, I'm sure GoDaddy probably guarantees and delivers much higher reliability. And as you mentioned to Ms Angel, no doubt GoDaddy's DNS servers are much faster at propagating the info across the net. 

> **windependence said:**
> If you use someone like GoDaddy, you don't need a "middleman". You can use their DNS.By 'middleman', I actually meant a DNS service. In my newbie mind, I see the chain very simplistically. There is the company that gave me my free domain, there is the DNS service, and there is me. That puts GoDaddy or any other DNS service as 'the middleman'. No doubt you see the world in much greater depth, and clarity. But for me it just seemed that the DNS service sits in the middle between me and the rest of the world.

> **windependence said:**
> It has nothing to do with taking down your "little" site. These attacks are occuring 24/7/365, every minute and every second of every day. If your gateway has logging, check it out, people are trying to get in ALL the time. They use automated bots to search the web for IP addresses that respond to queries no matter how big the site. If they can get into a machine, they will set up a backend FTP server or turn the machine into a zombie that send out even MORE requests looking for other open IPs. Once they find an IP, they can launch a DDOS, or try to hack your box if they want. If you are behind a firewall, it's OK, the firewall can take the brunt of the attack. If you really want to be safe, turn off response to pings, although there are other ways they can find you.You paint a very vivid image. It's amazing how the vast majority of users out there have no idea that when they plug their PC into the Internet, it's like swimming in shark infested waters.

Yes, I was somewhat aware that there are bots constantly crawling the web searching for any crack or crevice to infest. And yes, after reading you post I went back and looked at the log in my RG, and sure enough, there are dozens of probes every minute. Fortunately, my RG is a reasonably good one. Of course nothing is 'perfect', but it has a number of different layers of protection against many types of probes. For example, by default it turns off responses to pings. Bottom line is, I know the RG won't stop everything, but perhaps I'm somewhat better protected than the guy who just plugs his cable modem into his PC, and surfs without even installing any anti-malware protection.

> **windependence said:**
> the hostname of your box is just that - the name of your box, so lets say the name of your box is "penguin". That would be your hostname. Now, the fully qualified domain name FQDN would be penguin.yourdomain.co.cc, got it? It's probably not necessary to change your hostname.Ahhhh, I understand. That makes sense. Ok, so if I want to keep my server with the name "sloe-server", then hostname is where I'll set that. Ok. Thanks. I did wonder about that.

> **windependence said:**
> You can test it from the URL but just don't point your domain at your server until you are ready to go live. That way, you can still acces it from the inside (because your /etc/hosts provides DNS inside your box) without messing up the outside access.I never tried to test it with the URL, coz I expected I'd just get the free hosting site. So, while testing I just used the LAN IP of 192.168.1.100, and everything worked out well for me. But it is nice to know I could have used the URL, and that the hosts file would have taken care of the re-direction.

I do have one small question on this. Now that my site is live, I notice that whenever I try to go to my site by typing the URL into my browser, it just spends a long time trying to connect, then eventually times out. I'm not surprised by this behavior, I'd read other people mention it in other forums. But I'm curious if you could explain why it happens that way? To my newbie mind, it seems that I'm sending a request out for the URL, and the DNS should take care of working out the details.

I'm making a naive guess that it has to do with confusion over port 80 and me sending a request from my browser on port 80, while also expecting my server to respond on port 80. If that's the case, then hypothetically (if I cared enough to experiment) could this be resolved by having f.a.o redirect all requests to my server to port 8080? (I'd heard other people mention port 8080  as a way to get around ISP's blocking port 80) This isn't really an issue to me. But I am mildly curious about it.

> **windependence said:**
> Well, most free hosting doesn't have fancy features like using their DNS or even a nice control panel and most put ads on your site that you can't take off. not much for free anymore.Yes, the free hosting site I used at first would put their ad on the page. But as best I can tell, f.a.o is not doing that. Here is the only thing I can see that come close to something like that (quoted from their site)

> **freedns.afraid.org][FONT=verdana][SIZE=1][COLOR=black]If you could place a small text link somewhere on your site to [http://freedns.afraid.org/](http://freedns.afraid.org/) named "Free DNS" it would be greatly appreciated, to help raise search engine rankings and bring more users to the site, even if you don't think your site gets much traffic it would still help! - Josh[/COLOR][/SIZE][/FONT][/quote]Of course I lack broad experience, but that does seem like a reasonable, and non-intrusive request.

 [quote=windependence said:**
> No problem, if you need more help just yell, this is what I do for a living.

-TimThanks again. And don't be surprised if I come back before too long and start asking a whole slew of newer and even dumber questions! LoL

Best Regards,
Brian

---

### Post by HighlyDubious on 2009-09-17
:guitar:I want to thank everyone who offered suggestions and advice. Thanks to all of your help I was able to set up, configure and test my LAMP while the domain was hosted elsewhere. My server is now up and running and so now I'll go ahead an mark this thread as Solved.
:popcorn:

Best Regards,
Brian

---

