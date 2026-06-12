---
title: "Do you use dd-wrt or OpenWrt on your router? Tell us about it!"
date: 2007-10-06
forum: The Cafe
---

### Post by kentl on 2007-10-06
The title pretty much sums it up!

My personal interest is that I have a Linksys WRT54GL V1.1 which I plan to install either dd-wrt or OpenWrt on. For me it's not simply a case of wanting to run Linux on the router. By default the router has support for DDNS through DynDNS. But I want to use it with my provider, which is compatible with the DynDNS service but has their own servers. There is no option to change that by default, which is why I hope either one of these can help me out.

Tell us about what problems you have faced, if it was difficult to install, what you use it for. There's at least one person who's interested in reading everything you have to say about these two software replacements.

Thanks for reading, I hope you have somthing to share with us!

---

### Post by n3tfury on 2007-10-06
i have the linksys wrt54gl flashed w/ DDWRT v24 Beta std. and use it for everyday wireless and QOS although i've setup radius and chilispot (hotspot) also.  

it's so great i even contributed money to the project.

---

### Post by D-EJ915 on 2007-10-06
I have dd-wrt on my linksys and buffalo running WDS and it works really really well.  I think the buffalo is better, it responds faster through the interface and has a huge range.

It works great for me, I've never used any of the standard features and I have mini on the linksys.

---

### Post by Hortinstein on 2007-10-06
hmmm thats pretty cool...i am planning on flashing my router when I get a chance...QOS will really help when i have all my torrents running

---

### Post by Nessa on 2007-10-07
I suggest that you use it after the router's warranty expires so you don't lose the option of getting a replacement if it conks out. Unless you're rich then you can just buy another one.

Does it really improve the router's performance? I went to the dd-wrt site. Is there a difference between the paid and the free version?

---

### Post by Frak on 2007-10-07
DD-WRT with OpenDNS

---

### Post by n3tfury on 2007-10-07
> **Nessa said:**
> I suggest that you use it after the router's warranty expires so you don't lose the option of getting a replacement if it conks out. Unless you're rich then you can just buy another one.



you have to be halfway short of knucklheadedness to brick your router.  follow the instructions and there's such a small chance that you'll run into problems that it's not worth thinking about.  i flashed mine straight away, since that's the reason i bought it.

---

