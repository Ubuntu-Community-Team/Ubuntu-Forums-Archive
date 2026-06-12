---
title: "Software/OS spying and hardware spying. How to deal with both of them?"
date: 2019-04-14
forum: Security
---

### Post by vibers on 2019-04-14
Hi,

I am using Windows 10 but as it does a lot of spying on the user I intend to switch to Linux and from Linux versions I will pick the most popular and successful OS which is Ubuntu and this will solve my problem with software/OS spying. I have the solution for this.

But a few days ago I read about the Intel processors which have another operating system inside them called Management Engine which can bypass all encryptions, firewalls in the computers and read everything even when the PC is turned off. So the processor can do all the spying and it can't be stopped.

Kindly inform how big is this threat? Does the processor keep spying on the user all the time? And is there some way to stop the spying? Kindly inform. Best regards.:)

---

### Post by Rubi1200 on 2019-04-14
Hi and welcome to the forums :-)

Please post a link to the source you are referring to. Without reading the article or document you read how can we reasonably be expected to respond?

Thanks.

---

### Post by freemedia2018 on 2019-04-14
Hi vibers, welcome.

As you may have guessed, there are two options to avoid the problem you're talking about-- one is to use an older PC that does not have the feature. You would be surprised how far back that would go, however. Some may run Lubuntu, they would not be well suited for GNOME or KDE.

