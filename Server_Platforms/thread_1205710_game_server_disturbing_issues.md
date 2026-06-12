---
title: "game server disturbing issues"
date: 2009-07-06
forum: Server Platforms
---

### Post by nvid1a on 2009-07-06
hi all, i want to share what is happening with a server i have on a hosting.

Me and a friend founded about a year ago a webpage dedicated to quake 3 here in my country and along with it we decided according with money we had at the moment to build a server as decent as possible to run up some quake 3 servers along with a teamspeak server.

So far all went good for about 6 months with our first ultra budget server that had this configuration:

AMD Athlon 64, 2.4 ghz, 1 mb Cache L2, Socket AM2
Foxconn AM2, Mini ATX Mobo, Chipset VIA K8M890
Geil 2x512 Dual Channel Kit DDR2-533
Realtek 8139 10/100 Integrated LAN
Maxtor 40gb IDE 7200rpm HDD

I know that PC will sound crazy from what can be called as a server but it worked about 6 months without hook ups, all mounted with Debian 32bit and a customized kernel for the computer.

After those 6 months we realize that the website was growing very fast and we needed a bigger server to mount more quake 3 server, more TeamSpeak server, a shoutcast server that turns on 3 times a week and 1 Counter Strike server.

So with a few bucks we manage to buy some hardware and the configuration left like this:

AMD Sempron Dual Core 2300, 2.2 ghz, 2x256 kb Cache L2, Socket AM2
Foxconn AM2, Mini ATX Mobo, Chipset VIA K8M890
Kingston 2x1024 Non Dual Channel Kit DDR2-800
Realtek 8139 10/100 Integrated LAN
Seagate 160gb SATA2 7200rpm 8mb + Maxtor 40gb IDE 7200rpm HDD

Again so far the server was working like a charm, but about 1 month ago the problems started and still we cant really know what is truly happening, we have theories with my friend but we dont know for sure what is going on.

The server randomly in the night, when the people play on the servers, it just freezes during a short period of time without responding to SSH commands, no nothing, the quake 3 servers become very very lag with 200ms but the server is still up without responding to anything, you can be seeing the HTOP while this happens and you cant get a refresh to see something, it just kicks you out of the SSH and sometimes it just stops to refresh and you have to enter again.

We could see that when this happens the server that normally uses 2 to 5 mbps of bandwidth it goes sky high to a sustained 10 mbps of outgoing bandwidth, incoming bandwidth keeps normal at 2 or 3 mbps.

Sometimes this happens during the day when no one is connected to the server, sometimes it takes minutes to unfreeze, sometimes it takes just seconds.

We changed the ethernet card with no luck, the problem wast that, we changed the linux distro from debian 32 to gentoo 64, then to debian 64, now debian 32 again, customized kernels, normal kernels, and the freeze lag is still there.

Yesterday we put the server to stress while having three 16 clients server full, a remote GTV connected to our server to see the matches, 1 TeamSpeak server up, the shoutcast radio server up and a counter strike server online.

The server just couldnt manage that, since the CPU usage was normal and not even above the 50% this freezes came in again and again, we count and registered about 5 freezes in 2 minutes, finally we had to bring down all the servers and just leave the TS and shoutcast up.

This is really disturbing and we dont know what is exactly, the server is on a hosting that has a 100mbps fiber WAN and this WAN is connected to a cisco administrable switch and our rj-45 jack is limited to 10mbps for internal reasons.

The question is...

Could be the motherboard that is dying ?
Could be the CPU that just cannot take that not mentioning that never goes up further than 50% ?
Could be the RAM that is failing ?
Could be the ethernet card that we need a real one and not that integrated one ?
Could be a problem with too many concurrent connections ?
Can this problem be related to the hosting switch and not to our server ?
Is a good solution to buy a new but decent server this time ?
Is this enough load to require some fresh and more reliable hardware ?

I would really appreciate any help or ideas, this is very very important for me.

Best Regards,

nvid1a.

Santiago, Chile

---

### Post by Thirtysixway on 2009-07-07
First thing that comes to mind is perhaps someone has access to your server?  If the outbound bandwidth is going up without reason, perhaps your server has been compromised.  Just a theory, though.

Are there a lot of users online when it happens?  You said you stress tested it, maybe there's too many people trying to use the server.  Also, check your cron jobs to see if maybe a cron is set to do something that's causing the server to crash.

---

