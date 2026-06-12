---
title: "Securing windows and vm's running ubuntu"
date: 2022-02-01
forum: Security
---

### Post by wildmanne39 on 2022-02-01
Hi, I use tor browser in my vm's, is installing a vpn on my windows 11 host good enough for my host and guest operating systems? It seems to me that I would want the vpn on my host for sure and I figure it is enough to have the vpn running on my host and that I do not need it on my guest but I want to make sure.

Thanks

---

### Post by Frogs Hair on 2022-02-01
The internet connection my _V-Box_ machines is enabled and disabled from the host and that would suggest that the host vpn would protect those machines. There are many network settings in the V-Box manger that can be applied to each operating system and I've not learned about those yet being fairly new to VMs of any kind.

---

### Post by DuckHook on 2022-02-01
It depends on how you have networking set up on your VM&#8594;host. If you have the VM bridged to your host (the default settings) then, yes, your VM will go through the VPN. But if you have a fancier setup, then the VM might bypass host and go directly to your router, in which case, no VPN (unless you've got one running on the router as well). The latter topology is useful for people running, say, a web server on their VM which they want directly connected to the Internet without going through their host.

Can you give us an idea of your network topology? Both internal and external?

---

### Post by DuckHook on 2022-02-01
@Wild Man,

An errant thought just popped into my head:

Another option is to run the VPN directly from your router. That way, *everything* is VPNed, which will make the whole host/guest thing academic. It also has the benefit of VPNing your phones and mobile devices too, although you might not want that. Most half&#8209;decent routers these days will allow them to be set up as VPN clients. The drawbacks: throughput slows down anywhere from a little bit to a lot (depending on your VPN provider), you may compromise the benefits of the VPN depending on how you use your computers and the VPN provider now knows your DNS queries (instead of your ISP). This last isn't really much of a consideration&#8212;if you didn't trust your VPN more over your ISP, you shouldn't be using them.

---

### Post by Frogs Hair on 2022-02-01
In the case of V-Box selecting the host only network adapter would ensure that the VM is using the VPN. There are other options to investigate.

---

### Post by wildmanne39 on 2022-02-01
> **DuckHook said:**
> It depends on how you have networking set up on your VM&#8594;host. If you have the VM bridged to your host (the default settings) then, yes, your VM will go through the VPN. But if you have a fancier setup, then the VM might bypass host and go directly to your router, in which case, no VPN (unless you've got one running on the router as well). The latter topology is useful for people running, say, a web server on their VM which they want directly connected to the Internet without going through their host.

Can you give us an idea of your network topology? Both internal and external?
Hi DH, yes I have it setup with the default settings and that is what I thought but I usually do not run Ubuntu in a VM I prefer to run windows in a vm instead, thank you for clearing that up for me.

---

### Post by wildmanne39 on 2022-02-01
That&#8217;s the way my network is setup and I was almost positive that the vpn being installed with networking in this configuration would cover the host and guest, I am going to research how to make my system more secure.

Now to choose a vpn to use.
 
Thank you FH for clarifying the settings needed.

---

### Post by #&amp;thj^% on 2022-02-01
> **wildmanne39 said:**
> Hi DH, yes I have it setup with the default settings and that is what I thought but I usually do not run Ubuntu in a VM I prefer to run windows in a vm instead, thank you for clearing that up for me.

To ease ones mind check "IP" (Whats my Ip) DNS Leaks.
How well is it running under Windows? (Off Topic)

---

### Post by #&amp;thj^% on 2022-02-01
> **wildmanne39 said:**
> Hi, I use tor browser in my vm's, is installing a vpn on my windows 11 host good enough for my host and guest operating systems? It seems to me that I would want the vpn on my host for sure and I figure it is enough to have the vpn running on my host and that I do not need it on my guest but I want to make sure.

Thanks

Wiregaurd on the Host, OPENvpn in the Guest if you want to play. (Or Visa-versa)
If done correctly you don't suffer a big drop in speed.(Mbps)

---

### Post by wildmanne39 on 2022-02-01
Hi 1fallen, so you believe it is best to have a vpn on both the host and the guest?

---

### Post by #&amp;thj^% on 2022-02-01
Not the best per say. :)
But hey a double tunnel, can't be a bad thing. ;)
I use this method **_only _**when I'm monitoring bad things.

---

