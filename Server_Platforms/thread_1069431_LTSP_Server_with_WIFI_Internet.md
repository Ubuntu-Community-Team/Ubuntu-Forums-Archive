---
title: "LTSP Server with WIFI Internet"
date: 2009-02-14
forum: Server Platforms
---

### Post by haddog on 2009-02-14
I am running an Ubuntu 8.04.2 LTS LTSP server. Thin clients connect to the LTSP server through a switch using DHCP.

Is it possible to provide internet access to the thin clients via a wifi connection on the LTSP server?

Have had no luck with this config on the LTSP server yet. I am able to provide internet access to the thin clients with a hardwired/NIC connection on the LTSP server.

---

### Post by lykwydchykyn on 2009-02-14
In a default LTSP setup, the clients log in to the server where the desktop and applications are actually running.  So if the server is setup to access the internet, the clients will also have access.

Are you talking about booting a thin client across WIFI?  Or just uplinking the server via WIFI?

---

### Post by haddog on 2009-02-14
Thanks for respondidng lyk. No, not trying to boot clients across wifi, even though that does seem like something fun to try. Any good tutorials you know of regarding etherbooting on wifi cards to an LTSP server? 

Regarding wifi on the LTSP server, maybe I just need to tinker around with my wifi card. Looks like I don't actually have it up and running. I thought it should be 'that simple' as once the server has wifi access, the clients should to. 

BTW. What flavor/version of Ubuntu you running?

---

### Post by haddog on 2009-02-14
Lyk. I see the flavor of Ubuntu you run. Kubuntu 8.10. Right there where your name is listed. You use an LTSP server? I'm doing some voluteer work for a my church. Not really work, I just wanted to try it! Going to setup up a computer lab.

So far I have 3 thin clients with various hardware connecting to an Ubuntu LTSP server through a 5 port linksys swithch in my garage. Two of the thin clients have PXE capable nic cards, the other 2 I use a thinstation bootable floppy or CD to load a small image that allows the non PXE netgear FA311 nic cards to locate and boot off the LTSP server. 

The server has two 3com 905 nics, one connected to the switch, the other to an airlink 101 router that supplies the internet connection. The thin clients and the server all share a keyboard/mouse/monitor via a 4 port belkin KVM switch.

There is a cool surplus store out here in northern Cali. Located in silicon valley. Called Weird Stuff. Great prices. Thinking of using the following for thin clients. What do ya think?

[http://www.weirdstuff.com/cgi-bin/item/63001](http://www.weirdstuff.com/cgi-bin/item/63001)  

These should be great for thin clients I would think.

---

### Post by lykwydchykyn on 2009-02-14
> **haddog said:**
> Lyk. I see the flavor of Ubuntu you run. Kubuntu 8.10. Right there where your name is listed. You use an LTSP server? I'm doing some voluteer work for a my church. Not really work, I just wanted to try it! Going to setup up a computer lab.


I run Kubuntu on my desktops and laptop; I set up an LTSP a few years ago on Dapper at our public library to dish out a kiosk setup to thin clients throughout the building (card catalog terminals).  I've tinkered around with LTSP a lot since then, it's a cool technology that I wish I could find more real world applications for. Once all my kids are of computing age, I might have to set one up at home!

> 
 Thinking of using the following for thin clients. What do ya think?

[http://www.weirdstuff.com/cgi-bin/item/63001](http://www.weirdstuff.com/cgi-bin/item/63001)  

These should be great for thin clients I would think.

Oh yeah, those would work fine.  I've never tried doing any kind of demanding video stuff over LTSP, so I don't know what you'd need if you wanted to do that, but for most other purposes those specs are good.  My thin clients at the library are tiny little geode-based boxes, like 200Mhz things with 64 MB of RAM.  But they do fine, since most of the actual processing is done on the server.

---

### Post by haddog on 2009-02-14
Picked up three of these. Just got 'em all logged in and booted on the LTSP server. They even have intergrated 3com nic with MBA/PXE functionality! Probably won't do any heavy video. I'll look for some 64 MB pci video cards next time. Most likely I'll add the Edubuntu distro packages. 

Got a SATA 250GB drive for $30. Need more hard drive space on the server. Only a 40GB drive in there now. Probably just clone the 40GB to the 250 GB drive. You had any luck cloning a drive linux drive? Not sure if Norton Ghost will do the trick. I'm sure there is a Linux/Open source solution.

I picked up a 16 port rack mount switch for $10 bucks too. That place is awesome. Now i'll start messin' around with the wifi connection on the LTSP server. Have a good evening, thnx for the conversation!

---

### Post by hvc123 on 2009-02-15
i dont think you can pxe boot with wifi

---

### Post by haddog on 2009-02-15
Yes you can pxe boot with wifi. Here's a how to article in Linux Journal from May 2008 called "Thin Clients Booting over a Wireless Bridge."

[http://www.linuxjournal.com/article/9850](http://www.linuxjournal.com/article/9850)

---

