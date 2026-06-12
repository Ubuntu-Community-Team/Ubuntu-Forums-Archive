---
title: "Xeon and ECC RAM: worth it for LTSP?"
date: 2009-02-09
forum: Server Platforms
---

### Post by djsephiroth on 2009-02-09
I'm going to be putting together a server for an LTSP setup with 20-30 thin clients. We expect constant web browsing, some Flash (e.g., Youtube videos), a lot of office apps (e.g., OpenOffice), and at some point Wine serving Office 2007 and a couple of other Windows apps. The thin clients will only be used by students for classwork. OS will be 8.04 until Jaunty is tested and proven. 

I keep reading that Xeons are great for servers, but a) I can't seem to really find much in the way of *why* or *how*, and b) since this server will be serving standard desktop apps, as opposed to being a php/apache/mysql/etc. server, I'm curious as to whether or not the Xeon really fits the bill any better than a standard desktop CPU with the same specs (FSB, cache, clock, etc.). From what I can gather, the new Xeons are just Core2 Quads with more conservative voltage and clock multipliers. Given that assumption, plus the price difference between a Xeon and a regular desktop mobo, I'm leaning toward the Core2 Quad.

Is ECC essential? We're looking at either $150 for 8GB DDR3@1333Mhz or $260 for 8GB of DDR2@800Mhz. The motherboards that support ECC are also a bit high-priced, and there are much fewer options. Should we take the hit to speed and the higher price tag in order to counteract cosmic rays and any other gremlins assailing our RAM?  

PS: Apologies if this belongs in "hardware".

---

### Post by redroad55 on 2009-02-09
your biggest restriction is going to be bandwidth whether in your lan or your portal out .. sizing what you need will begin there .. 
For example a machine (server) built in 2004 with dual xeon 2.8 to 3.2 ghz. processors with 8 gb of ecc ram may be more than enough for your needs ..On the used market you could expect to pay anywhere from $300.00 to $700.00 for something like that , sometimes cheaper .. Just a thought .. Post back with any thoughts or questions .. Best to you

---

### Post by windependence on 2009-02-09
IMHO, ECC isn't worth the price unless you have a very high traffic  site or you are running a very CPU/RAM intensive application. I run servers with both and I have never had any problems with CRC memory errors. 

Xeons. Well, I'm an AMD man myself but I do run a few Xeon servers here and they are fine. Processing power is not usually an issue today if you run Unix. Memory is mor critical. Now, if you are unlucky enoughto run Windoze servers, especially in a virtualized environment, you'll need gobs of CPU for those hogs. I would still use server class hardware if you can instead of consumer hardware. 

-Tim

---

### Post by mpsii on 2009-02-09
First --
Xeon and Opteron processors are for server environments simply due to the level of L2 and L3 cache on the processors. They crunch the numbers that database and email servers like to throw at CPUs, typically better than desktop CPUs.

That said, an Intel Q6600 is a quad-core Intel Core 2 Quad processor. This is 4 CPUs that typically pairs with DDR2 RAM in anywhere from 1GB-16GB configurations.

Second --
ECC is not necessary for LTSP, unless your chosen system requires its use (the physical hardware). 

--------------------------------

