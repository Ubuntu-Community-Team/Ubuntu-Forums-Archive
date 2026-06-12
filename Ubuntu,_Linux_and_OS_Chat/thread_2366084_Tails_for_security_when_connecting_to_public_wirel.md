---
title: "Tails for security when connecting to public wireless?"
date: 2017-07-13
forum: Ubuntu, Linux and OS Chat
---

### Post by AbleTassie on 2017-07-13
Hello,

I will be travelling soon and plan to connect my laptop to some public wireless (wifi) sites. I've heard that Tails ( [https://tails.boum.org/](https://tails.boum.org/) ) is a good way to try to maintain security. Apparently it is used in a Live boot off a DVD/CD drive or usb port.

Does anybody have any comments about tails and if it is trustworthy? It does not appear to be in the Ubuntu Repositories that I can see.

Any other thoughts about using Tails would be appreciated. 

Thanks,

A.

---

### Post by deadflowr on 2017-07-14
[I]Thread moved to **Ubuntu, Linux and OS Chat**
[/I]
Tails has nothing to do with Ubuntu or Ubuntu's security designs.
If you have problems with Tails please post here
[https://ubuntuforums.org/forumdisplay.php?f=401]("https://ubuntuforums.org/forumdisplay.php?f=401")

---

### Post by TheFu on 2017-07-14
When on public wifi, you should use either
* full VPN to a network you trust
* SOCKS proxy to a network you trust
* TOR but don't believe that TOR is 100% anonymous

It isn't just wifi either - any hotel, library, or other wired public network is just as dangerous.

Being 100% secure is very hard.  Most people will make a mistake that breaks it.  Tails offers a false sense of security/anonymity for most people. If any cloud/local/web account is used that you have used from any other device, then you are no longer anonymous when using Tails.

Are all VPNs equal?  Nope.  Don't use PPTP (which has been hacked since 2002) and I'd wonder about any VPN that I didn't setup myself.  With that statement, there are times when I'd prefer NOT to tie my connection to my own network, so a reputable, paid, VPN is needed.  Look for a paid VPN that doesn't keep logs and supports IPSec for the tunnel.  Using a VPN run by someone else requires trusting they didn't/don't do things you would no like. No way to be sure of that.  Convenience vs security is almost always a trade-off.

To Tails or not?  Can't say. It is just a normal linux distro preloaded with the same stuff you can load into your Ubuntu install.

---

### Post by AbleTassie on 2017-07-14
> **TheFu said:**
> When on public wifi, you should use either
* full VPN to a network you trust
* SOCKS proxy to a network you trust
* TOR but don't believe that TOR is 100% anonymous

It isn't just wifi either - any hotel, library, or other wired public network is just as dangerous.

Being 100% secure is very hard.  Most people will make a mistake that breaks it.  Tails offers a false sense of security/anonymity for most people. If any cloud/local/web account is used that you have used from any other device, then you are no longer anonymous when using Tails.

Are all VPNs equal?  Nope.  Don't use PPTP (which has been hacked since 2002) and I'd wonder about any VPN that I didn't setup myself.  With that statement, there are times when I'd prefer NOT to tie my connection to my own network, so a reputable, paid, VPN is needed.  Look for a paid VPN that doesn't keep logs and supports IPSec for the tunnel.  Using a VPN run by someone else requires trusting they didn't/don't do things you would no like. No way to be sure of that.  Convenience vs security is almost always a trade-off.

To Tails or not?  Can't say. It is just a normal linux distro preloaded with the same stuff you can load into your Ubuntu install.

Thanks Fu,

Can you recommend one or more paid VPNs? Do you know of reliable instructions on how to set up your own VPN?

A.

---

### Post by TheFu on 2017-07-14
Nope and nope.  Sorry.

Good VPN providers change all the time. I probably will not renew mine.  There are comparison articles all over the web. Just find one that isn't too old and from a reputable source. Often defcon groups will make a chart every year or 2 for their members.  Google for complaints about any on your short list. Also google for any govt-friendly ones if that is a concern to you.  For example, the Russian govt required all VPN providers running inside their borders provide them with decryption keys.  Some providers decided to leave Russia, but some did not. If you never use servers inside Russia, it probably isn't an issue, but it is something to consider.

Setting up openVPN is a non-trivial thing if you want anything useful (IMHO).  It is very complex, because it has so many features that make sense for very many different uses.  

I use an internal pfsense router to deal with the local VPN. IMHO, VPN doesn't belong on an edge router connected to the WAN links.  But most of the time, I just use ssh with a tunnel into the LAN.

---

### Post by pauljw on 2017-07-15
> **AbleTassie said:**
> Thanks Fu,

Can you recommend one or more paid VPNs? Do you know of reliable instructions on how to set up your own VPN?

A.

I use Private Internet Access(PIA) [https://www.privateinternetaccess.com/](https://www.privateinternetaccess.com/) 

They're reasonably priced, have excellent support including complete on site setup instructions, left russia, don't log and run irc now if I'm not mistaken so they're trusted.

There are lot of vpn providers, check out a few.

---

### Post by TheFu on 2017-07-15
PIA may not be the VPN provider you want. They have changed some of their policies which made many customers mad.  If they meet your needs, great.  

Do your research.  

Capabilities and features of VPNs change all the time.

---

### Post by AbleTassie on 2017-07-15
Thanks to everybody, especially the Fu.

A.

---

### Post by kurt18947 on 2017-07-16
> **pauljw said:**
> I use Private Internet Access(PIA) [https://www.privateinternetaccess.com/](https://www.privateinternetaccess.com/) 

They're reasonably priced, have excellent support including complete on site setup instructions, left russia, don't log and run irc now if I'm not mistaken so they're trusted.

There are lot of vpn providers, check out a few.

I us PIA as well, they have a downloadable script that makes installation really easy. I'm not unduly concerned about government monitoring; anything confidential I send can be easily discovered via subpoena if they're interested. I'm mostly concerned about financial account info, credit cards etc. not being intercepted by the person a few rooms away. Something you could consider would be to use a live USB or even a full install to a USB drive. That would limit the amount of information already on your /home partition ....... cookies, browsing history etc. You could also simply create another user account for that location and wipe it when done. I'm not sure how much protection a new user account would offer.

---

### Post by TheFu on 2017-07-16
I've used PIA.  

No need to down load their app. Standard openvpn client stuff works. You don't need to trust their client-side stuff if that isn't something you want.  They used to have ovpn files for all their servers in a single ZIP file on their site somewhere. Those are probably still there somewhere.

PIA does not meet my needs.

---

### Post by mikodo on 2017-07-16
> **TheFu said:**
> PIA may not be the VPN provider you want. They have changed some of their policies which made many customers mad.  If they meet your needs, great.  

Do your research.  

Capabilities and features of VPNs change all the time.

Thanks! I wouldn't have known to look, for what is happening with them.

My subscription with PIA is up, towards the end of August, (if they are still running then). I'll be changing my provider. I have an alternative in mind.

---

### Post by unityforever on 2017-07-24
> **TheFu said:**
> When on public wifi, you should use either
* full VPN to a network you trust
* SOCKS proxy to a network you trust
* TOR but don't believe that TOR is 100% anonymous

It isn't just wifi either - any hotel, library, or other wired public network is just as dangerous.

Being 100% secure is very hard.  Most people will make a mistake that breaks it.  Tails offers a false sense of security/anonymity for most people. If any cloud/local/web account is used that you have used from any other device, then you are no longer anonymous when using Tails.

Are all VPNs equal?  Nope.  Don't use PPTP (which has been hacked since 2002) and I'd wonder about any VPN that I didn't setup myself.  With that statement, there are times when I'd prefer NOT to tie my connection to my own network, so a reputable, paid, VPN is needed.  Look for a paid VPN that doesn't keep logs and supports IPSec for the tunnel.  Using a VPN run by someone else requires trusting they didn't/don't do things you would no like. No way to be sure of that.  Convenience vs security is almost always a trade-off.

To Tails or not?  Can't say. It is just a normal linux distro preloaded with the same stuff you can load into your Ubuntu install.

may i ask you is the data transmitted via SOCKS proxy are encrypted?

by the way...how to use IPSec VPN in ubuntu?

---

