---
title: "Does anybody know any working free VPN service ?"
date: 2011-04-07
forum: Security
---

### Post by kapetr on 2011-04-07
Hi,

a cup of days I'm trying to find any working free VPN service.
Without success.

[to run Windows in VM and use service which works in Windows is no solution for me - it is pathetic and it takes too much system resources]

Everywhere are many questions. but no answers.
All tutorials I read are old and nothing works.

Can someone help ?

---

### Post by Fire_Chief on 2011-04-07
Hi kapetr!

I'm not sure I fully understand your question.
Are you looking for VPN software to let you access your private network (at home or work)? VPN is mostly used for secure remote access to a specific place.

Could you give more details on what you are seeking to do?

Cheers!

---

### Post by kapetr on 2011-04-08
I'm searching for free (not paid) service, not client SW, which works with Ubuntu.

So this service must offer access via e.g. OpenVPN, PPTP, ... and not just proprietary client SW for Windows only.

I had try UltraVPN, USAip, CyberGhost, ItsHidden,... but even if I had follow the instructions, all my attempts to connect failed.

--kapetr

---

### Post by BkkBonanza on 2011-04-08
But what are you needing to access via the VPN? Are you just wanting to connect to the internet via a VPN or tunnel link to protect yourself from local eavesdropping? Or is there something in particular at the other end of the VPN you need?

---

### Post by kapetr on 2011-04-08
> **BkkBonanza said:**
> But what are you needing to access via the VPN? Are you just wanting to connect to the internet via a VPN or tunnel link to protect yourself from local eavesdropping? Or is there something in particular at the other end of the VPN you need?

Anonymization  - to hide my IP, ...
Specially useful in public WiFi networks, ...
The services I have listed are exactly for such purposes.

I'm now "fighting" with USAIP - there is tutorial for Ubuntu which don't work why network-manager-openvpn(-gnome) applet is absolutely buggy. Manually to run OpenVPN works +- fine. But this service is limited by only 7 minutes of usage (free). There are some free services which works under Windows and I look for at least one working with Linux. 

--kapetr

---

### Post by adagio on 2011-04-08
I found I had to reboot for PPTP to startup when using gnome to set the connection up.  Worked find after that.

I can understand wanting to use a VPN, I use one all the time with nowt but the https port open, you can also get a free 30 day proxy trial from [getcocoon.com]("http://getcocoon.com").  Haven't seen any free VPNs though that give config. details, and even those on windoze generally don't work very well if at all.

You have to fork out $5 a mnth I'm afraid (I'm with AceVPN).  Is it possible to host your own on a free Unix shell I wonder (lemme know if you ever do this :)

A warning though, even with a VPN and firewall with nowt but the https port open, and with a proxy setting on the browser! the browser is still hacked, I'm looking into this at the moment wondering if it is Flash that is the culprit - running one browser with flash disabled, and another one to view flash pages only.

---

### Post by BkkBonanza on 2011-04-08
Ok. I see what you're after. Depending on just how anonymous vs. private you need there is a solution I use. I don't really need anonymous so much as privacy from local inspection.

I use Amazon EC2 servers as on-demand connection portals that I can completely control without any third-party service or trust issues. I say that knowing that Amazon could potentially provide account details to any legal request or even inspect my traffic if they had the urge. But they run hundreds of thousands of server instances that continually start and stop on demand. I don't think there's much of a likelihood that they have time/inclination to monitor traffic. And any service you use potentially can do that, and record access - so I figure it's as safe as any other, maybe more so.

Amazon currently has a "**first year free**" "micro server" instance where you can start up and run your own instances up to full time (720 hrs/mo) for free. It can be used in several ways but the easiest is to just start a pre-made instance and use SSH as SOCKS5 proxy mode. This way requires no setup at all since SSH is running off the get go and you just start the instance and then use a single ssh command locally to start the proxy and then route traffic to it.

The second way is to start and configure a pre-made instance, install and test OpenVPN on it to suit your needs (the same as if on your own local system) and then "**snapshot**" the system so you can start/stop it as you need on demand, any time you like. Cmd line tools make start/stop a dead easy cmd at your local machine (and scriptable).

In either case to local observers it looks like you have a connection to one random IP address owned by Amazon (they have millions) and all your traffic appears to distant observers also to come from an Amazon IP. A legal entity could get a court order to see that your account was used for the traffic but short of that no one else is too likely to get that information.

Amazon [IP ranges]("https://forums.aws.amazon.com/ann.jspa?annID=986") here - rough count 640k available.

After the first year you pay by the hour and using a spot instance this costs about 2 cents/hour + BW. Still cheap.

---