### Post by wildmanne39 on 2022-02-01
> **1fallen said:**
> Not the best per say. :)
But hey a double tunnel, can't be a bad thing. ;)

Is there particular way I would have to set it up to make them work together without a lot of slow down?

---

### Post by #&amp;thj^% on 2022-02-01
> **wildmanne39 said:**
> Is there particular way I would have to set it up to make them work and together without a lot of slow down?

My Friend, do we want this as a how to? Or how? (A PM won't allow enough space)
Give me some time, to best think how to reply
EDIT: This will take me some time due to work load, But I use KVM, might make a big difference.
You can run a linux VM on Windows, and then run most of the KVM toolchain inside it. But the core KVM depends having the Linux kernel running in baremetal. Without that, you're dependent on the qemu emulator, which should work in theory, albeit slowly.

---

### Post by wildmanne39 on 2022-02-01
> **1fallen said:**
> My Friend, do we want this as a how to? Or how? (A PM won't allow enough space)
Give me some time, to best think how to reply

Yes a how to is excellent, we always post all help in the forum so the whole community can benefit, thank you very much.

---

### Post by #&amp;thj^% on 2022-02-01
> **wildmanne39 said:**
> Yes a how to is excellent, we always post all help in the forum so the whole community can benefit, thank you very much.

Ok then it may be lengthy. :)
To start try Wiregaurd for Windows: [https://www.wireguard.com/install/](https://www.wireguard.com/install/)
Then for testing how the two mesh together. (WG on Windows VPN on linux): [https://vladtalks.tech/vpn/setup-wireguard-on-windows](https://vladtalks.tech/vpn/setup-wireguard-on-windows)
wilmanne39 I'll make a concerted effort to keep fresh information here.
BTW Good To Chat to U, been a minute.

---

### Post by wildmanne39 on 2022-02-01
> **1fallen said:**
> Ok then it may be lengthy. :)
To start try Wiregaurd for Windows: [https://www.wireguard.com/install/](https://www.wireguard.com/install/)
Then for testing how the two mesh together. (WG on Windows VPN on linux): [https://vladtalks.tech/vpn/setup-wireguard-on-windows](https://vladtalks.tech/vpn/setup-wireguard-on-windows)
wilmanne39 I'll make a concerted effort to keep fresh information here.
BTW Good To Chat to U, been a minute.

Out of curiosity can I use wiregaurd on host and guest?


Thank you very much and good to talk to you too.

---

### Post by #&amp;thj^% on 2022-02-01
> **wildmanne39 said:**
> Out of curiosity can I use wiregaurd on host and guest?


Thank you very much and good to talk to you too.

I've never got two of the same working. (WG Host WG Guest or openvpn Host openvpn Guest)(I didn't spend a great deal of time trying though)
That would choke our speed to near death.

---

### Post by #&amp;thj^% on 2022-02-01
> **1fallen said:**
> I've never got two of the same working. (WG Host WG Geust or openvpn Host openvpn Geust)(I didn't spend a great deal of time trying though)
That would choke our speed to near death.
Maybe I can make a easier solution here, I used Expressvpn Lightway protocol on Windows 11 and Nordlynx as my WG connection on linux. (Speed Test showed out of possible 60 Mbps with both going I still had 40 Mbps down and 11 up)
There is a $cost here though.

---

### Post by wildmanne39 on 2022-02-01
> **1fallen said:**
> I've never got two of the same working. (WG Host WG Geust or openvpn Host openvpn Geust)(I didn't spend a great deal of time trying though)
That would choke our speed to near death.

Okay, I was just curious.

---

### Post by #&amp;thj^% on 2022-02-01
> **wildmanne39 said:**
> Okay, I was just curious.

So was I at first. :)

---

### Post by DuckHook on 2022-02-01
> **wildmanne39 said:**
> …I use tor browser in my vm's…> **wildmanne39 said:**
> …is best to have a vpn on both the host and the guest?> **wildmanne39 said:**
> …to make them work together without a lot of slow down?
Let's look at this from a meta perspective:

That's a lot of layering you will have going on there. It *will* slow you down, possibly to a painful crawl.

Essentially, it means the following: VM &#8594; Host NAT &#8594; LAN NAT &#8594; VPN 1 &#8594; VPN 2 &#8594; TOR Entry Node &#8594; TOR Relay &#8594; TOR Exit Node &#8594; Destination

The return packets will traverse the same long and winding path.

