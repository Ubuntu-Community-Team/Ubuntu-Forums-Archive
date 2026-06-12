---
title: "[Noob Question] - What prevents my browser/browser extension from accessing my stuff?"
date: 2021-03-09
forum: Security
---

### Post by Swan_DB on 2021-03-09
[COLOR=#000000][INDENT][SIZE=4][FONT=arial][SIZE=3][Noob Question] [/SIZE]- [SIZE=2]What prevents my browser/browser extension from writing to my hard-drive, or gaining access to my wifi network? Specifically, hypothetically, ELI5 (Explain Like I'm 5 years old, or in layman's/simple terms) how would a malicious browser extension on my desktop that I am at right now, access my.... idk, my "smart doorbell security camera"?

My brain is saying: They'd need to get into my OS from my browser, which seems like if I simply clicked a button on a website (or installed a malicious browser extension), it could happen via: That "button"/extension downloads a program that executes writing code that breaks my wifi network passwords or by-passes the passwords if that's possible?, then finds my "smart doorbell security camera" and starts sending that video data back through the wifi network, then back through my OS/desktop, then back to... the web and the malicious browser extension's author can download my "smart doorbell security camera" video data.

Any input/details on this would be great, thanks in advance.[/SIZE][/FONT][/SIZE][/INDENT]
[SIZE=4][FONT=arial][SIZE=2]
[/SIZE][/FONT][/SIZE]

[/COLOR]

---

### Post by TheFu on 2021-03-09
Browser extensions are written in a language called Javascript.  This is a full featured language that can be used to create servers. All "node" or "node.js" server programs use javascript at the core.  Javascript is network-aware. That means it can scan any network it wants, unrestricted. This is easy.

Access to the hard drive on the same computer is harder, but access to networked storage is not, strange as that may seem.

The browser has rules that are supposed to prevent any javascript from accessing the local computer in ways that the browser doesn't approve. However, because browsers are extremely complex, they are often full of bugs for even the most simple things.  For example, Incognito-mode has been broken by all the browsers multiple times since it was first introduced.  Nefarious people seek out these bugs and take advantage of them.  That's how they might gain access to the local machine.

But as stated above, network stuff is easy and approved by browsers already. So, an extension can scan your network at home looking for camera, network storage devices, android devices, doorbells or anything else.  Each of the local LAN devices has a MAC address which often is tied to the hardware used. Google "mac address lookup" and you'll find databases where you can enter any MAC and be told who made that device.  This can be used for ethernet, wifi, and bluetooth devices. The same idea exists across all of them and on the same subnet, the MAC address is required. It is part of how ethernet works on a LAN.  So ... iPhones, cameras, doorbells can become known as those devices.  The specific device can be used to request an attack from the C&C (command and control) servers spread around the internet, always changing, in what seems to be random ways.  

So not the extension (or even a web page full of javascript that you allowed to run) knows the device type and has been provided with either the default login or a known security failure in the specific device ... and it can access the camera feed.  Once the camera feed is known, it can relay that data anywhere.  So the creepy person (or organization) gets notified that a new webcam feed is available and their servers start recording that feed looking for interesting things. 

[https://www.howtogeek.com/716771/did-you-know-browser-extensions-are-looking-at-your-bank-account/](https://www.howtogeek.com/716771/did-you-know-browser-extensions-are-looking-at-your-bank-account/) might explain things a little better for how extensions can see everything your browser can see.

If you have a little networking knowledge, this all becomes very easy to see. If you don't, I'm afraid to say that just because you can't see something, that doesn't mean it isn't a security risk.

If your OS is already on your network, they don't need to break any network password. It already has access to your network, unless you've setup firewalls between devices.

Be especially worried about IoT devices that "just work" and provide access to any device inside your home using a smartphone app from anywhere in the world without you needing to touch your router settings.  Those are the real security problem items.  If a device won't work without the internet, that's a good sign that you don't want it.  I always ask the sale person - can this work at my remote cabin without any internet, including initial setup, ever?  If they say no, I don't want it in my home.

If you want to learn how easy it is to scan a subnet for specific devices, check out "nmap fingerprinting" in a web search.

I doubt I've made this simple. Sorry if it isn't.

---

### Post by Swan_DB on 2021-03-09
I do know some networking stuff, but very very little, like "5 layers" and what a LAN is, and MAC Address I've seen before, but that's about the extent of my knowledge right now.

You've given me some great things to google search for, I just wish you had kept writing, lol.  Thank you very much : )

Edit:  I'm making some of this comment more for my own reference later, but if someone feels like replying, please do, it will be appreciated : )

> [COLOR=#000000]Javascript is network-aware.[/COLOR] Can someone explain this, it doesn't make sense to me after a cursory google search.  Is it suppose to say "NODE Javascript is network aware", or is it just saying Javascript can easily interact with networks?

> [COLOR=#000000]If your OS is already on your network, they don't need to break any network password. It already has access to your network, **unless you've setup firewalls between devices.**[/COLOR] "Firewalls between devices" would this not be default in most things?  I'm on old tech from 2012, mostly, and everything I've used always requires a password approval.  My real example would be a Roku 1, from like 10 years ago, I still use it, and...  Wait a minute!  Youtube has a feature that says "play on TV" and that sumbitch finds my Roku 1 in the other room via wifi.  I am pretty sure though I need to enter a password, but maybe not, regardless, the password could be cracked as it's something like "password", lol.  That link you provided might lead me in the right direction for explaining "firewalls between devices"...  Or at least I know what to Google search for now.

I've heard to avoid the IoT stuff and for the same reasons you've stated, will do some Google searching on that.

> [COLOR=#000000]If you want to learn how easy it is to scan a subnet for specific devices, check out "nmap fingerprinting" in a web search.[/COLOR] nmap fingerprinting AOIHER#)*#  FACK!!!!!  I'm sitting here alone, in complete silence with just a faint hum of the fans in my PC, writing about "network hacking", and then....  BAM!  My iPhone alarm goes off full blast!!  Scared the crap out me, lol.  8-[  :shock:  
Just looked into "nmap fingerpriting" and that's crazy, and kind of depressing for some reason that someone can tell my OS relatively easily if they wanted to.

Again, thank you : )

---

### Post by TheFu on 2021-03-09
> **Swan_DB said:**
> I do know some networking stuff, but very very little, like "5 layers" and what a LAN is, and MAC Address I've seen before, but that's about the extent of my knowledge right now.

It is 7 layers, not 5, but that really isn't all that important.

> **Swan_DB said:**
> You've given me some great things to google search for, I just wish you had kept writing, lol.  Thank you very much : ) I'm prolific in these forums. Thousands of posts, if you can stand them. ;)

> **Swan_DB said:**
>  Can someone explain this, it doesn't make sense to me after a cursory google search.  Is it suppose to say "NODE Javascript is network aware", or is it just saying Javascript can easily interact with networks?
Network aware just means it is really easy in the language to access network locations of all types. That is common for many languages. Php, Perl, Python, Ruby, Javascript, and others all make it next to trivial to pull or send data over any network.  Most of these tools can create a simple web server in just a few lines of simple code.  Python2 and python3 do it in 1 line.  I think perl needs 5 lines.  They also make it easy to figure out your IP on the LAN and other network information, so that scanning all the devices and every port of those devices is easy.  That's all I meant by network aware.

> **Swan_DB said:**
>  "Firewalls between devices" would this not be default in most things?  I'm on old tech from 2012, mostly, and everything I've used always requires a password approval.  My real example would be a Roku 1, from like 10 years ago, I still use it, and...  Wait a minute!  Youtube has a feature that says "play on TV" and that sumbitch finds my Roku 1 in the other room via wifi.  I am pretty sure though I need to enter a password, but maybe not, regardless, the password could be cracked as it's something like "password", lol.  That link you provided might lead me in the right direction for explaining "firewalls between devices"...  Or at least I know what to Google search for now.

Most devices DO NOT run firewalls and they certainly don't block access for devices on the same LAN. That would be too inconvenient.  We all want stuff to "just work" when we connect it on our LANs, so for that to happen, there can't be any firewalling between devices.  Passwords are different.
Your Roku is an IoT device.  The FBI says you shouldn't allow that on the same LAN as your computer(s).  [https://www.fbi.gov/contact-us/field-offices/portland/news/press-releases/tech-tuesday-internet-of-things-iot](https://www.fbi.gov/contact-us/field-offices/portland/news/press-releases/tech-tuesday-internet-of-things-iot)

Anything with "smart" in the name is an IoT device.  That could be a speaker, TV, phone, tablet, thermostat, doorbell, garage door controller, light switch, power switch ... pretty much anything that isn't a full computer.

> **Swan_DB said:**
> I've heard to avoid the IoT stuff and for the same reasons you've stated, will do some Google searching on that. Your house probably has 5 IoT devices already.

> **Swan_DB said:**
>  nmap fingerprinting AOIHER#)*#  FACK!!!!!  I'm sitting here alone, in complete silence with just a faint hum of the fans in my PC, writing about "network hacking", and then....  BAM!  My iPhone alarm goes off full blast!!  Scared the crap out me, lol.  8-[  :shock:  
Just looked into "nmap fingerpriting" and that's crazy, and kind of depressing for some reason that someone can tell my OS relatively easily if they wanted to.
Well, sorta, but not really.  You asked about LAN stuff, so my answers/warnings were specific to that.  Things are different for people on the internet. But you should know that every web server you visit with any device it told a bunch on information about your computer, browser, javascript version, battery life and a bunch of other things.  [https://coveryourtracks.eff.org/](https://coveryourtracks.eff.org/) is probably the best tool for seeing what google, facebook, and pretty much any web server can figure out about you and your browser.  Basically, you are nearly unique on the internet. In my default setup, it doesn't work, since I don't allow javascript anywhere by default.  Just a few trusted places are allowed.  

If you really like to be scared, I can post a number of links that will make you want to disconnect, move to the mountains or an island, never use a cell phone or internet again. ;)  Yet, most people don't seem to realize that all internet connections are a negotiation.  They ask for everything they can get, but we don't have to provide it or agree to allow it.  

Much of the security and privacy work happens by being selected about what we allow into our networks.  Sometimes we decide that convenience is more important than privacy.  I have a roku3.  It isn't inside my network - it is on a "guest" subnet. I block thousands of domains there to limit tracking, but the roku really wants to send every click and parts of every show/movie/content we hear or watch back to the mothership to determine our likes/dislikes, interests and how to better sell us junk. Every channel we enable on the roku tells them more. When we connect the roku with a paid TV subscription, now all that data can be linked - bam - even more data that we didn't intend to leak.  Ever search on the roku?  Those are sent back too. [https://www.nytimes.com/wirecutter/blog/data-harvesting-by-companies/](https://www.nytimes.com/wirecutter/blog/data-harvesting-by-companies/)

Amazon, google, facebook all do the same things.  I have an amazon tablet.  It connects to the "guest" network too, but I use a VPN for it to connect into specific servers I run for the family. It is convenient. I don't use any Amazon applications for those connections or the VPN.  I do use it for shopping with the company, but they will see what I look at and buy anyway, regardless of the platform used, so I figure go for the most convenient device. When I play video or music using it, none of the amazon apps or anything from the amazon app-store are used.  Everything in an app-store reports back to the appstore that you are using it, for 13 minutes, and assume the current list of processes, RAM, storage, and your location (general or fine) is provided back.  Of course, each app can access much of that same data and provide it to the app creator. Sure, they aren't supposed to, but if they can, and get away with it, why not? Especially if they aren't in the same country. What do they have to lose for trying?  Worst case, their app gets removed, but it will sit on millions of devices for years and keep reporting back.

I didn't say this explicitly, but all the popular browsers can do these things today.

There isn't any bone-head way to explain things without years of background in networking, programming, routing, firewalls, sorry. About the best that most people can do it be smart, wonder about risks in visiting any websites with scary names or common misspellings for popular sites and use your brain.  Unfortunately, 10,000 correct answers followed by 1 bad answer is all it takes for bad stuff to happen.

By using a less popular desktop, we avoid many of the most common attacks.  With just a little more effort, we can be fairly safe on the internet provided we don't look for trouble.

---

### Post by Swan_DB on 2021-03-09
> [COLOR=#000000]If you really like to be scared, I can post a number of links that will make you want to disconnect, [/COLOR][COLOR=#000000]move to the mountains...  [/COLOR]

This made me laugh, thank you, I needed a laugh. Very interesting stuff to look into, thanks again, it is appreciated : )

marking this as [SOLVED]

---

