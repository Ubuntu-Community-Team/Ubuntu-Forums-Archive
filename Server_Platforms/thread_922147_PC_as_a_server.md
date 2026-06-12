---
title: "PC as a server?"
date: 2008-09-17
forum: Server Platforms
---

### Post by zx6r1033 on 2008-09-17
I keep reading these threads where people are using standard PC equipment as servers. Since I have a lot of spare stuff floating around right now, I was thinking about seeing what I could scrounge up, but the whole idea of setting this up is foreign to me. I did a google search in an attempt to at least get a starting point, but all it turns up are different Xserver platforms and gaming things. What is actually required for servers? I would assume you don't need video cards, monitors, or anything like that? How does it show up on your network (if at all)? Are there any articles floating around that will actually get me started?

---

### Post by tuxxy on 2008-09-17
Yes, the [server guide]("https://help.ubuntu.com/8.04/serverguide/C/index.html")

---

### Post by zx6r1033 on 2008-09-17
> **tuxxy said:**
> Yes, the [server guide]("https://help.ubuntu.com/8.04/serverguide/C/index.html")

that is a great guide and I have already read it, as I have the stickies in the forum, but none really describe the components needed for the computer itself or how they are used.

---

### Post by Drezard on 2008-09-17
I built my server out of a old desktop i had lying around. 

I would advise just using a copy of the ubuntu desktop until you are familar with the command line. 

But, to answer your questions, you can use just a normal desktop box. No extra gear in the box needed.

From there you should be able to use the Server Guide (referenced above) to set it up.

---

### Post by SunnyRabbiera on 2008-09-17
These days any PC can be converted into a server, it seems like parts are better and more energy efficient.
But if you are running a full network server then I would not advise it, a webserver yes but a full network server no.

---

### Post by netztier on 2008-09-17
> **zx6r1033 said:**
> I would assume you don't need video cards, monitors, or anything like that?

Well, normal PC hardware doesn't always like to boot in absence of a video card, and depending on the BIOS, it likes to have a keyboard connected.

As for the video card: rip out any fancy 3D-Cards that need fans etc, and drop in a simple, passively cooled AGP or PCI card (of course PCI-E is also ok if the hardware supports it).

To start, this is all well and you can be a happy camper with recycled desktop-class hardware - that's how I started as well.

As soon as you're going to run the box 24x7x365, it might be worth having a closer look at proper airflow through the box. It will be about finding a compromise between noise and cooling performance for CPU and hard disks; lots of airflow is good, but generates more noise. Having speed-controllable fans in the right place will do a lot of good for the longevity of your hardware.

The choice of hard disks might also come into play: there are "server" versions of some drive models, engineered for 24x7 service and thus more appropriate for the job.

And then of course, redundant power supply , choice of Gigabit NIC, RAID for the hard drives...

regards

Marc

---

### Post by AndyCooll on 2008-09-17
At it's most basic any pc can be a server. The moment you share a folder with another computer then that pc is "serving" files to other pc's. And if you share your printer on your home network then that pc is becoming a "print server".

So you can easily setup another pc and simply have it sit on your home network as a file server or print server. And you can use a default Ubuntu install for that.

Clearly you can then advance from there. for instance you could make it headless so that it doesn't require a monitor and you control it from a remote command line. And you can use it for different features, and the guide indicates some of these extra choices.

You can make it as simple or advanced as you wish, it's up to you.

:cool:

---

### Post by TurboRush on 2008-09-17
How much horsepower you need depends on what you want to do.

I pieced together a lowly p4 with 256m of RAM that sits in the corner with no keyboard or monitor that handles my (low volume) website, media server for my PS3, and acts as a backup server for my other computers.

I access it exclusively via SSH and Web front ends...

---

### Post by bigfatdummy on 2008-09-17
Some sound advice posted above. 

I use a pc purchased right off the shelf for my media server. I have Ubuntu running on it with Boxee. I used a Dell XPS as a webserver for years. I still use an old PIII desktop as a windows 2000 server to run my companies accounting software. With only 10 user licenses, the load on it is pretty light. I used a P4 desktop to run MS SQL server for several years and never had a single issue. I currently use a Dell Dimension 2400 desktop with windows 2000 server on it to run our antivirus software (Trendmicro).

So as stated several times above, it really depends on what you will be using the server for.

---

### Post by Krupski on 2008-09-17
> **zx6r1033 said:**
> I keep reading these threads where people are using standard PC equipment as servers.

Q: What's the difference between a "Server" and a PC?

A: About $4000.

---

### Post by billgoldberg on 2008-09-17
> **zx6r1033 said:**
> that is a great guide and I have already read it, as I have the stickies in the forum, but none really describe the components needed for the computer itself or how they are used.

I would think anything that goes into a normal pc, without the graphics and sound card. 

You don't need a monitor. 

You can remote control it from another pc.

---

### Post by Krupski on 2008-09-17
> **netztier said:**
> Well, normal PC hardware doesn't always like to boot in absence of a video card, and depending on the BIOS, it likes to have a keyboard connected.
..................
The choice of hard disks might also come into play: there are "server" versions of some drive models, engineered for 24x7 service and thus more appropriate for the job.

And then of course, redundant power supply , choice of Gigabit NIC, RAID for the hard drives...

regards

Marc

An under-$200 Intel motherboard has RAID built in, gigabit LAN built in, supports no keyboard, no monitor booting and has (lousy) video built in which is more than suitable for installation and testing.