### Post by azcrumpty on 2011-04-09
I use The Onion Router (Tor) for that. If performance isn't an issue for you and you have the ability to leave a machine on at home that can be an exit node, you can use what you have.  

I configure my laptop with squid and a Tor hidden service.  I setup socket connection to the hidden proxy and set Firefox to use the proxy.  This is a poor man's VPN solution and doesn't do other services, but it has been handy in a pinch.

Do you have a full time home connection?  I use dnsalias, pfSense, PPTP, and OpenVPN at home to get free VPN services.  I try to leverage my home cable connection as much as possible to get my free services rather than rely on Tor.

---

### Post by wacky_sung on 2011-04-09
If you using VPN just to be so called "Anonymous" then you are wrong and there is only privacy involved. Those proxy / VPN service which they address it as Anonymous is just a commercial marketing to draw people.

---

### Post by listerdl on 2011-04-10
> **wacky_sung said:**
> If you using VPN just to be so called "Anonymous" then you are wrong and there is only privacy involved. Those proxy / VPN service which they address it as Anonymous is just a commercial marketing to draw people. So what is the benefit of VPN then?

Does it just mean that anyone looking in can see that you are you but they cannot see what it is that you are doing? Right?

---

### Post by wacky_sung on 2011-04-10
> **listerdl said:**
> So what is the benefit of VPN then?

Does it just mean that anyone looking in can see that you are you but they cannot see what it is that you are doing? Right?

VPN is just an additional security layer to your privacy which mean it protect you from the 3rd party to intercept what communicate / transfer you have done. 

You <<<---------->>>>VPN Server<<<<---------->>> Receiver
          Encrypt                   Encrypt/Not at all


If some people trying to do some criminal attempt conceal behind any VPN / Proxy server, there is always a ip log behind each VPN / Proxy server even though you can undergo a chain of proxies.

---

### Post by kapetr on 2011-04-11
> **adagio said:**
> I found I had to reboot for PPTP to startup when using gnome to set the connection up.  Worked find after that.


Do You mean the discussed USAIP service ?
By me has restart no effect.

> **adagio said:**
> 
You have to fork out $5 a mnth I'm afraid (I'm with AceVPN).  Is it possible to host your own on a free Unix shell I wonder (lemme know if you ever do this :)


To get free unix account is quite so difficult as to get free VPN :-)
And if they would allow to run OpenVPN service ? ...

--kapetr

---

### Post by kapetr on 2011-04-11
> **BkkBonanza said:**
> Ok. I see what you're after. 
I use Amazon EC2 servers as on-demand connection portals ....
After the first year you pay by the hour and using a spot instance this costs about 2 cents/hour + BW. Still cheap.

Thank You very much for that very interesting information.
I will take look on it. I hope I will with my very low knowledge of English find out how it works and how to use it.

Once more - thanks

--kapetr

---

### Post by adagio on 2011-04-17
Hackers can break openvpn I think:

What kind of hacking is going on here??
[http://www.unix.com/security/158075-what-kind-hacking-going-here.html](http://www.unix.com/security/158075-what-kind-hacking-going-here.html)

You have to 1) open only a https udp port in your firewall (+ DNS), 2) bring the network interface up, 3) start openvpn, and 4) add firewall rules for http + https and tun (+ DNS if changed, bootp if running, etc.).

I haven't looked at PPTP/L2TP, so not sure what is involved here.

Even with openvpn running Flash is still hacked and results in your box being trashed (though I haven't checked Chrome's inbuilt Flash as yet, which is sandboxed nowadays). There must be some sort of http tunneling code or something otherwise embedded in Flash - I'm not sure exactly what is going on here (some rogue easter eggs quite possibly - Adobe really should open up this code so we can take a good look at it).  You can sandbox a browser but the level of sandboxing that might be needed would probably mean you can't, e.g., cut and paste between the sandboxed browser and anything else:

