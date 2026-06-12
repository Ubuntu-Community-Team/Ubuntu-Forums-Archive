---
title: "Server vs Normal PC?"
date: 2008-03-15
forum: The Cafe
---

### Post by intense.ego on 2008-03-15
I'm thinking of buying a cheap machine to use as a file server, media server, and torrent server in my house. What is the difference between these two in terms of use and operation:

1) [PC](http://configure.euro.dell.com/dellstore/config.aspx?b=&c=uk&cs=ukbsdt1&kc=D4X20001&l=en&m_30=138820&oc=D032002&rbc=D032002&s=bsd")

2)[Server]("http://configure.euro.dell.com/dellstore/config.aspx?b=&c=uk&cs=ukbsdt1&kc=RS29003&l=en&oc=SV1T1051&rbc=SV1T1051&s=bsd")

BTW: I know one is a server and one is a pc. If the pc can do more how come it is only 10 pounds more (and that when the server is on 72% discount)

---

### Post by LaRoza on 2008-03-15
The first one is dead (server error)

A server is software, or a computer that runs such software. 

Assuming you are buying the hardware, not the software, you can use any hardware that fits your budget and needs.

---

### Post by amingv on 2008-03-15
Some servers (hardware, that is) are designed to fit, for example, more hard drives, interface cards or processors than normal desktops; or made so that you can have many without clutter. Other than that a server is not much different from a regular computer. If you don't plan to make anything. exceptional, a regular PC should be enough, I, for example, use a regular one, and old for that matter.

---

### Post by intense.ego on 2008-03-16
I've updated the link on the first post so that it works. Is it possible to use a server box as a normal pc, or is that only possible the other way around? also, the processor the server comes with is an AMD opteron. What makes this a "server processor" and not a regular one? How does the performance between the two compare?

---

### Post by Martin Witte on 2008-03-16
It depends how you plan to back-up your data, if I had to pick I would go for the PC as it looks more powerful, if I read the option list correct there is an option to configure it with disk mirroring, I would consider that for server use

---

### Post by jalebi on 2008-03-16
Aren't servers built to run the whole time, and therefore won't overheat or crash?

---

### Post by rocktorrentz on 2008-03-16
I've  run an old P4 box in my loft 24/7 for about a year and it's never overheated or crashed. However server components are often of higher quality than consumer desktop components.

---

### Post by popch on 2008-03-16
In this case, I would tend to buy the server. Processing power is nearly irrelevant for the kind of server you want to install. Servers usually have faster disk controllers and faster NICs. Beware, though: I have no idea whether this applies to the actual products you are considering.

---

### Post by banewman on 2008-03-16
I did a lot of googling for a home server and most sites recommend - because of the low load a home server experiences - to go for the least resource hungry system.
I've had a pent3 800mhz box as a file/media server and torrent box for a year and it is so underburdened I'm setting up a pent2 400mhz as its' replacement.
:)

---

### Post by intense.ego on 2008-03-16
I have an old (well, not really old but unused) pentium d 3.2ghz with 512mb RAM which i could use instead, though it wouldn't be as conveniently placed. 

Should I create a new thread about advice, or do you have any here?

---

### Post by banewman on 2008-03-16
As it was my first home server - and a learning experience - I started with xubuntu, nfs for file sharing (being behind a router it is a secure lan) and rtorrent for, obviously, torrents.
Couldn't be happier.
Now that I know more the next server will be cli - but still nfs and rtorrent.
:)

---

### Post by intense.ego on 2008-03-16
can you control rtorrent remotely (thru the internet)? otherwise i would prefer to use ktorrent. 

I know nothing about remote desktop sessions and the like, so how would I get about connecting into one computer from another on the same wireless network?

---

### Post by banewman on 2008-03-16
I use vnc to connect to my home server (which runs headless) in the lan - don't use an external comp to access it but ssh would be the prog to do that - and you could control rtorrent the same as any torrent client - vnc or ssh.

---

### Post by argie on 2008-03-16
> **intense.ego said:**
> can you control rtorrent remotely (thru the internet)? otherwise i would prefer to use ktorrent. 