### Post by bionnaki on 2007-10-07
I use thibor 15c with my wrt54g and highly recommend it: [http://www.thibor.co.uk/](http://www.thibor.co.uk/)

---

### Post by ssam on 2007-10-07
i have recenlty put openwrt Whiterussian 0.9  on a WRTSL54GS.

installation was very simple. i guess things can go wrong, but if you read the instructions it should be ok.

I recommend that you know the basics of networking, ssh, linux command line etc before starting. read through the wiki, if it all sounds like giberish then its probably not for you. also have a backup network connection.

if you get to a point where you need to use tftp firmware uploads then you will need to know how to set up static addresses on you computer (you may need to disable network manager).

I have added the webif2 package from [http://x-wrt.org/](http://x-wrt.org/) and shorewall.

my task for today is to learn how to set up a VPN so that i can have a open hotspot with restricted net access, but let my laptop use the ful connection. [http://wiki.openwrt.org/HotspotOpenvpnHowto](http://wiki.openwrt.org/HotspotOpenvpnHowto) has most of what i want. (if anyone has any hints let me know)

---

### Post by kentl on 2007-10-08
What's your argument for running dd-wrt or OpenWrt? It seems like OpenWrt would be more powerful as you don't have to have the web files on the router, you get space for something else. Or?

Can you:
[LIST=1]
[*]Use DynDNS with any server of your choice (which supports DynDNS)
[*]Check if a LAN server is responding to ping. And if it doesn't intercept web traffic with a page like "The Server Is Current Under Maintenence, Come back tomorrow"
[/LIST]
From either one?

---

### Post by kentl on 2007-10-08
And a third question. If I install dd-wrt, can I switch back to my original software if I'm not satisfied? Is it the same with OpenWrt? I would think that you can, but it's better to be safe than sorry. :-)

---

### Post by jrusso2 on 2007-10-08
I have a WRT54G v6 that someone gave me and I installed DD=WRT on it but I can't recommend it for that version as it really does not have enough memory to run it properly.

---

### Post by kevdog on 2007-10-09
Using wrt54gl with dd-wrt prerc4 (which I think is the latest beta), using it actually in repeater/bridge mode to repeat the signal from upstairs router.

Contrary to others - I did brick my router on the first try (have to install mini version first, and then can upgrade to any other version after that). With some searching however it was able to be recovered so it wasnt that big of deal. 

Im not sure if you can go back to the stock firmware.  Possibly the linksys site might give you a hint on this --- Why would you want to however??

For Dynamic DNS the version Im running has auto configuration for 7 providers and allows for a Custom option for updating.  I use noip.com and this is in the default list, so I didnt do any customizing, however it looks straightforward to me.

From looking at all the menus, I dont think it can ping a LAN machine and then post a message that its down.  You could possibly set up a cron job to do this, however Im not exactly sure how you would do this.  This question might be better posed in the dd-wrt forum

---

### Post by Dimitriid on 2007-10-09
I have plenty of "Busted" routers way out of warranty, didn't know I could flash em to linux, although they are Netgear and Berklin ( both wireless and both complete BS for reliability btw. ) Where can I look like all the models I could flash?

---

### Post by imagine on 2007-10-09
> **Dimitriid said:**
> I have plenty of "Busted" routers way out of warranty, didn't know I could flash em to linux, although they are Netgear and Berklin ( both wireless and both complete BS for reliability btw. ) Where can I look like all the models I could flash?
You can flash all routers with an open firmware. Of course if you don't want to hack firmwares yourself, you want a router that already got a big community.


The firmware I use on my WRT54GL is Tomato: [http://www.polarcloud.com/tomato](http://www.polarcloud.com/tomato). It has a noob-friendly web-interface, very detailed QoS-settings, nice graphs and statistics ([screenshot](http://www.polarcloud.com/img/ssbwm100.png)) and you can change the settings without rebooting the router.
It also supports the Buffalo WHR-G54S, WHR-HP-G54, WZR-G54, WBR2-G54 and the Asus WL500G Premium. Other firmware like HyperWRT, OpenWrt or DD-WRT may also support other devices.

For a general but of course uncompleted overview of devices that run Linux you can have a look here: [http://www.linuxdevices.com](http://www.linuxdevices.com). For example another very big project is the NSLU2, on which can put Debian.

---

### Post by n3tfury on 2007-10-09
> **imagine said:**
> You can flash all routers with an open firmware. 

i've previously looked for firmware for a DLink DI-524 and couldn't find any.  any open source firmware that you know of that supports this model?

---

### Post by Hallvor on 2007-10-09
> **jrusso2 said:**
> I have a WRT54G v6 that someone gave me and I installed DD=WRT on it but I can't recommend it for that version as it really does not have enough memory to run it properly.

I have a WRT54GS v5, but it has the same amount of memory. Mine works very well using the micro version. However, it is very important to flush the memory by resetting your router with the reset button (not just powercycle it) before upgrading the firmware. Forgot to do that once, and performance was not very good afterwards.

---

### Post by daynah on 2007-10-16
Randomly, the internet stopped working and it was obvious it was on our end. As a last ditch effort, I installed dd-wrt... lite? whatever the small one is before you install the real version. It worked. In fact, it allowed me to ssh which is something Comcast said that I wasn't able to do on my plan (though I had tried!!). Anyway, I tried then to go to the real version and... it wouldn't work. It just kept stalling. Nothing broke though. So... if it ain't broke don't fix it.

I haven't done anything advanced with it, because if I'm going to figure out how to upgrade I'll lose the settings...

Oh, I have some sort of wireless enabled linksys that's supposed to be fully supported.

---

### Post by asimon on 2007-10-17
My Buffalo WHR-HP-G54 router at home also runs Linux. After trying out dd-wrt, open-wrt, and x-wrt I settled with the [Tomato firmware]("http://www.polarcloud.com/tomato"). It's not the most powerful but nice and rock-stable and has everything I need. Especially I like it's nice and easy to use web interface, which is IMO the best of the mentioned firmwares.

It works on the typical Linksys routers too and also support many DDNS protocols including the possibility of using custom URLs.

Flashing the firmware was a little bit complicated (well it was easy, but not as easy as pressing a single button) because the "update" feature from the original Buffalo firmware only accepts crypted/signed firmwares, so I had to use tftp from the commandline during a 5 seconds window when the router boots to bring the goodness to the router.

I never saw the original Buffalo firmware, flashing was the first thing I did.  :-)

---

### Post by kentl on 2007-10-17
I installed dd-wrt and it seems great. When I look at Tomato I see one feature I would like to have. It seems like dd-wrt only can handle one dyndns-provider, while Tomato can handle two. That would fit me better as I need dyndns functionality from both DynDns.org and my domain name provider (as I run my own web server with my home page).

Any ideas on how to get this to work using dd-wrt? Should I be "afraid" of switching to Tomato? It seems a bit less popular, but I might be wrong. ;-)

---

### Post by jrusso2 on 2007-10-18
> **Hallvor said:**
> I have a WRT54GS v5, but it has the same amount of memory. Mine works very well using the micro version. However, it is very important to flush the memory by resetting your router with the reset button (not just powercycle it) before upgrading the firmware. Forgot to do that once, and performance was not very good afterwards.

I used the miro version but when I look in the statistics I see the router is using 90% of the memory just running.

---

### Post by Hallvor on 2007-10-18
> **jrusso2 said:**
> I used the miro version but when I look in the statistics I see the router of that brand with dd-wrt is using 90% of the memory just running.

Those routers are stripped of ram to begin with, but I can`t tell how much ram a router of that brand with dd-wrt normally uses since I am not at home. But did you do a hard reset (push and hold the button on the back for 30 seconds) before upgrading the firmware? It is important to flush the router memory before upgrading.

Anyway, I use the router a lot for heavy p2p usage, both aMule and Bittorrent. It is a *lot* better than the original firmware and haven`t given me any problems so far.

---

### Post by LoneShadow on 2007-10-18
If your requirements are simple, you can use any of the custom firmwares.

I personally prefer open-wrt since its very robust, very flexible, has tons of features. With X-Wrt out, I am sure its one of the best. This helps for people with less experience with iptables, FAQs, Wikis ... :)

I use Asterisk, QoS, NFS service, and run a bunch of custom scripts on my router, Openwrt fits perfectly these requirements.

- LS

---

### Post by Ubunted on 2007-10-18
I have a WRT54GL 1.1 with the latest DD-WRT version and compared to other routers and even the stock firmware it has been solid as a rock, absolutely NO issues and measures uptime in weeks instead of hours like my last D-Link. Only time it goes out is when it loses power, be it during a commercial outage or me messing with my cabling again.

Lots more options too that I like like AP Isolation etc.

Best router/firmware ever.

---

### Post by asimon on 2007-10-18
> **kentl said:**
> Any ideas on how to get this to work using dd-wrt? 
Looks like it's possible with dd-wrt too: [Multiple DDNS Accounts HOWTO](http://www.dd-wrt.com/wiki/index.php/DDNS_-_How_to_manage_multiple_DDNS_accounts_using_embedded_inadyn_-_HOWTO)

> **kentl said:**
> 
Should I be "afraid" of switching to Tomato? It seems a bit less popular, but I might be wrong. ;-)
If you want, just test it and switch back if it doesn't suit you. There is no harm in trying different firmwares. Maybe it's a good idea to first save your current config before trying something new so you can switch back without configuring everything again.

