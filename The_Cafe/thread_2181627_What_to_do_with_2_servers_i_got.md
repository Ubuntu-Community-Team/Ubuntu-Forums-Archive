---
title: "What to do with 2 servers i got"
date: 2013-10-18
forum: The Cafe
---

### Post by ads2996 on 2013-10-18
Hi,

I just got my hands on 2 rack mount servers. I plan to set them up as network storage for my current "home" server which server up media files and the such, (which i have to fix as it doesn't want to boot now :( so i was wondering if there is any good uses i could do with two servers i have.

Once i get them all sorted they will have 32gb of ram, 2 i think dual cores (could be quad) at about 2.3ghz and about 100gb of storage to donate to other than storing my media files.

My initial thoughts were running multiple web servers and lease them out to people. I also though about running game servers such a minecraft probably tekkit or a source engine server like cs or tf2 or some other games.

If you need any info just ask

Thanks in advance

---

### Post by ads2996 on 2013-10-18
This may be of help
[http://www.speedtest.net/my-result/3042156906](http://www.speedtest.net/my-result/3042156906)

---

### Post by eriktheblu on 2013-10-18
With that kind of bandwidth, the functions will probably be for personal use only.

Game server would be fine over a home network, but not over the Internet.

---

### Post by ads2996 on 2013-10-18
I'm new to enterprise servers so i dont know what u mean by bandwith

---

### Post by sandyd on 2013-10-18
> **eriktheblu said:**
> With that kind of bandwidth, the functions will probably be for personal use only.

Game server would be fine over a home network, but not over the Internet.
+1

> **ads2996 said:**
> I'm new to enterprise servers so i dont know what u mean by bandwith
Internet speed - shows you only have 1M dow and 0.37M up

Generally for internet servers, it is the upload speed that is more important - with 0.37M there are not a lot of things you can do.

---

### Post by ads2996 on 2013-10-18
I used to run a tekkit server off a laptop with those speeds and it seemed fine with those speeds. My main probelm was just my crappy laptop i think

---

### Post by ads2996 on 2013-10-18
[http://h20565.www2.hp.com/portal/site/hpsc/template.PAGE/public/kb/docDisplay/?sp4ts.oid=3219233&spf_p.tpst=kbDocDisplay&spf_p.prp_kbDocDisplay=wsrp-navigationalState%3DdocId%253Demr_na-c00778015-21%257CdocLocale%253D%257CcalledBy%253D&javax.portlet.begCacheTok=com.vignette.cachetoken&javax.portlet.endCacheTok=com.vignette.cachetoken](http://h20565.www2.hp.com/portal/site/hpsc/template.PAGE/public/kb/docDisplay/?sp4ts.oid=3219233&spf_p.tpst=kbDocDisplay&spf_p.prp_kbDocDisplay=wsrp-navigationalState%3DdocId%253Demr_na-c00778015-21%257CdocLocale%253D%257CcalledBy%253D&javax.portlet.begCacheTok=com.vignette.cachetoken&javax.portlet.endCacheTok=com.vignette.cachetoken)

this is the server, im not sure which porcessor, but i plan to install 32gb of ram in each

---

### Post by tgalati4 on 2013-10-18
Be sure to clean them out and reseat everything.  It's also a good idea to replace the paste with a quality ceramic or silver paste under the heat sinks.  The power supplies tend to blow on older servers (bad capacitors), so it's usually wise to replace them or keep a back up handy.  If your servers have double power supplies, pull one and keep it as a spare.  No need to burn extra watts.  You will find that these older servers will burn some power (200-300 watts) depending on how heavily populated.  Running them 24/7 will cost you.  You might want to measure the wattage with a kill-a-watt meter.  Quite a lot compared to 5 watts for a RaspberryPi.

I use one of my PowerEdge 1750 servers as a web/drupal server and the other as a development machine.  It sleeps and I use wake-on-lan when I need to do some hacking.  Each machine runs 218 watts at idle and 260 watts when 4 cores are jamming.  I've only got 8 GB in each.

Proliants are decent machines.  You should get several more years out of them.

---

### Post by ads2996 on 2013-10-19
they both have 2 875W power supplies, i do plan on getting a kill-a-watt, its just trying to find a reliable one that work with UK plugs, so i don't get false readings. The drives that are in them were just pulled fro other servers so that it had max storage. So everything will need to be formatted and re installed. I cant decide between Ubuntu server or a windows server probably 2012, i would like windows server, because then i could run a team foundation server, as well as to render videos from after effects. On ebay i have looked at 300W power supplies but i have no idea how much power these machines actually need.

What do u mean by a development server? Thanks for replying

---

### Post by tgalati4 on 2013-10-19
If you have Drupal7 running your website and then Drupal8 comes out, how do you test it?  Having a second machine allows you to migrate your website and test it before going live.  Of course you can set up virtual machines and do the same if you only have one physical server.  Or you can set up one with Windows Server and the other with Ubuntu/linux server, or you can play with Xen and set one with several virtual machines and leave the other as bare metal so you can play with cloud services.

When you measure the power consumption and cost of that power, you will start looking at low-power servers.

---

### Post by cptrohn on 2013-10-19
Sounds like one would make a nice FreeNAS.

---

### Post by QDR06VV9 on 2013-10-19
> **tgalati4 said:**
> 
When you measure the power consumption and cost of that power, you will start looking at low-power servers.

+1

---

### Post by ads2996 on 2013-10-20
They will be primarily used as NAS for my media files, but i will probably reserve about 140gb for the os and for me to muck about maybe even a dual boot of two oses or something like that.
Does anyone know of a reliable brand for a UK power meter.

---

### Post by tgalati4 on 2013-10-20
You can make your own.  You need two meters:  A current loop meter and a standard AC voltmeter.  Strip open one of the EIC power cables and pull the hot lead free so you can get your clamp meter around it--don't cut it and be careful not to damage the insulation around the wire.  Plug one meter into the wall outlet to read AC voltage, plug the EIC cable with your amp meter clamped around the hot lead into the same wall outlet and into the server.  Read both amperage and voltage at the same time and make a log:

**Computer Activity   Voltage  Amps Power (V*A)**

Idle     231.0   0.8  184.8 watts
burnP6 (x4)  229.0  1.2  274.8 watts

Most of the newer, server power supplies have 98% Power Factor so your V*A power (called Apparent Power) will be close to PF*V*A (Utility or Resistive Power)--or what you get charged for.

Take readings with one and two power supplies to see if the second power supply consumes more than 10 watts.  If so, then you will want to pull it and just keep it as a spare on the shelf than just burning power.

Here's a nice clamp meter for $55US, but you can find cheaper ones for ~$10:  [http://www.extech.com/instruments/product.asp?catid=27&prodid=101](http://www.extech.com/instruments/product.asp?catid=27&prodid=101)

You can use the same meter to make both measurements, but I find it easier and safer to have two meters.  Besides, you can't have too many meters.

If  you don't want to buy any meters, then you can simply use your house electric meter and turn off everything and just measure the server over an hour of use then subtract the two readings--that will give you a direct kilowatt-hour reading.

---

### Post by ads2996 on 2013-10-21
I may be getting my hands on two more servers so power consumption will be a definite factor.

---

### Post by Roasted on 2013-10-21
I have a desktop server I built at home running 4GB of RAM with an i3 processor and 2x3TB RAID 1 WD Reds. I run the following services and rely on all of them heavily:

Video Surveillance via "Motion" (in repos)
ownCloud - Personal Cloud
Web - Apache
File Services - Samba
Streaming Local Content To HTPC - Samba
System Backups - SSH and Samba, depending on what I'm doing

---

### Post by mayagrafix on 2013-10-21
If u are really feeling adventurous why not try Cluster computing?

[https://computing.llnl.gov/tutorials/linux_clusters/](https://computing.llnl.gov/tutorials/linux_clusters/)

---

### Post by ads2996 on 2013-10-22
Clusters sound pretty cool, but for me i don't really see much use for them, unless there are any cool uses i am missing. I just got my hands on a hp bladesystem with 2 server blades in them, i was wondering if there was any way to mount 3.5" drives inside the enclosure.

---

### Post by david98 on 2013-10-22
I would not trust the reliability of that speed test i took it and result's where 2.7 download and 0.96 upload which is incorrect because am getting 8.6 download and 2.1 upload try a different speed test like this one [http://www.uswitch.com/broadband/speedtest/?gclid=CIWp-LvGq7oCFbIPtAodW1IA9w](http://www.uswitch.com/broadband/speedtest/?gclid=CIWp-LvGq7oCFbIPtAodW1IA9w)

---

### Post by mayagrafix on 2013-10-23
> **ads2996 said:**
> Clusters sound pretty cool, but for me i don't really see much use for them, unless there are any cool uses i am missing. I just got my hands on a hp bladesystem with 2 server blades in them

Plus 2 more thats 4 servers... and used as servers u might end up spending 500 or more per month in electricity. If u want servers that much, better of getting one from Synology DS412 (for 600 dlls) which uses the equivalent of a 40 watt bulb per month and does a lot more that ur present hardware. But give me four servers in a cluster and I'll calculate when the next meteor will hit the earth... maybe.

---

### Post by ads2996 on 2013-10-23
Im currently having a probelm with my one of my blades, as they dont have much storage so i will probably use them to host game servers and the other servers for data storage, i may even pull the ram from the "broken" one and have 8gb in total.
For running a game server which would be better
1. 32gb ram 2 2.6ghz dual core
2. 8gb ram 2 2.6ghz quad core (may be higher clock not sure)

---

### Post by Old_Grey_Wolf on 2013-10-23
If those are going to be home servers, I noticed those ProLiant servers have iLO; therefore, you can turn them on and off remotely when not in use to save on power.

---

### Post by ads2996 on 2013-10-23
ilo will be very handy to control power, i just need to pick a suitable os for the servers.

---

### Post by Old_Grey_Wolf on 2013-10-23
The 2 dual-core and 2 quad-core, you may what to consider [Ubuntu OpenStack]("http://www.ubuntu.com/cloud") if you can get more RAM. Then run whatever OS you need for each of the Virtual Machines on the servers.

---

### Post by ads2996 on 2013-10-23
i think that my broken blade is unrecoverable so im juts gonna use it for spare parts, so ill have 2 quad cores at 2.6ghz with 8gb ram

---

### Post by mayagrafix on 2013-11-02
Heres a vid that might interest u
[http://www.youtube.com/watch?v=s5KG18M5U7o](http://www.youtube.com/watch?v=s5KG18M5U7o)

---

