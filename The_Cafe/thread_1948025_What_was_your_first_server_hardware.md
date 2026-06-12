---
title: "What was your first server hardware?"
date: 2012-03-27
forum: The Cafe
---

### Post by Ms. Daisy on 2012-03-27
I'm planning on installing my very first server.  However, it's vital that I totally over-think it first (that's just how I roll, folks).  I plan on messing with Linux and Windows servers so all advice is welcome.

I'm considering building something, also looking at refurbished servers.  Its function will be to teach me how to run a server.  It will get totally abused in the process.

So tell me, what was your first server hardware? What's your favorite hardware? Anything I should avoid at all costs?

---

### Post by CharlesA on 2012-03-27
I've never actually had true "server" hardware. My home server runs off of desktop hardware that I've built from parts.

My first one was a dual core pentium with 6GB of RAM and 4TB of storage (RAID5 array). The New one was the same storage but it's now an i7 quad core with 16GB of RAM.

---

### Post by sffvba[e0rt on 2012-03-27
I decided to faff around with Ubuntu server to play around with SSH and also host my own blog and run a Minecraft server etc... and as I had a Samsung N150 Netbook lying around I decided to use it.  Nothing more was needed.


404

---

### Post by alphacrucis2 on 2012-03-27
Elliot 503. Had 8K 39 bit words of magnetic core RAM.

---

### Post by KiwiNZ on 2012-03-27
My first was Redhat on a simple converted old PC. I now have ubuntu on an IBM Tower Server

---

### Post by Dangertux on 2012-03-27
My first was Redhat 6 (NOT RHEL)  on a beat up old emachines tower running a cyrix chip (anyone remember those?).

I would not recommend ACTUAL server hardware -- though you can get it pretty cheap at places like savemyserver.com. It's power hungry and extremely expensive to run it for any extended period of time. 


If you can afford it, I would recommed a set up like Charles mentioned, there is no difference (essentially) for home usage. The big features you get with enterprise class hardware are higher end processors (Xeons, though you can put them in regular desktop hardware). And tons and tons of redundancy. Redundant power supplies etc... You also get the added advantage of remote administration tools like the dell remote access controller. There is an entire subculture of administration that revolves around those types of devices in and of themselves. You also will get better support for HBAs and FCOE equipment.

The choice is yours. For fiddling and learning the services though, a cheapo desktop system will work fine. 

If you do grab actual server hardware I recommend something in the dell x950 series (preferably 1950) it will be adequate for all your needs and you can pick one up for about 200 bucks US. You may have to buy SAS drives for it though , which can get pricey. 

Something else to consider if you're buying actual server hardware... A lot of it runs on 220 Volts and isn't auto sensing. Make sure you get something that can run on 110 unless you want to plug in your server in lieau of your dryer.

Hope this helps.

---

### Post by Bandit on 2012-03-27
First server was a K6-2 400 with 164MB DRAM running Slack7 :guitar:

---

### Post by Bandit on 2012-03-27
> **Dangertux said:**
> My first was Redhat 6 (NOT RHEL)  on a beat up old emachines tower running a cyrix chip (anyone remember those?).
HEHE Yep.. 30 bucks a chip at one time and run hotter then a industrial toaster from hell. :lolflag:

---

### Post by Dangertux on 2012-03-27
> **Bandit said:**
> HEHE Yep.. 30 bucks a chip at one time and run hotter then a industrial toaster from hell. :lolflag:


yep -- that's them lol

---

### Post by lisati on 2012-03-27
> **alphacrucis2 said:**
> Elliot 503. Had 8K 39 bit words of magnetic core RAM.

Sounds like an interesting machine to tinker with. I haven't used a machine with magnetic core memory for many years.

My first server [s]was[/s] is a Compaq SR1520AN with 1Gb RAM (it came with 512Mb), AMD Sempron 3200 CPU, 80Gb HDD, and amongst other things a seldom used TV tuner card (even when I was running XP on the machine).

---

### Post by BertN45 on 2012-03-27
My first server is still in use, see my signature. It runs Windows XP PRO and I do not change it, since I paid 90 Euros for the OEM CD and XP is still a nice system. I use it mainly as a file server first in Belgium and later here in the Dominican Republic. In the time I still worked in Brussels, I could access the server in Santiago from Belgium using the P2P Virtual Network Hamachi, that works for Linux and Windows. 

The system also runs the network monitoring software "The Dude", which allows me to see the service and the load of each PC and each link. There is even some monitoring of my phones, if they connect to the wifi.

I control the server through RDP.

---

### Post by papibe on 2012-03-27
Hi Ms. Daisy.

For testing and 'abusing' I would suggest a refurbished/re-certificated/Off-lease PC. I would even recommend going to buy it on a brick and mortar store for instance gratification :)