Regarding popularity, at the [linksys.org forum](http://www.linksysinfo.org/forums/forumdisplay.php?f=116) the 3 most active subforums are dd-wrt, hyper-wrt, and tomato. Whatever that means.

---

### Post by asimon on 2007-10-18
> **LoneShadow said:**
> With X-Wrt out, I am sure its one of the best. 
Just be aware that X-Wrt's support for the current "kamikaze" version of open-wrt is still incomplete, see [Kamikaze - X-Wrt](http://wiki.x-wrt.org/index.php/Kamikaze). I think the X-Wrt support for older "white russian" is more feature complete (I only tested x-wrt with kamikaze).

---

### Post by kentl on 2007-10-18
> Looks like it's possible with dd-wrt too: Multiple DDNS Accounts HOWTO
Thanks! I'll stick with dd-wrt until it can't fulfill my feature requests and something else can. I had a little bit of problem upgrading the firmware to dd-wrt (my own fault though, I missed that note and did use firefox and was unable to use the web interface. A push reset for 30 sec and unplog the power cord and so on solved it) which made me a bit off on trying it often. :)

---

### Post by wieman01 on 2007-10-18
The reason why I went for DD-WRT is that **Quality of Service** (QoS) is really superior to all other pieces of firmware I have seen so far. It just works, no matter what kind of service you use (e.g. Skype, HTTP, streaming, etc.). 

Also **static DHCP** (based on MAC address) is worth mentioning.

---

### Post by kentl on 2007-10-18
wieman01: A quick question from someone who doesn't know much about QoS. Do you have to configure anything on the clients in order for it to work?

An example would be that I want http traffic to my web server to have a higher priority than BitTorrent downloads and FTP upload/downloads. Is that sort of stuff hard to get working?

---

### Post by wieman01 on 2007-10-18
> **kentl said:**
> wieman01: A quick question from someone who doesn't know much about QoS. Do you have to configure anything on the clients in order for it to work?

An example would be that I want http traffic to my web server to have a higher priority than BitTorrent downloads and FTP upload/downloads. Is that sort of stuff hard to get working?
No, there is no configuration needed on the clients. Configuring QoS via the DD-WRT web interface is a piece of cake. Simply select HTTP and assign "Premium" for instance and then "BitTorrent" = "Bulk"; and you are ready to go. It is as simple as that. And as I said it just works. I was really impressed.

I use Skype a lot so assigning a higher priority to VOIP was crucial.

---

### Post by asimon on 2007-10-18
> **wieman01 said:**
> The reason why I went for DD-WRT is that **Quality of Service** (QoS) is really superior to all other pieces of firmware I have seen so far. It just works, no matter what kind of service you use (e.g. Skype, HTTP, streaming, etc.). 

Yes, QoS is very convenient. My up- and downstream bandwidths are both currently saturated because of downloading/seeding the new Kubuntu release but browsing the web or doing stuff via ssh are still very responsive.