I know nothing about remote desktop sessions and the like, so how would I get about connecting into one computer from another on the same wireless network?

There is a web interface, but it doesn't have any security features: 
[http://code.google.com/p/rtgui/](http://code.google.com/p/rtgui/)

---

### Post by jayson.rowe on 2008-03-16
There some other differences between "Desktops", "Workstations" and "Servers".

All things similar (hardware), a "Desktop" will actually usually be faster (benchmarks). Workstations and Servers are actually built more for stability than for speed. A Workstation (if you are looking at Dell, think Dell Precision Workstation), and a Server usually have different chipsets, and sometimes different processors, although, often, you can get Workstations and Servers w/ Desktop CPU's. The chipsets used generally require  FB-DIMMs for Memory, which although more stable (as they provide on-the-fly error checking and correcting), are far more expensive than regular DIMMs (could come into play if you decide to upgrade your RAM later), and are usually [marginally] slower than traditional DIMMs, and have higher latencies.

Also the speed of the RAM is usually slower as well - a typical "high-end" desktop (either AMD or Intel based) will generally be running at least DDR2-800 (PC6400), but a Opteron or Xeon based Workstation or Server will generally be running DDR2-667 (PC5300).

Also, you may find some SATA based Servers and Workstaions, SAS (SCSI Attached Storeage) is also more common in Servers and Workstations, and although the drives can be much faster (up to 15,000 is common, 10,000RPM is considered 'low end'), the drives are FAR more expensive than a comparable (think WD Raptop 15K RPM) SATA Drive.

Generally, in terms of [base] hardware, there will be little difference between a Workstation and a [tower] Server, however a Workstation will generally be fitted with a more powerful graphics card such as an Nvidia Quadro or a ATI/AMD FireGL. Usually servers will have basic integrated on-board video. Also, despite their high pricetags, those Quadros and FireGL's aren't always great for gaming either - they are tuned for high end 3d modeling.

Hope this helps clear some things up for you.

---

### Post by Mike'sHardLinux on 2008-03-16
intense.ego,

Your older server would be perfect for a home server. In fact, it has more horsepower than you really need. Right now, I am using a 1GHz P3 with 512MB of RAM for my file/web server. I am actually hosting a website for my school's chapter of NTHS. I plan on hosting more sites. Anyway, I chose this system, compaq iPaq, because it uses very little power, especially compared to a "real server". It seems to have plenty or processing power for me.

But, there is a huge difference between a real server and using regular desktop hardware. You can run any hardware 24/7, but server hardware is designed to run 24/7. Also, the hardware architecture of the motherboard, cpu,   RAM, drives , and the interfaces are designed to work with large datasets quickly, and also with fault tolerance and reliability in mind. Things like ECC RAM and [true] hardware RAID make a real server more robust than a desktop. Also, you generally see servers with larger amounts of RAM than the average desktop and server cpus like the Opteron have larger onboard caches (well, at least that used to be the case) than regular desktop cpus. How often do you see a desktop with 32GB or more of RAM? :)

From a functional standpoint you can run any service you want on  your desktop that can be run on server hardware. If you can, I think you should really try to make your server be command line only. You can do anything from the cli, and I personally think you will learn more about Linux this way.

You can do ANYTHING remotely that you would do locally on a server. You would use ssh to do this. When it is set up properly, it is VERY secure. Also, there are applications that provide a cli-based gui to make traversing the cli easier. For example, I sometimes use MC (Midnight Commander) when I need to move files around on my server. There are even cli web browsers - ***elinks*** and ***lynx*** to name a couple.

You ought to go ahead and get your server going and start experimenting. There's tons of tutorials on this forum and on websites like [howtoforge]("http://www.howtoforge.com"). Just decide what you want to do first and find a tutorial. Whatever commands the tutorials have you using, try to learn more about them. Use the ***man*** command to learn the options available for those commands. Look at sample config files for the services like ***ssh*** and ***httpd***, or whatever services you will be running.

---

### Post by jalebi on 2008-03-16
the differences are pretty much what the people above me said. Its probably a lot more economical for you to use an old PC than buy a new one.

---

