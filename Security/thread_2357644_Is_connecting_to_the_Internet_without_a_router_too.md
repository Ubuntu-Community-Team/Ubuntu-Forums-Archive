---
title: "Is connecting to the Internet without a router too risky ?"
date: 2017-04-04
forum: Security
---

### Post by linuxyogi on 2017-04-04
Hi,

My router just failed. I dont have the cash right now to buy a new one. My ISP provides internet using Ethernet cable so I have connected the cable directly to the LAN port of my PC.
I will buy a router in a couple of months. 

ufw is enabled. Is connecting to the Internet without a router too risky ?

---

### Post by Perfect Storm on 2017-04-04
Moved to Security.

---

### Post by bonestabone on 2017-04-04
Yes it is risky, but if you don't have a choice make sure ufw is enabled and configured properly.

The default settings might not be enough for your use case.

[https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)

---

### Post by linuxyogi on 2017-04-04
> **bonestabone said:**
> Yes it is risky, but if you don't have a choice make sure ufw is enabled and configured properly.

The default settings might not be enough for your use case.

[https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)

```
$ sudo ufw default deny 
```

```
$ sudo ufw status 

Status: active 
```

That's whats I have done. Do I need to do something more ?

---

### Post by bonestabone on 2017-04-04
Check the rules and see if there are any incoming ports that are open, if there are you might want to close some ports. Does it list any rules when you run the status command?

Oh looks like you set incoming default to deny, so I think that's good.

---

### Post by linuxyogi on 2017-04-04
> **bonestabone said:**
> Check the rules and see if there are any incoming ports that are open, if there are you might want to close some ports. Does it list any rules when you run the status command?

 When I scan my own IP is get this :
```
$ nmap <IP>


Starting Nmap 7.40 ( https://nmap.org ) at 2017-04-05 02:52 IST
Nmap scan report for ubuntu (<IP>)
Host is up (0.00019s latency).
All 1000 scanned ports on ubuntu (<IP>) are closed


Nmap done: 1 IP address (1 host up) scanned in 0.12 seconds



```

```
$ sudo ufw status verboseStatus: active
Logging: on (low)
Default: deny (incoming), allow (outgoing), disabled (routed)
New profiles: skip



```

---

### Post by TheFu on 2017-04-04
You can't scan your IP from inside. 
Use an external service or IP to see what it really looks like to the external world.

There are risks. It is always better to have another, separate, device, serving as a firewall + router than your desktop.  Old PCs can be used for this - low power PCs aren't a bad choice - they just need a linux server configured as a router and 2+ NICs. 1 for the Red network and the other for the Green network. That is a minimal config. Plus, these can be better maintained than almost any other commercial router which doesn't get patched nearly enough by you, me or the vendor.  With a Linux distro-based router, weekly patching keeps them up-to-date pretty easily.

---

### Post by linuxyogi on 2017-04-04
> **TheFu said:**
> You can't scan your IP from inside. 
Use an external service or IP to see what it really looks like to the external world. 

[ATTACH=CONFIG]274431[/ATTACH]

My ISP blocks all ports. I cant open any ports even if I want to . The above is result from GRC.com. I heard that the stealth thing is all hype. Is that correct ?

> **TheFu said:**
> 
There are risks. It is always better to have another, separate, device, serving as a firewall + router than your desktop. Old PCs can be used for this - low power PCs aren't a bad choice - they just need a linux server configured as a router and 2+ NICs. 1 for the Red network and the other for the Green network. That is a minimal config. Plus, these can be better maintained than almost any other commercial router which doesn't get patched nearly enough by you, me or the vendor. With a Linux distro-based router, weekly patching keeps them up-to-date pretty easily.

I will buy a router real soon. I have a raspberrypi. I heard it can be used as a router too. I will google and find out about it.

---

### Post by TheFu on 2017-04-04
I consider stealth as hype. I didn't think GRC scanned **all** ports, just popular ones.  Best to get to a small, family-run, restaurant and run a full **nmap -sT -p0** on the WAN IP across all ports.  Also, with your current default deny ufw rule, you should only see closed ports from any scan even if your ISP is wide open.  Most residential ISPs block FTP, SMTP, HTTP and CIFS ports - those are the main ones below 1024.

