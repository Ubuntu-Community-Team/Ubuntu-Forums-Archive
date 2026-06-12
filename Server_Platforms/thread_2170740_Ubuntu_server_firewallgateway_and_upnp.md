---
title: "Ubuntu server firewall/gateway and upnp"
date: 2013-08-27
forum: Server Platforms
---

### Post by Demented ZA on 2013-08-27
Hi guys,

I have an Ubuntu server rig that acts as a Gateway and Firewall between my lan and internet connections. Unfortunately I'm forced to use Ubisoft's uPlay in order to play games like Assasins creed, Splinter Cell Blacklist and Farcry 3. uPlay requires either port forwarding of ports 13000:13032,14000,14008 (incoming). Unfortunately port forwarding can only happen to one host at a time for the same port(s), unless using something like Upnp. I'm trying to set up more than one computer to access uPlay on my network for multiplayer and co-op, and thus port forwarding isn't an option here.

Enter upnp. I have followed the steps pertaining to the linux-igd package ([http://linux-igd.sourceforge.net/documentation.php](http://linux-igd.sourceforge.net/documentation.php)) to enable upnp. I'm also using Shorewall to configure my iptables, and followed the appropriate guide.

The result is that uPlay doesn't connect to Ubisoft's servers, and I can't log in. If I set up port forwarding, then the machine I forward it to works as intended, but that leaves any of the other machines unable to connect.

The usual solution would be to "enable upnp" on your router.

Thoughts, suggestions, etc, please?

---

### Post by Demented ZA on 2013-09-05
I understand the security issues regarding uPNP. I just figured that any Linux solution should be able to do at least the same as an off the shelf router. Sureley there must be someone who has multiple devices behind an Ubuntu server/gateway with the same problem?

Edit: I have followed this guide. I don't get any errors, but it doesn't solve the problem. According to the guide, the packages have been removed since Ubuntu 8.04.

[https://help.ubuntu.com/community/firewall/Linux_UPnP_Internet_Gateway_Device_%28linux-idg%29](https://help.ubuntu.com/community/firewall/Linux_UPnP_Internet_Gateway_Device_%28linux-idg%29)

---

### Post by ian-weisser on 2013-09-05
Let's look in the Ubuntu repositories for packages related to upnpd:
```
$ apt-cache search upnpd
libnatpmp-dev - portable and fully compliant implementation of NAT-PMP (dev files)
libnatpmp1 - portable and fully compliant implementation of NAT-PMP
gir1.2-gupnp-dlna-1.0 - transitional dummy package
gir1.2-gupnpdlna-1.0 - GObject introspection data for the DLNA utility library for GUPnP
minissdpd - keep memory of all UPnP devices that announced themselves
miniupnpd - daemon providing UPnP Internet Gateway Device (IGD) services
natpmp-utils - portable and fully compliant implementation of NAT-PMP (userland tool)
```

I see two upnpd implementations already in the Ubuntu repos: miniupnpd and natpmp. Have you investigated either of those?

---

### Post by Demented ZA on 2013-09-05
> **ian-weisser said:**
> Let's look in the Ubuntu repositories for packages related to upnpd:
```
$ apt-cache search upnpd
libnatpmp-dev - portable and fully compliant implementation of NAT-PMP (dev files)
libnatpmp1 - portable and fully compliant implementation of NAT-PMP
gir1.2-gupnp-dlna-1.0 - transitional dummy package
gir1.2-gupnpdlna-1.0 - GObject introspection data for the DLNA utility library for GUPnP
minissdpd - keep memory of all UPnP devices that announced themselves
miniupnpd - daemon providing UPnP Internet Gateway Device (IGD) services
natpmp-utils - portable and fully compliant implementation of NAT-PMP (userland tool)
```

I see two upnpd implementations already in the Ubuntu repos: miniupnpd and natpmp. Have you investigated either of those?

Uhm, no, I havn't. The linux-igd package installs and I can set it up as described in the guide, but it doesn't work and I'm not having any luck finding out how to diagnose it, then I saw that the article states it doesn't work since 8.04. 

I wasn't aware of the NAT-PMP package. 

I have come accross miniupnpd, but its not in my packages (Ubuntu server 12.04). I see its in the Universe repo for Quantal. I'm adding universe to my Precise server and checking it out now.

Thanks for the response, you're at least pointing me in the right direction! Will report back what I find.

---

### Post by Demented ZA on 2013-09-05
```
 sudo apt-cache search upnpd
libnatpmp-dev - portable and fully compliant implementation of NAT-PMP (dev files)
libnatpmp1 - portable and fully compliant implementation of NAT-PMP
minissdpd - keep memory of all UPnP devices that announced themselves
natpmp-utils - portable and fully compliant implementation of NAT-PMP (userland tool)


```

Reading up on NAT-UPNP, its the Mac equivalent to universal plug and play. NAT-PMP only supports the Mac stuffs, whilst miniupnpd package supports both implementations, but isn't available for 12.04, only 12.10. I can install it by adding the repo, but maybe it would be safer to just upgrade to 12.10?

---

### Post by ian-weisser on 2013-09-05
Good research!
linux-igd is in the repositories for 12.04 (and, indeed, for current releases, too)
```
$ rmadison -u ubuntu linux-igd
 linux-igd | 1.0+cvs20070630-2 | lucid/universe | source, amd64, armel, i386, ia64, powerpc, sparc
 linux-igd | 1.0+cvs20070630-3 | precise/universe | source, amd64, armel, armhf, i386, powerpc
 linux-igd | 1.0+cvs20070630-4 | quantal/universe | source, amd64, armel, armhf, i386, powerpc
 linux-igd | 1.0+cvs20070630-4 | raring/universe | source, amd64, armhf, i386, powerpc
 linux-igd | 1.0+cvs20070630-4 | saucy/universe | source, amd64, armhf, i386, powerpc
```

Seems like that wiki page is several years out of date (last edited 2009).
I don't have upnpd installed, removed it a few years ago when I determined I wasn't using my media server nearly as often as I expected.
Nevertheless, a quick look at the manpages for upnpd and upnpd.conf seems to show that the config file is where all the action is.

If you still have linux-idg installed, show us your /etc/upnpd.conf file.

---