### Post by nvid1a on 2009-07-07
> **Thirtysixway said:**
> First thing that comes to mind is perhaps someone has access to your server?  If the outbound bandwidth is going up without reason, perhaps your server has been compromised.  Just a theory, though.

Are there a lot of users online when it happens?  You said you stress tested it, maybe there's too many people trying to use the server.  Also, check your cron jobs to see if maybe a cron is set to do something that's causing the server to crash.

Since we mounted this server with my friend only the two of us has access to it by ssh, on the hosting itself the computer is only connected to a power cord and a network cable, and no one can access locally since no one knows the users and passwords.

But though we changed the ssh port from the normal 22 to 9653 to prevent attacks through normal ssh.

And yes when it happens it has a lot of people connected to the server, maybe about 100 people accessing the server to different services ( quake 3 servers, teamspeak, radio shoutcast, counter strike servers ), but as i could saw the CPU usage and memory usage are very normal at that point, both cores barely pass the 50% usage and memory barely goes up to 50 to 60% from the 2 gb of ram.

A server admin i know here told me that maybe the RAMs are failing and that maybe i should change them for a test.

Though we are using the cool n quiet feature of the amd cpu we have and other thing that keeps me thinking is that the RAMs are working to factory settings ( 800mhz at 5 5 5 15 1.8v ) and the CPU FSB is 800mhz... RAMs according to this are in 1:2 Ratio with the CPU... could be really a problem of sychronization when the load goes up ?... Or that maybe the rams in use are not a dual channel kit ?

The older RAMs we used were a GEIL dual channel kit DDR2-533 mhz.

About the crons we checked that and it isnt. 

Thanks for the answer.

---

### Post by abaden on 2009-07-08
You could try running [memtest86]("http://www.memtest86.com/") if you think the RAM is bad. That might be the case, but it sounds more to me like you're overloading the server, although that shouldn't be spiking your outbound traffic. The Sempron is an ok chip, but it has very little cache, and its architecture is a bit outdated. Has your site increased in popularity since you set this new server up? It may be time for yet another upgrade - you might want to try Core 2 Duo or Core 2 Quad's this time (or Core i5's as they are called now).


Alex

---

### Post by nvid1a on 2009-07-08
> **abaden said:**
> You could try running [memtest86]("http://www.memtest86.com/") if you think the RAM is bad. That might be the case, but it sounds more to me like you're overloading the server, although that shouldn't be spiking your outbound traffic. The Sempron is an ok chip, but it has very little cache, and its architecture is a bit outdated. Has your site increased in popularity since you set this new server up? It may be time for yet another upgrade - you might want to try Core 2 Duo or Core 2 Quad's this time (or Core i5's as they are called now).


Alex

I will do the memtest, i guess today to see if its really that. I agree about the sempron that has very little cache and its outdated but it was really a bargain at the moment. Yes, the site really increased popularity since this " new " server is up, about 2 or 3 times the people we had on the begining.

I was looking foward to a new upgrade using and intel core 2 duo, are they a lot better than amd for servers ?, i know that intel is better for experience but its more expensive, at least here in my country.

Thanks for your answer.

---

### Post by abaden on 2009-07-08
> **nvid1a said:**
> 
I was looking foward to a new upgrade using and intel core 2 duo, are they a lot better than amd for servers ?, i know that intel is better for experience but its more expensive, at least here in my country.

The current generation chips are. They're faster, cooler, and have more widespread chipset support than AMD's. The Q9550 is a Quad Core Intel chip that can be found for around $200 USD now in the US. If that's a bit too much, the E8400 is a very good dual core chip that's around $150 USD now. I have two Q9550's at the moment and they've both served me extremely well.


Alex

---

### Post by nvid1a on 2009-07-08
> **abaden said:**
> The current generation chips are. They're faster, cooler, and have more widespread chipset support than AMD's. The Q9550 is a Quad Core Intel chip that can be found for around $200 USD now in the US. If that's a bit too much, the E8400 is a very good dual core chip that's around $150 USD now. I have two Q9550's at the moment and they've both served me extremely well.


Alex

Thats one thing i was just about to ask you, the L2 and if its the case L3 caches, how affects the server performance and usability ?, Intel cpus have very large caches compared to AMD, even the core 2 duos E7000 have 3 mb L2.

Thanks very much for the advice, i will see the price tags around here for intel and look foward to make the upgrade.

---