Raspberry Pi devices have limited I/O and limited CPU which isn't what you want in a router. Just because you can do something, that doesn't make it a good idea.  There are network services that raspberry pis are fine for - DHCP, DNS, DNS-filtering for ads, running a home email server or nextcloud box ... stuff like that.  I wouldn't run a VPN on a pi. Doesn't mean it can't, just that the network performance would be sluggish. A v3-pi would be a significantly more capable box, but it is fairly expensive for the I/O and CPU you get.  A $60 Intel CPU is 15x faster and has encryption extensions built-in - just sayin'.

If I were in the market, on the $sub-60 range, I'd look hard at the Ubiquiti Router-lite.  At the $120 range, I'd build a cheap Intel 35W system ($60 CPU) out of parts. For a higher price, a $150 APU2 which can do 650 Mbps throughput while routing.  

None of these are "end-user friendly", but they are all capable devices with fairly constant patch availability. I'm running an APU2 with pfSense and use another pfSense instance on a VM internally to deal with internal network requirements. The APU2 can also run Linux. These are GPU-less systems - zero GUI possible, so beware. You'll need console/serial access. 

YMMV.

---

### Post by HermanAB on 2017-04-05
Well, consider that most routers and 'firewalls' run Linux or BSD,  but they typically run a very trimmed down embedded version, which reduces the attack surface - and you don't put a firewall behind a firewall...

I have run thousands of server machines for several years, on the internet, with little or no maintenance - eventually, after four or five years, the PSU blows up.

Places like Google, Microsoft, Amazon, Microsoft, Rackspace - they run hundreds of thousands of Linux and BSD machines on the internet...

---

