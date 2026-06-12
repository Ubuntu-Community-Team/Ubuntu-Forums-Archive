---
title: "How do you configure it?"
date: 2005-10-26
forum: Server Platforms
---

### Post by shade11 on 2005-10-26
I don't know the first thing about severs. I am asking is how do I set one up? Using Ubuntu as the OS for the server. What do I need to do. And do I need the computer connect to the internet?

---

### Post by Surfoo on 2005-10-26
Which type of server ? ftp ? http ? irc ?

---

### Post by shade11 on 2005-10-26
Http server.

---

### Post by herrpoon on 2005-10-26
This is very easy to accomplish with ubuntu, I followed the following guide:[https://wiki.ubuntu.com/ApacheMySQLPHP?highlight=%28apache%29](https://wiki.ubuntu.com/ApacheMySQLPHP?highlight=%28apache%29) which includes PHP and mysql (LAMP) which you may or may not need.

---

### Post by shade11 on 2005-10-26
Do I need an ISP?

---

### Post by dbott67 on 2005-10-26
[quote=shade11]Do I need an ISP?[/quote] 
I think you mean, "Do I need a web hosting company?" It depends. Most ISPs do not want their end-users to be hosting websites and the like and some will even go so far as to block certain types of traffic, which would force you to use a non-standard port to host your website.

It also depends on what you want to do:[LIST=1]
[*]Is this purely for learning and playing around, or is it for a legitimate site that you want to host?
[*]Do you want to register a domain (i.e. [www.yourname.com)?]("http://www.yourname.com%29?")
[*]If so, best to let an ISP/WebHosting Company register the domain and DNS stuff and let them host it.
[*]If it's just for educational purposes, just set up the server and use your external IP address as the URL (i.e. [http://209.xxx.yyy.zzz]("http://209.xxx.yyy.zzz")) and have fun.[/LIST]_**Also keep this in mind:**_

Most broadband ISPs offer asymmetrical bandwidth --- meaning that your download speed is many times greater that your upload speed. For example, my DSL provider gives me 3.0 Mbps downstream, but only 320 kbps upstream. If you have a number of people accessing your locally hosted server, it would only provide them with 320 kbps, as well as basically choking off your ability to surf with any speed.

Check your ISPs "Terms of Service" (TOS) for hosting your own site. They may have limits on monthly bandwidth, or may not even allow it. If they don't, there are many low-cost ISPs available to host a site. The advantage is that they have lots of bandwitdth, but it's shared among all of it's clients. They also have the knowledge and skill to register your domain name, DNS settings, keep the server secure & patched, install & configure additional apps like PHP, Perl. etc., and even offer e-mail services. They can even co-locate a server, if desired.

Also check with your ISP.  Many ISPs offer 20-30 MB of storage as part of your monthly service fee.  Your site would be [http://www.yourisp.com/~yourname]("http://www.yourisp.com/%7Eyourname")

If you post more specific details of what you want to use the website for, I can give you much more specific advice.

-Dave

---

### Post by shade11 on 2005-10-26
What I mean is: I have a PC and i want it to become a server. What do I need to do? How do I make it a server. And do I need and ISP in order to make my server to work? That is what I need to know

---

### Post by dbott67 on 2005-10-26
BTW, with regards to pint #4 above, hosting your own server requires a lot of attention to detail for security purposes.  A simple misconfiguration can quickly result in your computer getting hacked.

If you have a small network at home, you can set up a webserver without ever putting it on the internet.  Everything would just be on your own private little 2 or 3 computer "internet".

-Dave

---

### Post by dbott67 on 2005-10-26
[quote=shade11]What I mean is: I have a PC and i want it to become a server. What do I need to do? How do I make it a server. And do I need and ISP in order to make my server to work? That is what I need to know[/quote]

One of the other posts has a link that will provide all the details to setup your computer to be a server, however:
[LIST=1]
[*]Who is going to access the server?  (friends, family, all sorts of people, just you)   
[*]What is it going to be used for? (information, file sharing, music, porn)   
[*]Will you require access from other locations?  (work, school, around the world)   
[*]Do you have high-speed internet? (dial-up, DSL, cable, satellite, T1, T3, OC3)   
[*]Who is your ISP?   
[*]Do you need a domain name or do you need one?   
[*]Do you have $10, $20, $50 per month to spend? [/LIST] Take another look at my first post and try to anwser as many of the questions that I've asked and I will try to give you the best advice to get you started.

-Dave

---

### Post by shade11 on 2005-10-26
It is going to be accesed by the public. Where people connect to it. The server is for the video game. Do I need internet access for it?

---

### Post by herrpoon on 2005-10-26
I'm slightly confused reading through this.  Do you want to run a server for this videogame or do you want to just have a simple web server (http)?  Either way, you're going to need a fair bit of bandwith (up and down), especially for the first option.  For something like this, you're better off renting a server from a company who specialise in stuff like this.  I run a webserver on my home connection but it's not like it gets many hits!

---

### Post by shade11 on 2005-10-26
I want a server for a video game. i thought I could use an http server but I guess not. So what do i do If i want a server for a video game?

---

### Post by herrpoon on 2005-10-26
Oh ok, I'm with you now!  Basically it depends on the game you are wanting to run, for instance if you were going to run a counter strike source server, you'd need to d/l the necessary server files and configure it etc.  If you do intend on doing something similar i.e. running a games server you're going to need a lot of bandwith (unless you're doing it for a LAN), something that most people don't have on their home connection.

---

### Post by trilo on 2005-10-26
I'm confused.

You have "Jade Red Webmaster/ Videogamevillage Mod/ Programmer" in your sig. So, you're a  programmer and you moderate a forum for games but you don't know if you need the internet to run a game server?

/me reaches for the bag of troll munchies...

---

### Post by shade11 on 2005-10-26
I have never done servers before. It is new to me. I am a programmer. Not someone who knows server stuff.

---

### Post by noigeaR on 2005-10-28
this is a joke, right? :shock: 
[http://www.ubuntuforums.org/showthread.php?t=82081]("http://www.ubuntuforums.org/showthread.php?t=82081")
you ask us how to setup a server for a game you're going to program yourself? :confused:

edit: should have seen the "age 14" in your profile :p
of course, if you write a game client yourself you also have to write the server software youself. i recommend spending some time (a lot of time actually) on learning some basics about distributed systems, client/server models, communication protocols like tcp/ip etc. before even starting to think about programming a multiplayer game.

---

### Post by hidamari no tami on 2005-10-30
[QUOTE=dbott67]BTW, with regards to pint #4 above, hosting your own server requires a lot of attention to detail for security purposes.  A simple misconfiguration can quickly result in your computer getting hacked.

If you have a small network at home, you can set up a webserver without ever putting it on the internet.  Everything would just be on your own private little 2 or 3 computer "internet".

-Dave[/QUOTE]

How can I go about only allowing access to people who are connecting to the internet from inside my router? I'm also new to servers, and I'm setting up one for people here to aid in file transfers and playing private multiplayer games and so forth. I guess basically a general use server, won't be using it for hosting a web site or anything of the like, so I'd like to block access to everyone that doesn't live here.

Any threads, places on the wiki, or such that anyone can recommend?

Thanks.

---

### Post by jjoyner on 2005-10-30
Shut off any ports on your router that may be forwarded to your server IP and disable DMZ.  Also, you all need to visit Wikipedia and search some of these terms as I do not like what I am reading so far regarding you guys and routers...it's kinda scary....:???: 

[QUOTE=hidamari no tami]How can I go about only allowing access to people who are connecting to the internet from inside my router? I'm also new to servers, and I'm setting up one for people here to aid in file transfers and playing private multiplayer games and so forth. I guess basically a general use server, won't be using it for hosting a web site or anything of the like, so I'd like to block access to everyone that doesn't live here.

Any threads, places on the wiki, or such that anyone can recommend?

Thanks.[/QUOTE]

---

### Post by dbott67 on 2005-10-30
[QUOTE=jjoyner]Shut off any ports on your router that may be forwarded to your server IP and disable DMZ.[/QUOTE]

In addition to the above, you can install a software firewall (like firestarter) and only allow local IP addresses of your computers to connect (i.e. 192.168.1.100-110 or whatever your local subnet is).  You would need to make sure that you keep the necessary ports open for whatever applications your server would be running.

**_Here's some food for thought about software firewalls:_** 
If you have any ports forwarded to any client PCs (such as BitTorrent or other file-sharing apps) or you have a wireless network, I would recommend installing software firewalls on each PC and server.  The firewall would help prevent the spread of worms, viruses and other nasties that may get picked up by the XP clients.

Personally, I think that jjoyner's advice is enough, a software firewall on the server (and on the clients) may only add another layer of sophistication and potential for problems.  However, depending on what clients will be accessing the server (i.e. Windows XP), it may be wise to take this route, as a Windows XP computer that is infected with a virus or spyware may be able to be used to attack other computers behind the router, including your server.

Just make sure that you always apply any software updates as they become available for both PCs and server, run anti-virus and anti-spyware on Windows clients and don't eat yellow snow.

-Dave

---

### Post by shade11 on 2005-11-08
Ok. I think I finally understand it now.

---

