---
title: "Setting up a server to learn"
date: 2009-09-16
forum: Server Platforms
---

### Post by ninc on 2009-09-16
I need some advice what kind of OS I should use. Basicly my needs are that my girlfriend should be able to use the computer normaly, play wow, surf the web etc. But I want it to be a dedicated server at the same time, so I can use it while studiyng and for diffrent home projects (host webpages, ftp, email server and more). And if you know a good HOWTO for the specific OS that you recommend. I currently use ubuntu and I was hoping I could use that.

---

### Post by R.Bucky on 2009-09-16
You could always operate an Ubuntu Desktop with Apache-MySQL-PHP stacked on top. However, a true server should be command line only. GUI installation for a server creates a storm of potential holes for those with malicious intentions. Your best bet for learning purposes would be an old box lying around that you can toy around and learn.

With that said, there are literally thousands of Ubuntu how-to posts just like this: [http://ubuntuguide.org/wiki/Ubuntu:Jaunty]("http://ubuntuguide.org/wiki/Ubuntu:Jaunty")

---

### Post by cdenley on 2009-09-16
I think you should just install LAMP on your desktop computer.
```

sudo tasksel install lamp-server

```
Assuming you don't need the server to be accessible from the web, you should make sure it is firewalled with either a hardware firewall (NAT router) or software firewall (UFW or GUFW) in case you make a mistake that could compromise your system.

When I read that thread title, I thought you were implementing some kind of artificial intelligence.

---

### Post by ninc on 2009-09-16
Not really, Im studying at Linköpings university in sweden and want to have something to toy around with and learn as much as possible from. I want to be able to expand it with my own programs and such as I learn more from my education. You where talking about a command prompt server, what OS should I use then. I can probably get my hands on some old crappy comp to fool around with. :)

---

### Post by cdenley on 2009-09-16
> **ninc said:**
> Not really, Im studying at Linköpings university in sweden and want to have something to toy around with and learn as much as possible from. I want to be able to expand it with my own programs and such as I learn more from my education. You where talking about a command prompt server, what OS should I use then. I can probably get my hands on some old crappy comp to fool around with. :)

Ubuntu Server does not have a GUI by default. I usually use Ubuntu Server for servers, and I would recommend it for beginners because this forum is a great resource. Choosing a Linux distribution is really just about personal preference, though.

---

### Post by trundlenut on 2009-09-16
> **cdenley said:**
> Ubuntu Server does not have a GUI by default. I usually use Ubuntu Server for servers, and I would recommend it for beginners because this forum is a great resource. Choosing a Linux distribution is really just about personal preference, though.

I agree with that, although unbuntu server can be a bit daunting to start with, as there is no gui, thanks mainly to this forum I have learnt an awful lot about linux and servers.

Also any old computer you can get hold of (unless it really is ancient) should have no problem with the server version - you don't have to worry about graphics card for starters, I would say you need a machine that will be attached to your network by ethernet rather than wireless though.  Once it's set up you can access it via SSH so you won't need a monitor (until you break it of course, you will sooner or later).

---

### Post by ninc on 2009-09-16
Ok well could a laptop work? Or is it to "squishy"? Any fun things you could can do on a server with good system specs? Mine for example: 

3,0 ghz dual core AMD 64bit
4gb ram
geforce 9800GT
1.5TB of hardrive space

---

### Post by fela on 2009-09-16
> **cdenley said:**
> Ubuntu Server does not have a GUI by default. I usually use Ubuntu Server for servers, and I would recommend it for beginners because this forum is a great resource. Choosing a Linux distribution is really just about personal preference, though.

Another good one for both beginners and experienced Linux nerds is Debian - it's got great flexibility when you install it and there are no separate 'editions' to choose from - apart from the old stable, unstable, testing and experimental (which are actually different versions, not editions). Plus alot of the stuff in Ubuntu is applicable to Debian since Ubuntu is based on Debian.

Ubuntu is great aswell though, for beginners anyway (I find I don't really like its lack of flexibility...could just be me).

Off topic:

> **ninc said:**
> 3,0 ghz dual core AMD 64bit
4gb ram
geforce 9800GT
1.5TB of hardrive space

That's almost exactly the same specs as me :)

---

### Post by ninc on 2009-09-16
> **fela said:**
> 


That's almost exactly the same specs as me :)


Sweet, what do you use your server for mainly?

---

### Post by Johnsie on 2009-09-16
> sudo tasksel install lamp-server

+1

lamp-server on a desktop runs quite nicely and you can even disable gnome from coming on at startup if you want to.

---

### Post by fela on 2009-09-16
> **ninc said:**
> Sweet, what do you use your server for mainly?

Actually, that's the same specs as my desktop.

My server has an AMD64 athlon (2.2ghz), it's used for everything from a file server, computational beast, geek-box, backup server, downloader, etc etc etc :)

---

### Post by cdenley on 2009-09-16
> **fela said:**
> Another good one for both beginners and experienced Linux nerds is Debian - it's got great flexibility when you install it and there are no separate 'editions' to choose from - apart from the old stable, unstable, testing and experimental (which are actually different versions, not editions). Plus alot of the stuff in Ubuntu is applicable to Debian since Ubuntu is based on Debian.


All the different "editions" are simply different default configurations. They are all the same version of ubuntu with the same repos. The debian-style alternate installers for ubuntu are still available last I checked.

The most significant difference between Ubuntu and Debian, in my opinion, is their different release cycles. Which one is better depends on your personal preference.

---

### Post by fela on 2009-09-16
> **cdenley said:**
> All the different "editions" are simply different default configurations. They are all the same version of ubuntu with the same repos. The debian-style alternate installers for ubuntu are still available last I checked.

The most significant difference between Ubuntu and Debian, in my opinion, is their different release cycles. Which one is better depends on your personal preference.

Really? I didn't know there was a Debian style Ubuntu installer - I mean debian style as in being able to choose to install a variety of stuff when you install the OS (from the internet if you like).

Also, yeah I do prefer Debian's release cycle. Ubuntu just doesn't seem mature enough when it's released (and the LTS is too old IMO).

---

### Post by Sporkman on 2009-09-16
> **ninc said:**
> Ok well could a laptop work? Or is it to "squishy"? 

Laptops area good choice for servers, actually, due to their small size & low power usage. The only downside is you can't upgrade or swap out parts as easily.

---

### Post by Udayakiran on 2009-09-18
> **ninc said:**
> Ok well could a laptop work? Or is it to "squishy"? Any fun things you could can do on a server with good system specs? Mine for example: 

3,0 ghz dual core AMD 64bit
4gb ram
geforce 9800GT
1.5TB of hardrive space

Aint that overkill?

---

### Post by Udayakiran on 2009-09-18
> **Sporkman said:**
> Laptops area good choice for servers, actually, due to their small size & low power usage. The only downside is you can't upgrade or swap out parts as easily.

And i dont think they are built for running continuously for long times. It should be placed in a well ventilated place. Quite a number of users have used laptops as servers.

---

### Post by trundlenut on 2009-09-18
> **Udayakiran said:**
> Aint that overkill?

Certainly a bit more power than my older server - a 550mhz PIII with 512mb of ram and a whole 30gb of storage.

---

### Post by hessiess on 2009-09-18
Laptops are fine for servers but you need to the dust out regularly and keep an eye on the temperature as they overheat very easily.

Also I recommend using SFTP instead of FTP as its a much more up to date protocol which works flawlessly with modern networking technology and is also a lot more secure.

---