### Post by SeijiSensei on 2017-04-05
Yes, you can use the Raspberry Pi as a router.  See [https://help.ubuntu.com/community/Router](https://help.ubuntu.com/community/Router) and [https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing).

---

### Post by linuxyogi on 2017-04-05
I have decided to buy [this router]("http://www.amazon.in/TP-LINK-TL-WR841N-300Mbps-Wireless-Router/dp/B001FWYGJS/ref=sr_1_2?s=computers&ie=UTF8&qid=1491413774&sr=1-2&keywords=router").

---

### Post by TheFu on 2017-04-05
> **linuxyogi said:**
> I have decided to buy [this router]("http://www.amazon.in/TP-LINK-TL-WR841N-300Mbps-Wireless-Router/dp/B001FWYGJS/ref=sr_1_2?s=computers&ie=UTF8&qid=1491413774&sr=1-2&keywords=router").

A story about my tp-link router. For a number of reasons, it cannot be used anymore (buggy, unpatched firmware & zero support for after-market firmware) except as a LAN switch and wifi AP. It is not suitable for WAN protection, IMHO.  There were a few releases of openwrt for it, but none of those were production quality. It actually required a 4-step firmware process to even get a beta openwrt loaded (downgrade to prior release, load german firmware, then load buggy openwrt, then load the newer beta openwrt). On paper, the router was awesome.  IRL, things are very different.  It wasn't a a low-end TP-link either.

The lack of consistent updates by home router makers is a serious issue.

Just sayin'.

---

### Post by linuxyogi on 2017-04-05
> **TheFu said:**
> A story about my tp-link router. For a number of reasons, it cannot be used anymore (buggy, unpatched firmware & zero support for after-market firmware) except as a LAN switch and wifi AP. It is not suitable for WAN protection, IMHO.  There were a few releases of openwrt for it, but none of those were production quality. It actually required a 4-step firmware process to even get a beta openwrt loaded (downgrade to prior release, load german firmware, then load buggy openwrt, then load the newer beta openwrt). On paper, the router was awesome.  IRL, things are very different.  It wasn't a a low-end TP-link either.

The lack of consistent updates by home router makers is a serious issue.

Just sayin'.

Thanks for the warning. What is your opinion about [Netgear routers ]("http://www.amazon.in/Netgear-WNR614-Wi-Fi-Router-White/dp/B00M0ODVM8/ref=sr_1_7?s=computers&ie=UTF8&qid=1491415937&sr=1-7&keywords=router")? I just don't want to buy Dlink anymore.

---

### Post by SeijiSensei on 2017-04-05
I have been pretty happy with this TP-Link Archer: [https://www.amazon.com/gp/product/B00BUSDVBQ/](https://www.amazon.com/gp/product/B00BUSDVBQ/)

I only wish the Linux kernel had better support for AC adapters.  It seems to be taking a very long time before the stock kernel includes drivers for devices like this one: [https://www.newegg.com/Product/Product.aspx?Item=N82E16833704202](https://www.newegg.com/Product/Product.aspx?Item=N82E16833704202).  There is a driver, but it has yet to be incorporated in released kernels.

---

### Post by linuxyogi on 2017-04-05
> **SeijiSensei said:**
> I have been pretty happy with this TP-Link Archer: [https://www.amazon.com/gp/product/B00BUSDVBQ/](https://www.amazon.com/gp/product/B00BUSDVBQ/)

I only wish the Linux kernel had better support for AC adapters.  It seems to be taking a very long time before the stock kernel includes drivers for devices like this one: [https://www.newegg.com/Product/Product.aspx?Item=N82E16833704202](https://www.newegg.com/Product/Product.aspx?Item=N82E16833704202).  There is a driver, but it has yet to be incorporated in released kernels.

That router is highly expensive in [Indian currency]("http://www.amazon.in/Tp-Link-Archer-C7-Wireless-Gigabit/dp/B00CEB53MS/ref=sr_1_1?ie=UTF8&qid=1491417445&sr=8-1&keywords=TP-Link+Archer+C7+Wireless+Dual+Band+Gigabit+Router+%28AC1750%29"). I am looking for a product within Rs 1200.

---

### Post by SeijiSensei on 2017-04-05
> **linuxyogi said:**
> I am looking for a product within Rs 1200.
That's about US$18.  I've never bought a router for less than about $50.  I wouldn't know what to recommend at that price.  You can take a look here: [https://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=100158096%204024&IsNodeId=1&bop=And&Order=PRICED&PageSize=60](https://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=100158096%204024&IsNodeId=1&bop=And&Order=PRICED&PageSize=60)

---

### Post by TheFu on 2017-04-05
Post #9 above provides my suggestions for specific equipment for a home environment.

---

### Post by SeijiSensei on 2017-04-05
> **TheFu said:**
> Post #9 above provides my suggestions for specific equipment for a home environment.

The cheapest router you proposed, the Ubiquiti Edgerouter Lite, is $93 new at [Amazon]("https://www.amazon.com/Ubiquiti-Edgerouter-ERLITE-3-Desktop-Router/dp/B00HXT8EKE/").  That's nowhere near linuxyogi's ceiling of US $18.

---

### Post by TheFu on 2017-04-05
> **SeijiSensei said:**
> The cheapest router you proposed, the Ubiquiti Edgerouter Lite, is $93 new at [Amazon]("https://www.amazon.com/Ubiquiti-Edgerouter-ERLITE-3-Desktop-Router/dp/B00HXT8EKE/").  That's nowhere near linuxyogi's ceiling of US $18.

My mistake - meant to say "[ubiquiti edgerouter x]("https://www.amazon.com/Ubiquiti-ER-X-Networks-Router/dp/B0144R449W/")" - which is available from Ubuquiti Networks on Amazon for $49.95 [https://www.ubnt.com/edgemax/edgerouter-x/](https://www.ubnt.com/edgemax/edgerouter-x/) .  That isn't anywhere near $18 either, but throwing money away on a bad router that won't get patches in 8 months is worse than running without one, IMHO.  A router providing a false sense of security is worse than being afraid AND cautious without a router at all.  My stance on this has changed in the last few years.  I used to think that any router would provide sufficient protections, but that just isn't true anymore.  Too many back doors. Too many old, unpatched routers in the wild.

We all have budget constraints. Sometimes it isn't possible to get a good solution within the current budget. 
[https://arstechnica.com/security/2017/04/rash-of-in-the-wild-attacks-permanently-destroys-poorly-secured-iot-devices/](https://arstechnica.com/security/2017/04/rash-of-in-the-wild-attacks-permanently-destroys-poorly-secured-iot-devices/) shows what can happen to out of date routers.

Others are free to have different opinions and those are probably valid within their experiences.

---

### Post by linuxyogi on 2017-04-19
> **TheFu said:**
> A story about my tp-link router. For a number of reasons, it cannot be used anymore (buggy, unpatched firmware & zero support for after-market firmware) except as a LAN switch and wifi AP. It is not suitable for WAN protection, IMHO.

The lack of consistent updates by home router makers is a serious issue. 

I cleaned my router with a blower then cleaned the WAN port with isopropyl alcohol now the router is working again.

My question is how did you decide that your router is not suitable for WAN protection anymore ? Is there a method ?

I checked dd-wrt's site and my router is not supported. I also checked Dlink's web site there is no update for my firmware.

---

### Post by TheFu on 2017-04-19
> **linuxyogi said:**
>  My question is how did you decide that your router is not suitable for WAN protection anymore ? Is there a method ? 

**The first cutoff:**
Any linux-based router that hasn't been patched since February 2017 has a fatal flaw that lets anyone on the internet have complete, root, access, from anywhere. There isn't a firewall run on the router that will protect it.

So - if your router doesn't have a new firmware from after that time, it isn't suitable for use. 

**Longer Term Issues:**
Routers that cannot be patched, constantly, at least monthly, will have bugs that can be used by "bad people/actors" to do things you don't intend. If a vendor doesn't produce monthly updates for their firmware, then they aren't providing proper support. It really is that simple.
 It is crazy these days how poorly every cheap (less than $350) router make is maintained by users AND by the vendors.  They are used to selling something that doesn't need updates for the 10 yr life of the device. That is completely unacceptable for any security device connected to the internet.  Some of the $300+ routers which look cool are just as bad as the $15 specials from a security standpoint. It really is sad.

There is only one solution that I can see to these issues.  The only way I now to have continuously patched routers is to use a continuously patched OS as the base.  That mean I cannot use dd-wrt, openwrt, tomato, or any of the *-wrt clones on non-Intel compatible hardware.  The good news is that low-power, relatively inexpensive, Intel x86 compatible hardware designed for router use is available these days.  Load up a BSD or small Linux distro on those devices and we can patch daily if we like.  An old PC ($20) can be used if you like and don't mind the power use. It just needs to run Linux and have at least 2 network cards - Red Zone for the Internet and Green Zone for the LAN.  More ports mean more vlans can be managed, but with a dumb switch, you can add as many other devices as you like.
[B]
Keep WAN protection separate from Wifi:[/B]
And by keeping the wifi AP away from the router, the router life is drastically extended.  Wifi standards change every few years with different bandwidth and different frequencies.  The underlying routing doesn't really change that much over decades, so why change everything just for new wifi stuff?  For most people, the best location of their router isn't the same as the best location for their wifi AP. Separating these has other good aspects.

---

### Post by linuxyogi on 2017-04-19
@[[COLOR=#000000]TheFu[/COLOR]]("https://ubuntuforums.org/member.php?u=1037685")[COLOR=#000000] 

I get it. There is no shortcut when it comes to security. I am planning to buy [this motherboard / cpu]("http://www.amazon.in/Gigabyte-GA-J1800M-D3P-Motherboard-Built-Celeron/dp/B01MF5YPVA/ref=sr_1_1?ie=UTF8&qid=1492625857&sr=8-1&keywords=celeron+motherboard") combo and load pfsense on it.

In the meantime is there a way to find out if someone has access to my router / home network ? Any logs I should monitor ?[/COLOR]

---

### Post by The Cog on 2017-04-19
> **TheFu said:**
> **The first cutoff:**
Any linux-based router that hasn't been patched since February 2017 has a fatal flaw that lets anyone on the internet have complete, root, access, from anywhere. There isn't a firewall run on the router that will protect it.
Ooh! I haven't heard of that one. Can you point me to a fuller description of the vulnerability please?

---

### Post by linuxyogi on 2017-04-20
That's really scary stuff.#-o

I am having this weird idea. I am planning to use my desktop as pfSense box and my raspberry pi as my regular desktop.
What do you guys think ? Possible ?

---

### Post by The Cog on 2017-05-02
Ooh! Looky here. 
[https://arstechnica.co.uk/security/2017/05/intel-patches-remote-code-execution-bug-that-lurked-in-cpus-for-10-years/](https://arstechnica.co.uk/security/2017/05/intel-patches-remote-code-execution-bug-that-lurked-in-cpus-for-10-years/)
WIthout a  firewall between your computer and the internet, computers with intel vPro would be vulnerable to remote code execution regardless of the firewall rules in iptables, even a deny all.

---

### Post by TheFu on 2017-05-02
> **The Cog said:**
> Ooh! I haven't heard of that one. Can you point me to a fuller description of the vulnerability please?

[http://www.securityfocus.com/bid/97397](http://www.securityfocus.com/bid/97397)

The Intel CPU issue doesn't impact most desktop-CPUs.  It is a high-end or server thing. Think Xeon or Core i7.

---

### Post by linuxyogi on 2017-05-02
I am using pfSense now. So no more worries.

---