Under Tomato QoS looks like this:
* [Screenshot: QOS Classification](http://www.polarcloud.com/img/ssqosc108.png)
* [Screenshot: QOS Graphs](http://www.polarcloud.com/img/ssqosg108.png)

> **wieman01 said:**
> Also **static DHCP** (based on MAC address) is worth mentioning.
I think it's a standard feature which all mentioned firmwares support.

BTW, the english DD-WRT entry in Wikipedia contains some ugly accusations against the project (which are disputed).

---

### Post by wieman01 on 2007-10-18
> **asimon said:**
> I think it's a standard feature which all mentioned firmwares support.
Static DHCP... I did not know that. The previous version of my firmware (Linksys proprietary firmware) did not, so I thought not all do. Nevertheless it is quite convenient as well.

---

### Post by wieman01 on 2007-10-18
By the way... you need to know your **maximum upload & download rate** for QoS to work... there are tools on line that help you determine your bandwidth. That's the greatest stumbling block though. The rest is easy.

---

### Post by jrusso2 on 2007-10-18
> **Hallvor said:**
> Those routers are stripped of ram to begin with, but I can`t tell how much ram a router of that brand with dd-wrt normally uses since I am not at home. But did you do a hard reset (push and hold the button on the back for 30 seconds) before upgrading the firmware? It is important to flush the router memory before upgrading.

Anyway, I use the router a lot for heavy p2p usage, both aMule and Bittorrent. It is a *lot* better than the original firmware and haven`t given me any problems so far.

I don't really recall, I am pretty sure I did do a hard reset.

---

### Post by Hallvor on 2007-10-18
> **jrusso2 said:**
> I don't really recall, I am pretty sure I did do a hard reset.

Back home. Here are my stats:

System
Router Name
DD-WRT
Router Model
Linksys WRT54G/GL/GS
Firmware Version
DD-WRT v23 SP3 (07/21/07) micro - build 7509
 
WAN Domain Name
 
LAN Domain Name
 
Current Time
Thu, 18 Oct 2007 18:04:49 
Uptime
3 days, 23:23

Memory
Total Available
88%
14344 kB / 16384 kB 
Free
29%
4092 kB / 14344 kB 
Used
71%
10252 kB / 14344 kB 
Buffers
9%
968 kB / 10252 kB 
Cached
31%
3152 kB / 10252 kB 
Active
24%
2496 kB / 10252 kB 
Inactive
16%
1648 kB / 10252 kB


Network
IP Filter Maximum Ports
4096 
Active IP Connections
7%
288  

90% used memory is *not *normal.

---

### Post by asimon on 2007-10-18
> **Hallvor said:**
> 
90% used memory is *not *normal.
My WHR-HP-G54 with Tomato usually also has around 90% used memory. Sometimes it goes down a little bit to 82-85%, but most of the time it's around 90%.

```
Tomato v1.10.1188


BusyBox v1.2.2 (2007.10.07-17:18+0000) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

# free
              total         used         free       shared      buffers
  Mem:        14540        13212         1328            0         1352
 Swap:            0            0            0
Total:        14540        13212         1328

```

---

### Post by theacoustician on 2007-10-18
I use DD-WRT .23 standard on my router.  I've tried upgrading several times to one of the SP's or to .24, but it simply doesn't work with Bellsouth (now AT&T) DSL.  Love it otherwise.

---

### Post by Frak on 2007-10-18
> **theacoustician said:**
> I use DD-WRT .23 standard on my router.  I've tried upgrading several times to one of the SP's or to .24, but it simply doesn't work with Bellsouth (now AT&T) DSL.  Love it otherwise.
Good, I'm not the only one who despises SBC/AT&T.

---

### Post by tlg on 2007-10-20
I have DD-WRT V23 SP2 installed on several Linksys WRT54GL and ASUS WL-500gP routers which work fine with Ubuntu 7.04, Mac and Windows clients running WPA PSK security.

However I have one installation which has three of the Linksys devices running WDS (with WPA  PSK) to give coverage over a large area.

The Mac and Windows devices work OK but I have tried two laptops (Dell 640m and an Acer with Intel wireless chipsets) which run Ubuntu and while they can see the wireless network OK, and seem to connect, the connection is not stable. 

I have tried Network Manager and WICD and both give the same result, leading me to the conclusion that the problem is somewhat deeper in Ubuntu.

Has anyone else any experience with using DD-WRT or Open WRT with WDS and Ubuntu, successfully or otherwise?

Thanks

---

### Post by wieman01 on 2007-10-20
> **tlg said:**
> I have DD-WRTV24 SP2 installed on several Linksys WRT54GL and ASUS WL-500gP routers which work fine with Ubuntu 7.04, Mac and Windows clients running WPA PSK security.

However I have one installation which has three of the Linksys devices running WDS (with WPA  PSK) to give coverage over a large area.

The Mac and Windows devices work OK but I have tried two laptops (Dell 640m and an Acer with Intel wireless chipsets) which run Ubuntu and while they can see the wireless network OK, and seem to connect, the connection is not stable. 

I have tried Network Manager and WICD and both give the same result, leading me to the conclusion that the problem is somewhat deeper in Ubuntu.

Has anyone else any experience with using DD-WRT or Open WRT with WDS and Ubuntu, successfully or otherwise?

Thanks
That could relate to a driver issue depending on the hardware you have got. Have you tried playing around with the physical settings of your wireless network (router settings e.g. bacon interval with a lower value)? And what happens if you move closer to the router?

---

### Post by tlg on 2007-10-20
The laptop wireless chipsets are Intel Pro/Wireless 3945ABG

I haven't modified any settings as I don't want to disturb the running setup as there are users working off it.

I will set up a test network and replicate the problem when I get a chance.

The WDS has been running for months with Macs and Windows clients, and it was only recently that we introduced another laptop that was the first machine running Ubuntu that we got a nasty surprise when it would not work. The connection is so unstable as to be unusable.

I am interested to see if any one else has the same set up running successfully before I beat my head against the wall for too long.

---

### Post by roachk71 on 2007-10-21
My WRT54Gv2 used to run DD-WRT v23 Standard, but I found it used too much memory (it would often stall during trash collection, and our internet access would suffer.)

I just flashed the latest release of Tomato, and everything we need works much better; I'd highly recommend this firmware. :KS

---

### Post by tlg on 2007-10-25
Further to my post above about DD-WRT in WDS mode, I have set up a test network and reproduced the problem.

However what I have discovered is that it fails for my two laptops with Intel 3945ABG chipset ( Acer and Dell 640m), but works fine for another IBM T41 laptop which has Intel 2100 chipset (B mode only).

Switching off WPA1 PSK security, or using WEP security works fine for the 3945ABG laptops.

Using WPA2 AES seems to work OK.

So it seems that there is a problem with the combination of Ubuntu, DD-WRT in WDS mode, WPA1-PSK security and the Intel 3945ABG chipset.

Note that the laptops with the 3945ABG chipsets work OK when running Windows XP SP2 in the same WDS network - the problem is only evident under Ubuntu.

---

### Post by JPorter on 2007-10-25
I use the Tomato firmware on my Buffalo WHR-HP-G54, which is similar to the Linksys WRT54GL.

The Tomato firmware is fantastic... I prefer it over DD-WRT and HyperWRT.  I've had zero problems since installing it, its featureset is broad and performance is high.

I highly recommend.  

[http://www.polarcloud.com/tomato](http://www.polarcloud.com/tomato)

---

### Post by tlg on 2007-10-25
JPorter
Thanks for the info.
I'll definitely have a look at the tomato firmware on that recommendation.
I need to use it on Linksys as well as Asus WL-500gP devices, and with WDS so I hope it has support for that, as well as the USB ports on the Asus.

---

### Post by tlg on 2007-10-25
Just one more thing I have found with the WDS and WPA1-PSK testing:
The connection appears to be made, then drops out afetr a few seconds, and this cycle is repeated continuously.
I accidently mistyped the passphrase word in the WPA2-AES mode and the effect was the same. 
So it seems that the problem may be something to do with incorrect handling of the passphrase.

---

### Post by n3tfury on 2007-10-25
> **JPorter said:**
> I use the Tomato firmware on my Buffalo WHR-HP-G54, which is similar to the Linksys WRT54GL.

The Tomato firmware is fantastic... I prefer it over DD-WRT and HyperWRT.  I've had zero problems since installing it, its featureset is broad and performance is high.

I highly recommend.  

[http://www.polarcloud.com/tomato](http://www.polarcloud.com/tomato)

why do you prefer it over DD-WRT?  the feature set isn't as broad as DD-WRT and i'm not sure how you're judging performance.  not being a smart ***, i'm just curious because i would try it out if i heard some real reasons why some people prefer it.

---

### Post by basketcase on 2007-10-25
Paid for Talisman, then went to OpenWRT, and then to dd-wrt.  

I've rolled out many routers to local small business, family and friends.  Only 2 are using Talisman still since they're remote to me and I didn't want to instruct the user how to flash his firmware and hope for the best.   

Upgraded to third-party to gain support for WDS.  
 
I switched to Buffalo routers and dd-wrt works great!

---

### Post by n3tfury on 2007-10-25
which specific buffalo are you using basketcase?

---

### Post by basketcase on 2007-10-25
> **n3tfury said:**
> which specific buffalo are you using basketcase?


WHR-G125

Side-by-side comparison (replacing my WRT54GL's with the Buffalos) I got a better and stronger signal with the Buffalo.

---

### Post by kentl on 2007-10-27
I'm now pretty satisfied with my setup at the moment. I use dd-wrt with static DHCP addresses for my three machines so that I can use Local DNS for them and port forwarding.

Security wise I use WPA with PSK at the moment. Perhaps I'll switch over to WPA2 later on, I got to check if my and other client laptops support it first.

I will setup DDNS with two providers. I'll have to use the startup script I guess, as the web GUI only has support for one provider.

It uses lots of RAM, but perhaps its normal? What do you people think?
[[IMG]http://img509.imageshack.us/img509/8595/13955757ip8.th.png[/IMG]](http://img509.imageshack.us/my.php?image=13955757ip8.png)

---

### Post by n3tfury on 2007-10-27
> **basketcase said:**
> WHR-G125

Side-by-side comparison (replacing my WRT54GL's with the Buffalos) I got a better and stronger signal with the Buffalo.

thanks basket.  i'm going to purchase one just for the hell of it even though there's nothing wrong with my WRT54GL (now running tomato)

---

### Post by asimon on 2007-10-27
> **n3tfury said:**
> why do you prefer it over DD-WRT?  the feature set isn't as broad as DD-WRT
IMO Tomato's user interface is much better then DD-WRT's. DD-WRT is badly organized and it's add-buttons are counter-intuitive: press ADD, enter data, press ADD again for more and loose your previous input. Before adding an other item you first have to save it. Tomato's user interface doesn't has such idiosyncrasies.

Another issue I like with Tomato is the logging of bandwidth usage.

The only thing I really like with DD-WRT  is [wi-viz]("http://devices.natetrue.com/wiviz/") (available in DD-WRT 24 RC4).

> **kentl said:**
> It uses lots of RAM, but perhaps its normal? What do you people think?
[[IMG]http://img509.imageshack.us/img509/8595/13955757ip8.th.png[/IMG]](http://img509.imageshack.us/my.php?image=13955757ip8.png)
Be aware that "Cache" and "Buffers" are essential free ram. But as it is absolutely pointless to have ram which is not used, the kernel uses it for caching and as file buffers.

---

### Post by n3tfury on 2007-10-27
yeah it sure is clean, perhaps a bit spartan.  i agree with the add buttons a bit of a pain in the **** i must say.  i haven't used some of the advanced feature set for awhile (chilispot for example) so i thought i'd try out something else.  any other suggestions asimon?

---

### Post by OffHand on 2007-10-27
> **kentl said:**
> I'm now pretty satisfied with my setup at the moment. I use dd-wrt with static DHCP addresses for my three machines so that I can use Local DNS for them and port forwarding.

Security wise I use WPA with PSK at the moment. Perhaps I'll switch over to WPA2 later on, I got to check if my and other client laptops support it first.

I will setup DDNS with two providers. I'll have to use the startup script I guess, as the web GUI only has support for one provider.

It uses lots of RAM, but perhaps its normal? What do you people think?

Mine is running dd-wrt as well and is also using quite a lot of ram...

---

### Post by kentl on 2007-10-29
So far it's working out quite fine for me! :)

I got DDNS to work with my Swedish provider Loopia.se today using the Inadyn application through the dd-wrt web interface. It was a bit tricky as documentation is a bit lacking. For example the URL box became left empty for me, as I only needed to use the Additional DDNS Options box in my Custom setup.

I do have one question. Perhaps someone here will be able to answer.

Is it possible to change the port of the web interface? I have a web server on my LAN and I want to make it accessible from the outside. I will setup port forwarding of port 80, but I still want to be able to access my dd-wrt web interface.

---

### Post by kentl on 2007-10-29
Having a forward on port 80 works quite well. As I use Loopback I can access my webserver like any other use. I'm also able to access the admin through the LAN DNS I've setup.

---

### Post by Atreus12 on 2007-12-16
I'm running dd-wrt on a WRT54GS v1.1, the one with 8mb flash and 32 mb ram :)

It's awesome. I even set up the status lights to blink red if someone is ssh'ed into the network from outside.

I managed to install it with no previous knowledge, so it's definitely do-able. dd-wrt has spoiled me, now I can never accept stock firmware.

-Andrew

---

### Post by BrokenBrick on 2008-01-16
I have a WRT54GL on the way from Newegg tomorrow.  I think I am going to start with Tomato and switch to dd-WRT if I don't like it.  I bricked a WRT54GSV7 that I got from BestBuy earlier, so yes it is possible, but that's mostly because I didn't follow the instructions very well :oops:

---

### Post by Steve Zenone on 2008-01-17
I'm running dd-wrt v23 sp2 (vpn) on a Linksys wrt54gl. I have OpenVPN setup in tunnel mode for road warrior connections and it works great. I can use Network Manager in GNOME (with OpenVPN support) to connect to my dd-wrt device. Here are instructions on how I set mine up:

[http://blog.zenone.org/2008/01/openvpn-and-dd-wrt-on-linksys-wrt54gl.html]("http://blog.zenone.org/2008/01/openvpn-and-dd-wrt-on-linksys-wrt54gl.html")

---

### Post by nikolaos on 2008-01-27
Hey everyone, i have a ASUS wl500-g with openWRT flashed on. I have openVPN & openDNS and i find things much better than when i was using dd-WRT (although it was just for 1 week). It is much better on the configuration side as well as the space available.
The webpage enviroment though is much much better in dd-wrt. Hence my question is: 
Can someone direct me to a link for QoS in openwrt, because the ones in the website are pretty old??

---

### Post by kevdog on 2008-01-27
If someone could point me to a link or write a small tutorial how to use the OpenVPN feature of dd-wrt that would be great.  I have the vpn version installed, but just dont know how to make use of it.

---

### Post by wieman01 on 2008-01-27
> **nikolaos said:**
> Hey everyone, i have a ASUS wl500-g with openWRT flashed on. I have openVPN & openDNS and i find things much better than when i was using dd-WRT (although it was just for 1 week). It is much better on the configuration side as well as the space available.
The webpage enviroment though is much much better in dd-wrt. Hence my question is: 
Can someone direct me to a link for QoS in openwrt, because the ones in the website are pretty old??
But isn't QoS kind of self-explanatory? I could help you set it up, but I really find DD-WRT's help function good enough. 

I have attached an example.

---

### Post by nikolaos on 2008-01-29
Thanks for the reply wieman01 but i need a HOW-TO for openWRT not DD-WRT. I repeat that the ones in their webpage are  2 yers old.

---

### Post by BatPenguin on 2008-02-01
Hello everybody,

I have the Siemens SE505 ([http://www.dd-wrt.com/wiki/index.php/Flash_Your_Siemens_SE505#Install_the_tftp_package_on_your_Linux_Box](http://www.dd-wrt.com/wiki/index.php/Flash_Your_Siemens_SE505#Install_the_tftp_package_on_your_Linux_Box))

..and I have to use the tftp method of flashing the router. Could somebody who has done this on Ubuntu please let me in on the secret of how it's done? It doesn't accept the command as one line as it apparently does under Suse since this one doesn't work:

```

#tftp -v 192.168.2.1 -m binary -c put dd-wrt.v23_mini_generic.bin
```

I apparently have to go to tftp prompt with "tftp 192.168.2.1" and then type "binary" and "put <flashname>" in a matter of seconds to get it done. I've tried it and it always just boots normally, I guess I'm not fast enough. Any way of getting it done with one quick command in Ubuntu? Anybody with experience using tftp to flash, please let me know. Thanks.

---

### Post by bufsabre666 on 2008-02-01
i love my dd-wrt, with the vlan wireless networks and the advanced firewall, and the overclocking, i put a heat sync in my router and i have it over clocked to 270mhz up from 200

---

### Post by wieman01 on 2008-02-02
> **bufsabre666 said:**
> i love my dd-wrt, with the vlan wireless networks and the advanced firewall, and the overclocking, i put a heat sync in my router and i have it over clocked to 270mhz up from 200
What are actually the benefits of overclocking your router?

---

### Post by bufsabre666 on 2008-02-02
> **wieman01 said:**
> What are actually the benefits of overclocking your router?

wider and more powerful range on wireless network, i can get my wireless network at full strength in my neighbors house 3 doors down

---

### Post by wieman01 on 2008-02-02
> **bufsabre666 said:**
> wider and more powerful range on wireless network, i can get my wireless network at full strength in my neighbors house 3 doors down
Wow, I'll check that out. How safe is it? Thanks for your help, buddy.

---

### Post by bufsabre666 on 2008-02-02
> **wieman01 said:**
> Wow, I'll check that out. How safe is it? Thanks for your help, buddy.

its safe as long as you have extra cooling in the router ((like i said i put a big north bridge heat sync in there)) and you should also enable the hold down the reset button to restore defaults

then it should be safe, ive been running it for about 7 months, the heat sync gets pretty warm but its never gone down ((other than that black out a few days ago but that doesnt count))

---

### Post by bobbocanfly on 2008-02-02
Planning to flash DD-WRT to my WRT54GS at some point but still terrified ill brick the thing and i cant live for long without a router.

Edit: Decided just to go for it (this was the third time i had been contemplating flashing dd-wrt, the other two times i was too scared) and its working fine :D This is really cool.

---

### Post by BatPenguin on 2008-02-02
> **bobbocanfly said:**
> Planning to flash DD-WRT to my WRT54GS at some point but still terrified ill brick the thing and i cant live for long without a router.

Edit: Decided just to go for it (this was the third time i had been contemplating flashing dd-wrt, the other two times i was too scared) and its working fine :D This is really cool.

Glad to hear yours worked. I just managed to get the fftp transfer started on the Siemens I mentioned above...and....bricked it. FIle transferred OK, router should've rebooted within 5 - 10 minutes. Never did. Finally after about an hour I rebooted it to find out I have a nice little paper weight on my hands.

Oh well, bought this thing used for 15 euros for this exact reason, so not a big loss, but still makes me feel very  suspicious about buing one of those 100+ euro routers and doing the same to it.

Too bad, I really would love to have a router that I could log into and use WOL to wake up my home network machines. oh well.

Edit: if somebody can suggest a router with a ridiculously easy and foolproof way of flashing it (think web interface or something like that), I'm all ears. I really would love to use this but, hmmm, so far I'm 0 for 1 :)

---

### Post by AndyCooll on 2008-02-02
> **BatPenguin said:**
> Edit: if somebody can suggest a router with a ridiculously easy and foolproof way of flashing it (think web interface or something like that), I'm all ears. I really would love to use this but, hmmm, so far I'm 0 for 1 :)

Well I've just bought a Linksys WRT54GL and flashed dd-wrt on to it. Was a piece of cake. Logged in using the Linksys web interface and there's a section for upgrading firmware.

There are quite a few howtos, these for instance:
[URL="http://www.testmy.net/forum/t-12222"] 	
How to install DD-WRT on a Linksys router [/URL]
[How to Flash the WRT54GL with DD-WRT Firmware]("http://www.mandladventures.com/2007/04/12/how-to-flash-the-wrt54gl-with-dd-wrt-firmware/")

Though I haven't used most of the features provided yet, I love the options and flexibility I now have available.

:cool:

---

### Post by bobbocanfly on 2008-02-02
> **BatPenguin said:**
> 
Edit: if somebody can suggest a router with a ridiculously easy and foolproof way of flashing it (think web interface or something like that), I'm all ears. I really would love to use this but, hmmm, so far I'm 0 for 1 :)

My Linksys WRT54GS was really simple. Web upload, wait 5 minutes, flush all settings and you are sorted. All of the Linksys WRT* seem fairly easy to flash.

---

### Post by BatPenguin on 2008-02-03
Thanks, bobbocanfly and AndyCooll, both of those routers look nice. Web interface sounds very nice for flashing. I'll keep an eye out for those ones...if I can find a used one for sale somewhere, I'll grab one.

I was looking at the instructions and the "brick" word wasn't too common there, so looks pretty good. If I can't find a used one, I'll probably wait until [www.dd-wrt.com](www.dd-wrt.com) re-opens their shop and starts selling pre-flashed routers again. If I have to get a new one, I wouldn't mind paying the little premium for somebody to take care of the flashing. My blood pressure can't handle watching the damn lights blink anymore while wondering if it's ever gonna reboot :)

---

### Post by wieman01 on 2008-02-03
> **bobbocanfly said:**
> My Linksys WRT54GS was really simple. Web upload, wait 5 minutes, flush all settings and you are sorted. All of the Linksys WRT* seem fairly easy to flash.
+1

Linksys routers are fine. I own a WRT54G and replacing the firmware was really simple.

---

### Post by bufsabre666 on 2008-02-03
i did it with my wrt54gs and it was cake, the only thing is the speed booster wasnt as prevalent after but it still worked ((enable the afterburner if you didnt ;-) ))

---

### Post by psb007 on 2008-02-06
I have a WRT54g v8 running DD-wrt micro and a WRT54g V2 running the standard version of DD-wrt. It seems to work with XP no problems and with my ubuntu boxes (only if they are connect via ethernet cable) my wireless is funky. Seems the WEP doesnt work and i am having trouble with the WPA settings. Any help is good help on this one.

Cheers

R4000 Compaq Presario

---

### Post by Pekkalainen on 2008-02-06
I use a WRT54GL 1.1 with Tomato firmware. The stock firmware would either be really slow or completely lock up all the time. I have my desktop and laptop hooked up via Wifi and my little webserver by wire to it and its been working splendidly ever since I flashed it to Tomato, and its nice to have internal IP adresses :)

Please remember, kids: Don't flash it via Wifi, I did that newbie mistake at first, bricked it and had to reinstall it via tftp #-o

---

### Post by wieman01 on 2008-02-07
> **psb007 said:**
> I have a WRT54g v8 running DD-wrt micro and a WRT54g V2 running the standard version of DD-wrt. It seems to work with XP no problems and with my ubuntu boxes (only if they are connect via ethernet cable) my wireless is funky. Seems the WEP doesnt work and i am having trouble with the WPA settings. Any help is good help on this one.

Cheers

R4000 Compaq Presario
That's in all likelihood a problem with your wireless adapter and has nothing to do with the router. 

This thread is a good starting point if you want to troubleshoot your network:

[http://ubuntuforums.org/showthread.php?t=684495]("http://ubuntuforums.org/showthread.php?t=684495")

---

### Post by Paco758 on 2008-08-12
I just flashed my wrt54gs v6 with dd-wrt micro today and it is running fine. I configured the wireless with WPA2 TKIP+AES and that seems to have worked perfectly: the Wii and several Ubuntu laptops have been able to connect wirelessly without too much fussing. 

The only thing that I wasn't able to sort right away was having the router connect to the internet through PPP. I had to revert that back onto a DSL modem rather than having the modem as a passthrough. I'm not sure why, but it works that way, and not the other. It ain't broke and I'm not fixing it for the time being. 

One other problem is that Firefox doesn't handle the WebUI very well. Use epiphany instead. I have had no problems with epiphany. It is probably best to use epiphany for the initial install steps as well, considering. 

The range is great with the default TX Power at 70. 

The handiest thing is using DNS service for local DNS. This was my primary reason for switching. 

It is worth switching to dd-wrt, even the micro version, from the original Linksys firmware. Just follow the instructions if you are using a v5-6 wrt54g/gs exactly and you won't have a problem. 

Good luck.

---

### Post by bcn17 on 2008-09-14
dd-wrt ROCKS!!
stable and feature rich. Flash right away!

---

### Post by bp1509 on 2008-09-14
d

---

### Post by cpcnw on 2010-05-16
Very late to this discussion however, can confirm recent flash of Firmware: 

DD-WRT v24-sp2 (12/28/09) mini - to my Linksys WRT54GS v1.1

Why mini? I was interested in seting up a micro / info site and wanted the most amount of space without doing the SD card mod.

Having said that my requirements are minimal in any case.

Space Usage JFFS2
4,736.00 KB / 4,052.00 KB

Current uptime is 7 days without a hitch, my wireless laptops are quick on the net too.

I have read briefly about how DD-WRT is partly closed source so I guess if you want to be more open use OpneWRT?

I'd also like to see feature comparison list between DD-WRT and OpenWRT.

---

### Post by cllow2020 on 2010-05-28
have linksys WRT54G-V5, try to flash it with openWT or DD-WRT but fail. are this version can't flash ??
 
 
 
update:-.......
great, updated using micro version, due to to lag or ram issue. refer link for great info
[http://www.dd-wrt.com/wiki/index.php/Version_5_And_6_Router_Information](http://www.dd-wrt.com/wiki/index.php/Version_5_And_6_Router_Information)

---

### Post by BigSilly on 2010-05-28
Dunno much about routers, but I have a Linksys WRT54GL, and I ended up putting Tomato on it. It's been very good, but I have to admit that a lot of the settings go way over my head! Great router otherwise. The missus bought it because it had Linux on it. Go missus! :D

---

### Post by blueturtl on 2010-05-28
I run DD-WRT on a Buffalo WHR-HP-G54.

Rock solid and configurable enough for our needs. You can pretty much change any settings you want without rebooting or dismissing your client connections. The router now has an uptime of 103 days. I never got around to testing OpenWRT. :)

---

### Post by mr-woof on 2010-05-28
can you do this on netgear routers?

---

### Post by CharlesA on 2010-05-28
> **mr-woof said:**
> can you do this on netgear routers?
Only on a few of them. I'm running DD-WRT on a Dlink DIR-615, which was newly supported in the beta release. It's running great too.

---

### Post by mr-woof on 2010-05-28
ah pity, you can guarantee it'll be the router I own that you can't flash :)

---

### Post by CharlesA on 2010-05-28
Could always check the router database over at dd-wrt.com.

---

### Post by cariboo on 2010-05-28
You can go [here]("http://www.dd-wrt.com/site/support/router-database") and check the database to see if your router is supported.

---

### Post by mr-woof on 2010-05-28
thanks guys, netgear wgr614 v7 is not possible :(

what things can you do with this firmware that you can't with the manufacturers?

---

### Post by blueturtl on 2010-05-28
Depends entirely on what router you have. Some have more robust stock firmware than others.

I gained the ability to run for long periods of time without crashing (so far hasn't crashed!), support for WPA2, port range triggering (really handy for those who like their VOIP) and also QoS (Quality Of Service, giving priority to different types of traffic over others)... the ability to use the router as a client to connect other computers to WLAN, the ability to bridge two routers, the ability to adjust the clock speed of the CPU and the TX power used...

---

### Post by iponeverything on 2010-05-28
dd-wrt works on the Linksys wrt160nv1 and wrt160nv3.

I picked up Linksys wrt160n-rm from amazon for $30. I knew from the amazon reviews that some people were getting ver. 3 of this router -- people were getting v2's as well -- I got a v3 and didn't bother with stock firmware at all and went strait to dd-wrt. 

wrt160nv2 is no-go for dd-wrt and if you google around you'll see that the v2 has lots of issues. So, its a roll of the dice. If I had gotten a version 2, I am sure that i would have regretted not spending the extra $60 dollars or so and ordering something that I knew would work with dd-wrt..  

I love it though, solid as a rock and very configurable. Mine is setup for bridging to the machine managing my 3G connection.

---

### Post by FuturePilot on 2010-05-28
I have a Linksys WRT54GS. Running the Micro version of DD-WRT. Works great.

```
$ uptime
 17:26:59 up 187 days,  1:32, load average: 0.00, 0.01, 0.00
```

```
Release: 10/10/09 (SVN revision: 13064)
```

---