These days, in microcenter for instance, you can get a IBM/Lenovo or Dell P4, 1Gb RAM as low as $99.

Just my thoughts.
Regards.

BTW: here's my own [thread]("http://ubuntuforums.org/showthread.php?t=1435720&highlight=refurbished") with the same concern.

---

### Post by cariboo on 2012-03-27
For my first server, I bought a dual-cpu motherboard on Ebay. It used two MMX 233Mhz cpu's and 256MiB of 72 pin ram. It ran various sized hard drives but before it was retired I was running 4 40GiB hard drives. The BIOS wouldn't detect any hard drive over 8GiB, but the drives worked with zero problems. The biggest hassle was having to compile a new kernel every time one was released, as dual cpu support wasn't built into the Debian kernel at the time.

If I remember correctly, I spent more time re-painting the case, than I did actually assembling the thing. :)

This was back in 2000.

Currently all my server does is serve media files, so consumer grade hardware works well for my needs.

---

### Post by Dangertux on 2012-03-27
Here is another idea. If you are just wanting to learn the basics of administering a server, and you're not planning on buying actual server hardware. Have you considered renting a VPS?

They're extremely cheap, decent VPS setups for tinkering can be as low as $20 per month with providers like Linode. It's a virtualized system in their data center. You can buy as many as you want and tear them down and set them back up as many times as you want. The only difference is you don't have an upfront cost for hardware (not more than 50 bucks if you get a really nice VPS) and of course, you don't get to mess with the hardware. In this case that is actually a bonus considering you probably wouldn't be buying ACTUAL server hardware. A PC is a PC a server is a server, if you want to learn about the guts of a server you will actually have to buy that type of hardware. That being said, you also wouldn't be paying the electric bill for an actual server.

This would also alleviate the issue of possibly buying a bum piece of hardware.  

You can do anything with a VPS you can do with a regular system (except virtualize, but...I think they may allow you to enable nested paging so that may even be possible). But you could set up HA, clustering, load balancing and anything else you wanted (though you might have to rent more than one VPS for those) 

My only word of  warning if you do that, don't cheat by using their "pre-made images" or "helper scripts" upload your own image and do it from scratch.

---

### Post by rk0r on 2012-03-28
I use to be a datacentre engineer, government standard have IBM p570's for unix and some other high end models. For windows they use Dell poweredge gear.

A lot of today’s servers are running in virtualized environments being more efficient for cost and productivity. I think for a home server your better off having a high end pc and set up virtualization and install some distros. 

IBM use AIX 5.1 and 6.3 on their servers, again this is desirable in the UK for government working.

"dangertux" had a good idea of renting a VPS to play about with... however you can pick up an **old **server from ebay.. " rack mounted" for not a whole lot of cash.

let us know how you go about.

---

### Post by Grenage on 2012-03-28
Beyond a media server at home (which is really just a desktop), I've only implemented servers at work.  You can get some damn cheap HP/Whatever refurbs out there, but they are noisy as Hell*; I'd probably recommend going with something that is modern enough to use little power.

*Have not been, assumed much screaming.

---