The LTSP has some good information on the wiki about server sizing ([http://k12ltsp.org/mediawiki/index.php/Server_Sizing](http://k12ltsp.org/mediawiki/index.php/Server_Sizing)).

According to that guideline, your configuration would need:

RAM = 256MB + (50MB x 30 users) = 256MB + 1500MB = 1756MB for 30 simultaneous connections (all users at once)
Network = at least 100Mbit switches and cat5 cabling

CPU = 1 P3 1GHz can run 12 terminals comfortably = get a dual core AMD or Intel CPU at 2GHz speed (minimal)

I would suggest building or buying a system with:

Intel Core 2 Quad Q6600 or better
4GB DDR2 RAM or more
2 x 1TB SATA2 drives in RAID 1

---

### Post by djsephiroth on 2009-02-10
Thanks for all the responses!

> **redroad55 said:**
> your biggest restriction is going to be bandwidth whether in your lan or your portal out .. sizing what you need will begin there .. 

Definitely. We'll most likely be using a Cisco 10/100 Switch with 1000Mbps copper uplinks and the option for 1000Mbps fiber should we want it later on. Cat5e/6 for the copper, of course.
> **mpsii said:**
> 
The LTSP has some good information on the wiki about server sizing ([http://k12ltsp.org/mediawiki/index.php/Server_Sizing](http://k12ltsp.org/mediawiki/index.php/Server_Sizing)).

According to that guideline, your configuration would need:

RAM = 256MB + (50MB x 30 users) = 256MB + 1500MB = 1756MB for 30 simultaneous connections (all users at once)
Network = at least 100Mbit switches and cat5 cabling

Ehhh, their guidelines are more derived from art than science. I've been running various apps on different clients to get a more realistic idea of what we'd need. Each user could easily eat up 192MB or more running Firefox and watching Youtube videos, or just keeping a lot of random apps open. These are high school and middle school kids, so I expect Firefox windows galore, and we all know how that adds up.    
> 
CPU = 1 P3 1GHz can run 12 terminals comfortably = get a dual core AMD or Intel CPU at 2GHz speed (minimal)

I would suggest building or buying a system with:

Intel Core 2 Quad Q6600 or better
4GB DDR2 RAM or more
2 x 1TB SATA2 drives in RAID 1
A PIII could probably run twelve terminals comfortably assuming LOCAL_APPS is enabled and the terminals have decent local resources, assuming that no one is doing anything particularly demanding, e.g., clerical work. However, the Pentium D with 512MB DDR2 I'm using as a test system looks like it could be bogged down with half that many clients browsing the web. 

It's kind of moot, though, since this is my current proposed setup:

Core2Quad Q6600
8GB DDR3 @ 1333Mhz
RAID 5 (dedicated PCIE 8x card)
4x 1TB WD Caviar Black
2x 1Gbps Intel NICs (PCIE 1x cards)

I figure that ought to handle 20-30 clients with no speed issues. From what I've gathered and from what you've mentioned here, I think I'll stick with the Core2 instead of the Xeon. I'm still a bit undecided on the ECC/non-ECC issue, since I keep reading posts elsewhere in which people swear by ECC. Anyone ever experienced a problem when using non-ECC versus ECC?

---

### Post by mpsii on 2009-02-10
> I'm still a bit undecided on the ECC/non-ECC issue, since I keep reading posts elsewhere in which people swear by ECC. Anyone ever experienced a problem when using non-ECC versus ECC? 

ECC is not worth the extra coinage for your needs. Non-ECC is by far much more cheap and is just as capable.

ECC RAM is primarily used in an environment where bad hardware cannot be tolerated. In a typical 24x7 server shop, where an outage of 30 minutes equals $3 million, you want ECC in your servers (along with hardware SCSI RAID 10, redundant power supplies, multiple CPUs, multiple servers). In your case, the price does not seem to justify the need. If a stick of your RAM goes bad, you can replace it the next day after a trip to Best Buy or your local computer shop. ECC RAM is much harder to find locally, unless it is part of your Dell/Compaq/IBM service contract.

---

### Post by windependence on 2009-02-11
> **djsephiroth said:**
> Thanks for all the responses!

Ehhh, their guidelines are more derived from art than science. I've been running various apps on different clients to get a more realistic idea of what we'd need. Each user could easily eat up 192MB or more running Firefox and watching Youtube videos, or just keeping a lot of random apps open. These are high school and middle school kids, so I expect Firefox windows galore, and we all know how that adds up.    



Remember, this depends on whether your graphics are rendered in the server or on the client. I am inclined to think it would make a better user experience on the client.

-Tim

---

### Post by djsephiroth on 2009-02-11
> **windependence said:**
> Remember, this depends on whether your graphics are rendered in the server or on the client. I am inclined to think it would make a better user experience on the client.

-Tim
Naturally. I mean, all the client does is render graphics, afaik.

---