The other option is to use a non-Intel, non-AMD processor. Some ARM processors may qualify. More information here: [https://jxself.org/titanic.shtml](https://jxself.org/titanic.shtml)  

> The Intel Management Engine (ME), also known as the Manageability Engine, is an autonomous subsystem that has been incorporated in virtually all of Intel's processor chipsets since 2008

[https://en.wikipedia.org/wiki/Intel_Management_Engine](https://en.wikipedia.org/wiki/Intel_Management_Engine)

---

### Post by TheFu on 2019-04-15
I wear a tinfoil hat more than most.

For some things there isn't much we can do except to unplug the computer from the network or to have external devices block in and out access to any part of the computer except that which you approve.  This isn't easy, especially for unsophisticated, home, computer, users.  Most home networks block inbound connections, but don't prevent outbound connections at all, which means that if someone on the outside can trick the computer into opening a connection, then they effectively can bypass the firewalls. There are some commonly used techniques to accomplish that - javascript is a favorite.  Do you allow javascript in your browser?

You can run netstat to see which connections are being used inbound and outbound with source IP[noparse]s:[/noparse]ports and target IPs[noparse]:p[/noparse]orts.  Don't forget to monitor all the other protocols - the ones not based on ICMP or IP.  There are many others.

The main issue is limited to the computer, so having a well-maintained, well-configured, external firewall and external router is a good way to address this.  But there are liabilities with most router hardware too.

Security is always about having multiple layers and it is best to have those layers be physically separate.

---

### Post by Rubi1200 on 2019-04-15
@TheFu

I am interested in security but certainly do not have anywhere near the level of expertise you do.

Could you please comment on this article [https://www.eff.org/deeplinks/2017/05/intels-management-engine-security-hazard-and-users-need-way-disable-it](https://www.eff.org/deeplinks/2017/05/intels-management-engine-security-hazard-and-users-need-way-disable-it) and specifically the part where the authors write that > Not every machine is susceptible to the attack. For it to work, AMT has to have been both enabled and provisioned (commonly AMT is enabled but not provisioned by default).

If I understand correctly, isn't this more likely to be a problem in an enterprise situation and is unlikely (though I am sure not impossible) that an average home computer user would be affected?

---

### Post by 1clue on 2019-04-15
Certainly this would require an external firewall device, but how to get an adequate device which is not also affected?

Switching to some other brand of processor is of limited value as that processor may have an embedded processor we don't know about, controlled by some other agency. So out of the frying pan, into the fire.

I would start by building a system from scratch, and then ONLY hook it up through a port which can be monitored (a switch with a mirror port?) at the hardware level and which has no Internet connection. See what sort of packets it sends out and where it wants to send them, before there is any operating system attached. 

You would certainly need both outbound firewall rules prohibiting traffic to the sites the processor is trying to reach, and inbound firewall rules responding to that sort of traffic. And some sort of monitoring to ensure that your intel-based firewall/router is actually filtering that traffic.

---

### Post by vibers on 2019-04-15
freemedia2018, Thanks for your reply. I have checked the Processor found in your link but that would be quite expensive. I also checked other Linux PC makers’ websites but they charge quite high prices as compared to the prices charged by others. I agree that Arm based processors is the way to go if you care for your security. I would wish we see Arm processors based PCs with a reasonable price.

---

### Post by vibers on 2019-04-15
TheFu, Thanks a lot for your reply. The solution you posted is the most practical and can be applied sooner. Can you give a few links to some reasonably priced routers & firewalls? Also is there some way to find out what to block and what not to block. Kindly inform.

---

### Post by vibers on 2019-04-15
1clue, Thanks a lot for your reply. Could you suggest me some devices for that Kindly inform.

---

### Post by 1clue on 2019-04-15
> **vibers said:**
> freemedia2018, Thanks for your reply. I have checked the Processor found in your link but that would be quite expensive. I also checked other Linux PC makers’ websites but they charge quite high prices as compared to the prices charged by others. I agree that Arm based processors is the way to go if you care for your security. I would wish we see Arm processors based PCs with a reasonable price.

Arm is a SoC architecture. By definition, there are coprocessors and whatever else in there, and some of it is undisclosed closed-source stuff with proprietary "black box" blobs in there. So Arm is no more secure.

> **vibers said:**
> 1clue, Thanks a lot for your reply. Could you suggest me some devices for that Kindly inform.

I don't have recommendations, only speculation as I posted above.

Having done some research since you posted this, I'm not sure this has much security exposure for me personally.

It seems that this tech you're talking about is built around the same idea as IPMI, and some of the code is shared. IPMI is for servers, and the IME is for consumer products. Yes there are tools which could be used to take control of the sytem by remote, but at least according to the documentation you need to turn that stuff on first. Yes the processor is running if there's power, but if it has no IP address and is not responding to network activity then what's the harm?

If someone were to find a system which has the remote admin stuff turned on, then certainly there could be a huge problem. If they can install their own firmware there's no way to tell what you might get in there. But if you never turn it on, and if you were to take precautions with your site's firewall then I would think it could be managed.

Points:
[LIST=1]
[*]The processor has its own MAC address and direct control of part of the NIC. So it does NOT have the same IP address as your computer.
[*]You could define outbound and inbound rules on your firewall such that only known hosts have Internet access, either outbound or inbound.
[*]You could configure your DHCP server to put unknown addresses into a special IP range so that special rules applied within your network. Like a switch-based filter limiting access to other hosts on the net, if you have a nice switch.
[*]At least with IPMI, the controller does not seem to want to accept connections from a host with a different network number.
[LIST=1]
[*]This means that your "client" has to be on your same network.
[*]If you have an OpenVPN with a 'tap' mode (the VPN emulates a network card on the host network so it looks like you're inside the net) then they can get remote access, but not if you use 'tun' mode.
[*]If the new stuff enforces the same rule then this reduces the security exposure.
[/LIST]
[/LIST]

I'm not saying there's no security exposure in ANY situation, because clearly there is. My systems are always in the same place (no mobile devices except phones), behind a firewall I made. I'll see what I can do to at least detect activity from this controller, and mitigate its possible harm for me.

---

### Post by TheFu on 2019-04-15
> **vibers said:**
> freemedia2018, Thanks for your reply. I have checked the Processor found in your link but that would be quite expensive. I also checked other Linux PC makers’ websites but they charge quite high prices as compared to the prices charged by others. I agree that Arm based processors is the way to go if you care for your security. I would wish we see Arm processors based PCs with a reasonable price.

There appear to be 2 methods on Linux to check whether a system has MEI enabled. 
[https://www.cyberciti.biz/faq/how-to-check-whether-amt-is-enabled-and-provisioned-under-linux/](https://www.cyberciti.biz/faq/how-to-check-whether-amt-is-enabled-and-provisioned-under-linux/) (I consider this a reputable site).
I use nmap a little, but not with lua, so that technique didn't work for me.  I pulled the mei-amt-check code down, compiled it and ran it on 3 of my physical systems.
On AMD Ryzen:
```
$ sudo ~/bin/mei-amt-check 
Unable to find a Management Engine interface - run sudo modprobe mei_me and retry.
If you receive the same error, this system does not have AMT
```
Very much expected.

On both Intel systems - a) Pentium 3258 and a Core i5-8250U```

$ sudo  ~/bin/mei-amt-check 
Error: Management Engine refused connection. This probably means you don't have AMT
```
Both of these do have the mei_me kernel module loaded.  None of my boxes are "High end", sorry.

At least for my systems, this one variant doesn't matter.  If your system supports IPMI [https://en.wikipedia.org/wiki/Intelligent_Platform_Management_Interface](https://en.wikipedia.org/wiki/Intelligent_Platform_Management_Interface), then perhaps you should be worried.  IPMI has a history of not really having much security, just like RIBLO and DRAC cards.

ARM has all sorts of issues.  They just aren't as fast, capable, compatible, at least at the $100/CPU ranges.  Trying to find an ARM CPU that competes with a $80 Ryzen 5 1600 (65W) is impossible. Forget about mid-level or above gaming or any virtualization on ARM. I use some programs that have never been ported to ARM too, so include that in your "he's biased" calculations.

For routing, it isn't just about the CPU, it is about the packets/sec, which is why custom routers, from reputable vendors, known to support their product lines, could be the best choice. I've named them already.  If you find it in a big-box electronics store, that isn't likely a router for your best security.

If you seek a low-end desktop, then some of the higher-end ARM SBCs are a viable option.  Check out the Rock64PRO and the Odroid-N2.  These are in the $60-$80 range and I think both have GigE networking, USB3 ports and perhaps SATA-3 connectors.  You'd want to use an eMMC storage module for the OS-Boot, not any SD-based storage.  Running an OS on SD is brutal to the flash storage. Those are the good options if you want a tiny computer and don't need peripherals or much data throughput.  The lack of dual (or quad) NICs limits their usefulness as a router.

If it isn't clear, I've given up on trying to have a non-Intel/AMD server or desktop, except for play devices.  I'm going to believe that my router provides the best protection available due to the choices I make around that hardware, software, and network architecture.  I would never put wifi into a router.  Adding a PoE wifi-AP for $70 that can actually be located where you need it is much better than trying to get wifi signal out of a wiring closet or the corner home-office.  Plus, wifi standards are rapidly changing with plans for wpa3, wpa4, wpa5, and wpa6 over the next 6-10 yrs.  Best to have a solid router and be able to swap out the wifi-AP with minimal fuss, IMHO.  Plus, I don't trust any wifi enough to put it onto the LAN.  Wifi is put next to the internet and treated just like all other internet traffic.  If a wifi device needs access into a protected part of the LAN, then it needs to use a full VPN.

There are many more important security issues than the supervisor on a CPU, IMHO. Perhaps I'm just mis-informed, but worrying about the bucket of feed in the corner while the barn is on fire doesn't make sense when there is livestock and horses in the barn that need to get out for safety.  Ya'll.

That EFF link says this:
>  If provisioned, AMT listens on ports 16992 and 16993
```
sudo nmap  -p 16992-16993  172.22.22.1/24 |more
```
Should find them. Change the network/subnet to whatever you need.

---

### Post by 1clue on 2019-04-15
+1 for what TheFu says. All of that.

I have IPMI on more than one system. The IPMI processor (called a Base Management Controller, or BMC) is tied to a specific NIC by the BIOS settings. I leave them at the system board default, just in case my system gets the BIOS zapped for some reason. The physical NIC with the BMC on it in my case is attached to a network with no route to the Internet. I have the IPMI-controlled systems and one workstation on that network. None of them forwards packets for that interface. Virtual machines do not have access to that NIC, at all.

If I were really worried about this security exposure for your IME processor, I would add an external NIC and then make sure the internal NIC has no connection, or wire something up like what I did.

IPMI is very cool hardware. I specifically look for hardware with IPMI for my servers. Frankly I hadn't followed it closely enough to realize that the IME is the next generation of that.

You can't possibly investigate, use and configure IPMI without knowing that it's a massive security hole if you're not careful. It's blatant. In my opinion Intel should make more noise about this IME processor, so people are aware of it. But that said, the really dangerous stuff seems to be turned off in the BIOS by default.


With respect to coprocessors with closed-source blobs, we've never really been free of that ever. Your video card. Your motherboard. Whatever. Your TV, BluRay, phone, tablet, SmartHome hardware, you can actually get a light bulb with wifi built in and it talks directly on TCP/IP. Your car either does now or soon will have up to 20 processor subsystems each with IP addresses, and a cellular connection to the Internet. Eventually you have to trust somebody, or you have to prevent any new technology from entering your life.

---