Server grade hard drives can be easily had and setup as any kind of RAID array one needs.

Make sure the machine stays cool and has reliable power (i.e. a UPS) and you have a machine which is 100% as good as any overpriced "server".

---

### Post by zx6r1033 on 2008-09-17
Sound/Cooling are not an issue. I have a very large house, and currently my modem and router are both sitting in an otherwise unoccupied room. 

I am somewhat familiar with command lines for ubuntu... I have been using it for about a month now. GUI is still preferred, but then again, controlling the computer remotely is the goal anyway. Most of the spare components I have kicking around have the ability to wake on LAN. Does Ubuntu support this? (I haven't actually looked for that information or read far enough into the how-tos yet.)

I had two overall goals in mind, but it is still just in the idea stages for both. The first was a low power web server for a low traffic site. Storage would only need to be a couple of gb at most. The second would be a home server/storage for home videos. (I do a lot of video editing). That will require a bank of HDs... my current plan is for 6tb. But that computer wouldn't be on all the time... maybe only about 6 hours a week.

---

### Post by y@w on 2008-09-17
> **SunnyRabbiera said:**
> These days any PC can be converted into a server, it seems like parts are better and more energy efficient.


You've found that consumer-class hardware is more reliable than server-class hardware? Either you're buying crap for servers or over-paying for your desktops :)

---

### Post by windependence on 2008-09-18
> **y@w said:**
> You've found that consumer-class hardware is more reliable than server-class hardware? Either you're buying crap for servers or over-paying for your desktops :)

Agreed. That being said, it really depends on what you are going to do with the "server". If you just want a file server for your home network, just about any old PC will do. If you are going to run a production web site for say, ecommerce, then you really should be running on server class hardware. 

-Tim

---

### Post by Krupski on 2008-09-18
> **windependence said:**
> Agreed. That being said, it really depends on what you are going to do with the "server". If you just want a file server for your home network, just about any old PC will do. If you are going to run a production web site for say, ecommerce, then you really should be running on server class hardware. 

-Tim

I don't mean to be a pain in the bee-hind... but could you give me an example of, say, a hard drive that would be used in an e-commerce website server?

How would it compare to, say, a Western Digital "Black" series SATA hard drive?

The way it's spoken about, one would think that a "server" hard drive would be an ultra fast, ultra reliable device that cost 5X as much as a "consumer" drive.

I haven't been able to find any (although I would like to).

Thanks!

---

### Post by jamesrfla on 2008-09-18
I run a web server (apache2), mail server (citadel), SSH, Samba, and Terminal Server on my Ubuntu Desktop Edition. The box I use is a HP Media Center m7160n Desktop PC. You can use any desktop PC for a server. A lot of people use a old box and make it a file server and put it in their closet. If you are looking for performance I would use the Ubuntu Server edition. Unless your planing on doing real server stuff with it I would get a real server computer. If not then stick with a plain desktop PC.

---

### Post by nerdzero on 2008-09-18
> **Krupski said:**
> I don't mean to be a pain in the bee-hind... but could you give me an example of, say, a hard drive that would be used in an e-commerce website server?

How would it compare to, say, a Western Digital "Black" series SATA hard drive?

The way it's spoken about, one would think that a "server" hard drive would be an ultra fast, ultra reliable device that cost 5X as much as a "consumer" drive.

I haven't been able to find any (although I would like to).

Thanks!

A "real" server would probably have multiple SCSI drives or SSD in a RAID configuration. This would cost a couple thousand dollars or more.

A home server can do just fine with one or more IDE or SATA drives in whatever configuration you want.

You can head over to newegg.com and compare the specs (and prices) of all kinds of hard drives.

---

### Post by jamesrfla on 2008-09-18
> **nerdzero said:**
> A "real" server would probably have multiple SCSI drives or SSD in a RAID configuration. This would cost a couple thousand dollars or more.

A home server can do just fine with one or more IDE or SATA drives in whatever configuration you want.

You can head over to newegg.com and compare the specs (and prices) of all kinds of hard drives.

Thats what I am talking about. I would recommend using SATA because it is faster.

---

### Post by cariboo on 2008-09-18
Since nobody else has linked to it, have a look at this page to see what common software components make up a server.

[http://www.howtoforge.com/perfect-server-ubuntu8.04-lts](http://www.howtoforge.com/perfect-server-ubuntu8.04-lts)

Jim

---

### Post by windependence on 2008-09-19
> **Krupski said:**
> I don't mean to be a pain in the bee-hind... but could you give me an example of, say, a hard drive that would be used in an e-commerce website server?

How would it compare to, say, a Western Digital "Black" series SATA hard drive?

The way it's spoken about, one would think that a "server" hard drive would be an ultra fast, ultra reliable device that cost 5X as much as a "consumer" drive.

I haven't been able to find any (although I would like to).

Thanks!

You're not a pain in the behind at all. Let me explain. I think you really want to know what "server class hardware" is.

A hard drive is a bad example here. What I am referring to is say a motherboard of say Tyan, or Supermicro class vs say Gigabyte or ECS or some other consumer board. Usually a rack mount case with redundant power supplies. As for hard drives, it used to be SCSI would be considered server class and still is but SATAII is in my data center as well and catching up fast with SCSI. Even there, for example Seagate and Western digital have different SKUs for "home" and "server" versions of their drives. Think of it as "normal" and "heavy duty".

-Tim

---