This topology is certainly safe (and I'm usually all for that) but is it really essential for you to have *that* much layering?

There's a point of diminishing return. You achieve marginally more anonymity at great cost in performance.

---

### Post by wildmanne39 on 2022-02-01
> **DuckHook said:**
> Let's look at this from a meta perspective:

That's a lot of layering you will have going on there. It *will* slow you down, possibly to a painful crawl.

Essentially, it means the following: VM &#8594; Host NAT &#8594; LAN NAT &#8594; VPN 1 &#8594; VPN 2 &#8594; TOR Entry Node &#8594; TOR Relay &#8594; TOR Exit Node &#8594; Destination

The return packets will traverse the same long and winding path.

This topology is certainly safe (and I'm usually all for that) but is it really essential for you to have *that* much layering?

There's a point of diminishing return. You achieve marginally more anonymity at great cost in performance.

No it's not essential but I am curious how much of an impact this will have on speed, I have a little time on my hands, I think I am going to have to have surgery either way I am laid up at the moment and have time to experiment, I really only need one vpn I imagine and I do not use tor browser a lot I am just checking things out.

---

### Post by DuckHook on 2022-02-01
> **wildmanne39 said:**
> No it's not essential but I am curious how much of an impact this will have on speed, I have a little time on my hands, I think I am going to have to have surgery either way I am laid up at the moment and have time to experiment, I really only need one vpn I imagine and I do not use tor browser a lot I am just checking things out.
Ah! You're doing this for kicks and giggles!

Then, go nuts my friend!

(Hope your surgery goes well.)

---

### Post by wildmanne39 on 2022-02-01
> **DuckHook said:**
> Ah! You're doing this for kicks and giggles!

Then, go nuts my friend!

(Hope your surgery goes well.)

Thank you DH.:)

---

### Post by #&amp;thj^% on 2022-02-02
Source Used: [https://restoreprivacy.com/vpn/multi-hop/](https://restoreprivacy.com/vpn/multi-hop/)

Disclaimer: For the majority of users, a multi-hop VPN may be overkill and not worth the performance tradeoffs (increased latency and slower speeds). A standard (single-hop) VPN setup with strong encryption, zero leaks, and zero logs, other privacy tools (secure browser, ad/tracking blocker, etc.) should be adequate.

However, for those interested in achieving higher levels of privacy and security, there are multi-hop VPNs.

Single VPN Host (Wiregaurd)
```
me on Wed Feb 02 at 08:39 AM in ~ branch: (HEAD) 
>> speedtest
Retrieving speedtest.net configuration...
Testing from Performive (104.200.132.106)...
Retrieving speedtest.net server list...
Selecting best server based on ping...
Hosted by TELUS (Vancouver, BC) [3.77 km]: 47.436 ms
Testing download speed................................................................................
Download: 47.09 Mbit/s
Testing upload speed......................................................................................................
Upload: 22.58 Mbit/s

```
Double VPN Guest (OpenVpn)
```
me@me-Standard-PC-i440FX-PIIX-1996:~$ speedtest
Retrieving speedtest.net configuration...
Testing from Maxihost LTDA (2.57.171.15)...
Retrieving speedtest.net server list...
Selecting best server based on ping...
Hosted by Claro net vírtua (São Paulo) [1.91 km]: 314.023 ms
Testing download speed................................................................................
Download: 17.34 Mbit/s
Testing upload speed......................................................................................................
Upload: 11.13 Mbit/s

```
That is a big hit on speed.
Now one a little closer
```
me@me-Standard-PC-i440FX-PIIX-1996:~$ speedtest
Retrieving speedtest.net configuration...
Testing from Eonix Corporation (45.131.194.49)...
Retrieving speedtest.net server list...
Selecting best server based on ping...
Hosted by Netprotect (Seattle, WA) [0.76 km]: 49.753 ms
Testing download speed................................................................................
Download: 43.22 Mbit/s
Testing upload speed......................................................................................................
Upload: 21.26 Mbit/s
me@me-Standard-PC-i440FX-PIIX-1996:~$ 

```
Closing thought I would not spin your own VPN for privacy sake.
My best To Wild Man && DH

---

### Post by DuckHook on 2022-02-02
Thanks for the test results 1f.

I've never bothered to actually test my connections, but you have inspired me to do so. The following are my results:

Bare metal no VPN

```
310 Mbps down
125 Mbs up
```

Bare metal host with 1 VPN (exit node 1200 km away)
```

310 Mbps down
110 Mbs up
```

Surprisingly little loss.

Containerized with 2 VPNs—one on host, one in container (final exit node 1600 km away)
```
290 Mbps down
83 Mbps up
```

Again, not bad for two VPN layers. Note, however, that I use containers. A VM would add a tiny bit more overhead, though not really that much more.

2 VPNs and TOR
```
12 Mbps down
9 Mbps up
```

High degradation ranging from 1/10 for upload to 1/25 (yikes!) for download. These results are no surprise. The TOR relays this time were Switzerland &#8594; Germany &#8594; Germany which, as far as TOR goes, isn't at all bad. I've had some circuits that crossed the pond four times and they were excruciating. Sites would time out waiting for or resending packets.

Conclusion:

Double VPN is okay if you have a good VPN service(s). All bets are off if you use the free ones.

TOR, however, is a pig. Though no surprise, the starkness of the numbers is rather sobering. Moreover, it's a crapshoot. If you luck on to an efficient speedy circuit, then you could get decent throughput. If you draw a joker circuit that spans the globe two times, it's unusable.

---

### Post by #&amp;thj^% on 2022-02-02
> **DuckHook said:**
> 

Double VPN is okay if you have a good VPN service(s). **_All bets are off if you use the free ones._**

Amen Brother.:) Even some paid, but that's a different colored horse.

---

### Post by DuckHook on 2022-02-02
> **1fallen said:**
> ...I would not spin your own VPN for privacy sake.
I've just recently done the following having learned it from other forum gurus:

I've set my home router up as a VPN server using Wireguard. It has no access to any home LAN and just reflects traffic back into the Internet. When I'm out of the house, I now VPN into that router to reach the Internet. I must say that the results have been great and I wish I had done this sooner. But this works for me because I have a business account that gives me high throughput and a static IP. Others may be better off with one of the commercial VPN providers with their thousands of server nodes scattered all over the planet.

I consider the biggest threats to be sniffers on public WIFI. Therefore, my private VPN looks after that. If I wanted the privacy of bypassing my ISP, I could always set up the router as a VPN client to my VPN provider. I have't done that up to now because I didn't want the performance hit, but your inspiration to actually quantify what were only suspicions has educated me that it really isn't much of a performance hit, so I might now consider it.

---

### Post by #&amp;thj^% on 2022-02-02
> **DuckHook said:**
> I've just recently done the following having learned it from other forum gurus:

I've set my home router up as a VPN server using Wireguard. It has no access to any home LAN and just reflects traffic back into the Internet. When I'm out of the house, I now VPN into that router to reach the Internet. I must say that the results have been great and I wish I had done this sooner. But this works for me because I have a business account that gives me high throughput and a static IP. Others may be better off with one of the commercial VPN providers with their thousands of server nodes scattered all over the planet.

I consider the biggest threats to be sniffers on public WIFI. Therefore, my private VPN looks after that. If I wanted the privacy of bypassing my ISP, I could always set up the router as a VPN client to my VPN provider. I have't done that up to now because I didn't want the performance hit, but your inspiration to actually quantify what were only suspicions has educated me that it really isn't much of a performance hit, so I might now consider it.
Yep that's so very close to my set-up as well. :)
My Router is not a commercial grade router, with a paid for firewall. I'm required to send telemetry.

---

### Post by wildmanne39 on 2022-02-04
Hi everyone, a couple of questions, where I enter the Address it has to be like > Address = 194.128.2.2/32 with a range of ip addresses right and not like > 192.168.2.1? I can not find any ip address like the first one only the later, and these directions are setup for the vpn to be on one computer and the vps to be setup on another right so essentially I will have my own vpn server in my house and not one like norde? when I setup my guest OS the same will be true with it?

How do I determine the following information 
> Endpoint = 32.185.112.15:12345

Thank you

---

### Post by DuckHook on 2022-02-04
Are you using Wireguard?

If so, try the following website, with instructions modified to suit your particular server and client: [https://homenetworkguy.com/how-to/configure-wireguard-opnsense/](https://homenetworkguy.com/how-to/configure-wireguard-opnsense/)

He also has a good guide for setting up OpenVPN, but OpenVPN is more involved: [https://homenetworkguy.com/how-to/configure-openvpn-opnsense/](https://homenetworkguy.com/how-to/configure-openvpn-opnsense/)

Even though these tutorials are made for OPNSense, the general principles are applicable universally.

With respect to address notation, if you are asking about the allowed IPs on the server, then yes, it should be of the x.x.x.x/32 form. However, I'm confused by your 194.128.2.2/32 address since this falls outside of the private ranges. AFAIK, both server and client addresses should be in the private ranges since you are setting up what is basically a private VPN network.

The endpoint is the IP address that your ISP has assigned to you. If this is a dynamic address like those on most consumer accounts, then you will need to subscribe to some sort of Dynamic DNS service and make the endpoint your DynDNS URL instead of an IP address (which would change from time to time). Example: vpn.wildman.com:12345  Even if it is static, the usual recommendation is to register a public domain, then assign the IP address to the domain rather than use the actual IP address. That way, you can make use of DNS safeguards like DNSSec and DoT or DoH to prevent MitM attacks.

The port number (in your example, 12345) must be the one you assigned when you set up your Wireguard server, so this is a customized field. The default Wireguard port is 51820, but security-mined people will change this to an arbitrary port in order to evade port scanning bots.

Best, I think, to take a look through HomeNetworkGuy's tutorials. If there is still anything unclear after that, I will try to help as best I can.

---

### Post by DuckHook on 2022-02-04
> **wildmanne39 said:**
> ...these directions are setup for the vpn to be on one computer and the vps to be setup on another right so essentially I will have my own vpn server in my house and not one like norde? when I setup my guest OS the same will be true with it?
...and yes, the end goal is to run a private VPN server so that you won't need a commercial provider like Nord (unless you want one).

It should be noted that, on most consumer grade ISP accounts, throughput is asymmetrical. Upload speeds are usually only 1/4 to 1/10 that of download speeds. Since a private VPN requires packets to go into then out of your home router, this could be a significant choke point. Packets going into your router should be okay, but going out will be choked to your ISP's maximum upload speed. This happens twice: on your packets' initial route from source to destination, then on the return route from destination to source.

The reality is that a self-hosted VPN service is bearable only if you have a decent account from your ISP. This was a big reason that I went for a business account. Aside from the static IP (which simplifies life a lot by avoiding the use of DynDNS), the big reason was much higher upload speeds.

---

### Post by CharlesA on 2022-02-04
I don't use a VPN, but I have some VMs sitting on their own VLAN so I can control what they can and cannot connect to at the router/switch.

With that said, I have the host set up as a trunk port and set the network card on each VM with whatever VLAN ID I want it to be a part of. It seems to work decently for me, but it also means I'm not using an always-on VPN to encrypt my traffic.

---

### Post by DuckHook on 2022-02-04
> **CharlesA said:**
> I don't use a VPN, but I have some VMs sitting on their own VLAN so I can control what they can and cannot connect to at the router/switch.

With that said, I have the host set up as a trunk port and set the network card on each VM with whatever VLAN ID I want it to be a part of. It seems to work decently for me, but it also means I'm not using an always-on VPN to encrypt my traffic.

You are describing LAN >> WAN whereas I believe that what Wild Man is looking for is Mobile Device >><< Internet >><< Home Router without ever connecting to his LAN. I could have mistaken Wild Man's intentions though.

---

### Post by wildmanne39 on 2022-02-05
> Are you using Wireguard?
Yes I am, your explanation cleared up some confusion for me, I have a great desktop I can use as an vpn server but I am thinking about buying another rasberry pi.

Thank you CharlesA for you suggestions.

---

### Post by DuckHook on 2022-02-05
> **wildmanne39 said:**
> …I have a great desktop I can use as an vpn server but I am thinking about buying another rasberry pi…
You may wish to consider getting something just a bit more robust than a RPi.

Or, if you have any old desktop laying around, then a viable alternative is to install another NIC in the thing and use pfSense or OPNSense. Although the RPi is a very versatile little beastie, it does have its brittle aspects because it relies on an SD card. Moreover, its lack of multiple NICs is limiting.

If you decide to use the pf/OPNSense strategy, then you will have a super powerful enterprise grade router as your front gatekeeper. And since pf/OPNSense already comes with its own VPN server, it's relatively easy to set up a powerful VPN service without having to make fancy LAN routes and IP forwardings and poke holes in your firewall.

---

### Post by TheFu on 2022-02-08
Sorry, I'm late.  Not sure I understand everything said above. There was some meandering.

[B]No VPN:
[/B]29.58 Mbit/s down
2.60 Mbit/s up

**Commercial VPN (nearby exit node, openvpn AES256):**
28.35 Mbit/s down
2.86 Mbit/s up


**Commercial VPN (Next country away exit node, openvpn AES256):**
27.30 Mbit/s down
2.84 Mbit/s up

**Commercial VPN (Japan exit node, openvpn AES256):**
22.17 Mbit/s down
2.53 Mbit/s

What this tells me is that
a) I have a fast VPN service, if they are trustworthy and don't retain any logs. A few years ago, the FBI asked for data with a court order and they were unable to provide any. I think they changed owners, so who know what will happen today.
b) I need to find a faster ISP. In theory, I'm on a business plan with 30/5Mbps. To get a bump in speed, the cost is 2x what I'm already paying with is over 2x more than a residential 300Mbps/symmetric plan.  AT&T fibre is symmetric. Cable is not. Most Cable uploads won't go over 1 channel, which is a tad over 35Mbps on DOCSISv3.

I don't see the point of double VPN, especially if TOR is being used. Just add 2 more intermediate nodes in the TOR route and forget the VPN.

I'm not a fan of having a WAN router do anything besides routing and firewall duties. Adding complexity there is asking for more attack vectors and odd failur modes.  I run a VPN server ( WG, ovpn, and ssh) for access when I'm away and for any wifi-connected devices here (I don't trust any wifi at all to be secure), but that is a completely different purpose than going on the internet seeking a little privacy.

If any of your systems phone-home, now your router-based VPN has just given up who you are.  Think of the IoT things phoning home. That BR player, TV, streaming stick, thermostat, wifi-connected phone/tablet, Plex Server ... all phoning home.  Maybe just want specific systems using the VPN?

If you use TOR, use a different user-login and never post using any logins to cloudy services that you've used previously, outside TOR. Probably best not to write much at all with TOR, since our writing styles are like fingerprints to people who study those things.

As for Windows security, my remaining system has a whitelist of locations it can visit which don't including phoning home. When MSFT changed the EULA, I backed out those updates and prevented updates going forward. I boot MS-Windows about once a week to enter financial data and do stock analysis. Orders are handled from Linux.

I'm not a fan of using r-pi for VPN or NAS purposes.
I run my VPN in a KVM VM using PCI passthru of a NIC to keep that traffic separate from the host and other VMs.  There have been some issues with shared NIC traffic being seen by other VMs and the host. Perhaps those have been fixed, but there is always at least 1 more problem ... and usually 50 more. 

As a programmer, I've worked on SEI-CMM5 process coding projects that lasted decades.  I recall the year it was believed that no more critical bugs existed in the software. They were using statistics. However, over the remaining years of the project, they tracked every bug and determined there were over 100 critical faults discovered later that were already in the code.  This was the most reviewed, most tested, non-trivial code in the world. Everyone there (multiple, independent, companies) had a mandate to create bug-free software, period, following optimized processes and using statistical process management methods.  The statistics were such that we'd actually delay sending code to the client if our process model indicated a bug was likely and nobody had found any in the review.  About 90% of the time, we'd find the undiscovered bug(s) - before testing. I have little expectation that any commercial software or F/LOSS is nearly as bug free.  When I moved to commercial software development, it was crazy how many bugs where known and ignored due to other priorities - usually driven by marketing.

---

### Post by DuckHook on 2022-02-08
> **TheFu said:**
> &#8230;I run a VPN server ( WG, ovpn, and ssh) for access when I'm away and for any wifi-connected devices here (I don't trust any wifi at all to be secure), but that is a completely different purpose than going on the internet seeking a little privacy&#8230;
&#8230;
&#8230;I run my VPN in a KVM VM using PCI passthru of a NIC to keep that traffic separate from the host and other VMs.  There have been some issues with shared NIC traffic being seen by other VMs and the host. Perhaps those have been fixed, but there is always at least 1 more problem ... and usually 50 more.
It's amazing the brilliant little strategies that I keep learning from you.

Just so's I'm sure I understand: you bind a NIC physically to a VM to run as a sandboxed VPN server. Only "serious" computers, presumably on their own vLAN, are routed through this VPN. The other IoT stuff don't get a sniff of it and go directly out to the Internet. I know from previous postings of yours that you have all of that stuff on its own little vLAN, probably with enough firewalling to suffocate the bejeezers out of them.

This is a great topology. I think I'll give it a go in the next few weeks.

---

### Post by TheFu on 2022-02-08
I don't use vlans.  Where those make sense is when a single physical wire is used to support multiple LANs. But a vlan tag is just a tag - a request - not a mandate. If you want better security, use separate LANs on separate physical networks.  A few $20 cheap GigE dumb switches connected to your core router/firewall can provide the needed separation. The LANs should be physically connected to a different router port for correct firewalling and separation.

If there are managed switches on each end of a VLAN'd wire, then those will split off each LAN to a specific port at the client-edge. That would prevent the "tag" security door issue of VLANs.  
I've seen VLANs used in businesses where each desk had a desktop and VOIP VLAN going down the same wire to a hub at the cube.  Both ports were hot for for VLANs - and security was broken.  There are some nifty fun things we can do to VOIP equipment, just sayin'.  At 1 client, they actually allowed the VLAN for their servers on every ethernet cable, so if we knew to use the server tagged VLAN, bypassing all the physical locked doors for direct, full, network access to their internal server LAN was trivial.

Technology all has limitations. We tend to condense all the little details and somehow VLANS = security seems to be left.  Or HTTPS = security, neither of those are true and it is easy to ignore/forget the details.

---

### Post by #&amp;thj^% on 2022-02-08
@ TheFu post #37 Brilliant =d>

---

### Post by DuckHook on 2022-02-08
Unfortunately, I'm stuck with the limitations imposed by the existing single wire topology of my house. Running parallel wires to certain rooms is a non-starter.

I don't want to hijack Wild Man's thread any further. If I have any more questions about this off-topic, I'll start my own thread.

Sorry for the digression, Wild Man. Hope you've gotten your Wireguard working.

---

### Post by #&amp;thj^% on 2022-02-08
> **DuckHook said:**
> Unfortunately, I'm stuck with the limitations imposed by the existing single wire topology of my house. Running parallel wires to certain rooms is a non-starter.

I don't want to hijack Wild Man's thread any further. If I have any more questions about this off-topic, I'll start my own thread.

Sorry for the digression, Wild Man. Hope you've gotten your Wireguard working.

Actually I think currently all of this will or can help Wild Man, I wouldn't call this a Hijack but better clarity and understanding.
Best Regards DH

---

### Post by DuckHook on 2022-02-08
> **1fallen said:**
> Actually I think all of this will or can help Wild Man, I wouldn't call this a Hijack but better clarity and understanding.
I believe you are right, 1f, so I will keep going.
> **TheFu said:**
> …If there are managed switches on each end of a VLAN'd wire, then those will split off each LAN to a specific port at the client-edge. That would prevent the "tag" security door issue of VLANs.
Well, at least I got that little detail right then.

I have a VoIP box that has to be in a separate room from my router. The packets get there after snaking through two smart switches from which a whole bunch of other LANs branch off. But at least the port to the VoIP box is untagged, so I did get that right.

This is a mind boggling topic. I will look into the sort of physical separation that you advocate, though I don't know how much flexibility I have to configure it. If I understand you properly, after implementing your physically separated LANs, the remaining weak point would be the router itself.

---

### Post by wildmanne39 on 2022-02-08
I got real busy this week so I installed nordvpn for now and I did get it setup with my vm's and I have t set to double vpn so I thinnk I am good for now.

Thank you everyone for you help, there is a lot of very good information in this thread that I will come back to several times I am sure.

---

### Post by CharlesA on 2022-02-09
> **TheFu said:**
> 
If there are managed switches on each end of a VLAN'd wire, then those will split off each LAN to a specific port at the client-edge. That would prevent the "tag" security door issue of VLANs.  
I've seen VLANs used in businesses where each desk had a desktop and VOIP VLAN going down the same wire to a hub at the cube.  Both ports were hot for for VLANs - and security was broken.  There are some nifty fun things we can do to VOIP equipment, just sayin'.  At 1 client, they actually allowed the VLAN for their servers on every ethernet cable, so if we knew to use the server tagged VLAN, bypassing all the physical locked doors for direct, full, network access to their internal server LAN was trivial.


That's what I do with the managed switches I use. I set up each port for a specific vlan or set up as a trunk port. I've only really used vlan tagging on VMs when I don't put them on a separate NIC.

---