### Post by knight2000 on 2012-03-28
First server was a 333mhz whitebox Viglen Desktop that could barely run windows. It hosted websites and a game server. That was about 10 years ago after getting kicked off my paid hosting. Host didn't like my perl scripts so I migrated to my own hardware and never looked back. Nowadays I work as the programmer at a medium sized businnes and we have  alot of servers doing different tasks. Most of the servers are part of a vmware infrastructure. Esxi is a great piece of Software to learn because it allows mulpile virtual appliances to be run off a single hardware server. The operating systems we use on our servers are Esx hosts with Windows, Ubuntu and Freebsd as the guests. We also have a few whitebox servers floating around for training purposes. I train my junior staff on those before introducing them to, mostly simple stuff like how to install a server securely, set up lampp properly and secure the shelll and shared resources etc. Once they understand those aspects we work on their server side programming abilities.

Knowing about servers is a really good skill in the IT industry because nearly all companies rely on their servers alot. Anyone can learn desktop admin but server admin is not as common. Add programming skills to those skills and you are on to a winner.

---

### Post by rk0r on 2012-03-28
> **knight2000 said:**
> First server was a 333mhz whitebox Viglen Desktop that could barely run windows. It hosted websites and a game server. That was about 10 years ago after getting kicked off my paid hosting. Host didn't like my perl scripts so I migrated to my own hardware and never looked back. Nowadays I work as the programmer at a medium sized businnes and we have  alot of servers doing different tasks. Most of the servers are part of a vmware infrastructure. Esxi is a great piece of Software to learn because it allows mulpile virtual appliances to be run off a single hardware server. The operating systems we use on our servers are Esx hosts with Windows, Ubuntu and Freebsd as the guests. We also have a few whitebox servers floating around for training purposes. I train my junior staff on those before introducing them to, mostly simple stuff like how to install a server securely, set up lampp properly and secure the shelll and shared resources etc. Once they understand those aspects we work on their server side programming abilities.

Knowing about servers is a really good skill in the IT industry because nearly all companies rely on their servers alot. Anyone can learn desktop admin but server admin is not as common. Add programming skills to those skills and you are on to a winner.



Not sure what you mean by "* Anyone can learn desktop admin but server admin is not as common"*  this statement is incorrect as anyone can learn anything given the right tutor.  I am sure you will upset a lot of " system admins" with a comment like that.

---

### Post by spynappels on 2012-03-28
I ran ESXi from a 4GB USB Stick on a HP ProLiant ML115 with 4GB RAM, an extra GbE NIC and 3 250GB SATA drives for VM storage.

Best learning experience ever.

I also have a Linode VPS now which is fantastic value for a root access Ubuntu 10.04 server.

---

### Post by CharlesA on 2012-03-28
> **Dangertux said:**
> You can do anything with a VPS you can do with a regular system (except virtualize, but...I think they may allow you to enable nested paging so that may even be possible). But you could set up HA, clustering, load balancing and anything else you wanted (though you might have to rent more than one VPS for those) 

My only word of  warning if you do that, don't cheat by using their "pre-made images" or "helper scripts" upload your own image and do it from scratch.

+1 to that. Using a VPS is a whole lot easier than actually getting server grade hardware and playing around with it.

> **knight2000 said:**
> 
Knowing about servers is a really good skill in the IT industry because nearly all companies rely on their servers alot. Anyone can learn desktop admin but server admin is not as common. Add programming skills to those skills and you are on to a winner.

Heh. Server admin is different from desktop admin. They are similar, but there are differences. Security plays a part on both desktops and servers, but I'd say securing desktops are more about training the people who use those machines and less about securing services that are running. It's not that hard to secure a service properly if you spend a ton of time reading about best practices and whatnot, but security is a process and is always changing. Knowledge is key.

> **rk0r said:**
> Not sure what you mean by "* Anyone can learn desktop admin but server admin is not as common"*  this statement is incorrect as anyone can learn anything given the right tutor.  I am sure you will upset a lot of " system admins" with a comment like that.

What they said ^.

---