SELinux sandbox on Ubuntu
[http://ubuntuforums.org/showthread.php?t=1724689](http://ubuntuforums.org/showthread.php?t=1724689)

If a basic AppArmor sandbox were to fix the hack then that would be OK, but a full SELinux sandbox places the browser in a Xnest server with a temporary (kiosk/ guest) login.

---

### Post by amerinde on 2011-04-17
When i use Windows, i use Anchorfree for VPN. It gives me a US ip. [http://hotspotshield.com/](http://hotspotshield.com/)

Works great for registering US game in Germany.. lol and also use it for getting programs not available where i live.

---

### Post by kapetr on 2011-04-18
> **amerinde said:**
> When i use Windows, i use Anchorfree for VPN. It gives me a US ip. [http://hotspotshield.com/](http://hotspotshield.com/)

Works great for registering US game in Germany.. lol and also use it for getting programs not available where i live.

There are HOWTOs about HotSpotShield and Linux, but they are old and there are many reported end unanswered problems ...

So I did it not try jet.

BTW - it is necessary to register by Anchorfree to get account by HotSpotShield ? Or are this two different services ?

--kapetr

---

### Post by kapetr on 2011-04-18
FYI: I have get USAIP working :-)

The (unsolved) problem was with my local BIND9 - it gets crazy when there is new default route. So I have give up and use public DNS servers over host route via the old (not VPNed) route.

--kapetr

---

### Post by kapetr on 2011-04-18
> **adagio said:**
> Hackers can break openvpn I think:

What kind of hacking is going on here??
[http://www.unix.com/security/158075-what-kind-hacking-going-here.html](http://www.unix.com/security/158075-what-kind-hacking-going-here.html)

You have to 1) open only a https udp port in your firewall (+ DNS), 2) bring the network interface up, 3) start openvpn, and 4) add firewall rules for http + https and tun (+ DNS if changed, bootp if running, etc.).

I haven't looked at PPTP/L2TP, so not sure what is involved here.




Due my bad English, I do not understand well.

You mean here server mode of OpenVPN I hope.

> 
Even with openvpn running Flash is still hacked and results in your box being trashed (though I haven't checked Chrome's inbuilt Flash as yet, which is sandboxed nowadays). There must be some sort of http tunneling code or something otherwise embedded in Flash - I'm not sure exactly what is going on here (some rogue easter eggs quite possibly - Adobe really should open up this code so we can take a good look at it).  You can sandbox a browser but the level of sandboxing that might be needed would probably mean you can't, e.g., cut and paste between the sandboxed browser and anything else:

SELinux sandbox on Ubuntu
[http://ubuntuforums.org/showthread.php?t=1724689](http://ubuntuforums.org/showthread.php?t=1724689)

If a basic AppArmor sandbox were to fix the hack then that would be OK, but a full SELinux sandbox places the browser in a Xnest server with a temporary (kiosk/ guest) login.

I use standard AppArmor config for Firefox - so it can R/W "anything" in my $HOME :-(  I had no time to change it.

And - as You talk about FLASH  - is here some security risk on Linux too ? And what kind ? And if yes - what to do ? AppArmor ? And/or to run FF from different user account to protect my $HOME ?

--kapetr

---

### Post by amerinde on 2011-04-19
> **kapetr said:**
> There are HOWTOs about HotSpotShield and Linux, but they are old and there are many reported end unanswered problems ...

So I did it not try jet.

BTW - it is necessary to register by Anchorfree to get account by HotSpotShield ? Or are this two different services ?

--kapetr

yes, anchorfree and hotspotshield are the same. hotspot is made by anchor.. :o

i never had to register, i just downloaded the program and installed it, and it goes. You can register and pay, if you want, but i dont use it enough.

---

### Post by kapetr on 2011-04-20
> **amerinde said:**
> i never had to register, i just downloaded the program and installed it, and it goes. You can register and pay, if you want, but i dont use it enough.

... on Windows only :-(

---

### Post by dentaku65 on 2011-04-25
> **kapetr said:**
> Anonymization  - to hide my IP, ...
Specially useful in public WiFi networks, ...
The services I have listed are exactly for such purposes.

I'm now "fighting" with USAIP - there is tutorial for Ubuntu which don't work why network-manager-openvpn(-gnome) applet is absolutely buggy. Manually to run OpenVPN works +- fine. But this service is limited by only 7 minutes of usage (free). There are some free services which works under Windows and I look for at least one working with Linux. 

--kapetr

Usaip it works pretty well here (just some disconnection) on Lucid
I prefer vpn1.usaip.eu host against the one proposed in their tutorial (vpn4.usaip.eu)

I'm using the PPA of NetworkManager Team instead the repos one (less buggy):
[https://launchpad.net/~network-manager/+archive/ppa](https://launchpad.net/~network-manager/+archive/ppa)
You can save safely demo password with it.

Heavy doubts that Usaip can manage https sites :-(

---

### Post by adagio on 2011-07-03
Has anyone mentioned Tor yet -- it works pretty well - select your entry and exit nodes carefully though.  A paid Tor service that didn't work at a snail's pace would be something for someone to do.

I'm also using ivpn.net -- more expensive that other VPNs, but I like the way you set your connect password and there is no way for you or anyone else to ever get it back, you just reset it again.  By contrast one service actually displays the passphrase in full clear text on the screen everytime you login, and will even let you download it in a file.

---

