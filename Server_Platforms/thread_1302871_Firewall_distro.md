---
title: "Firewall distro"
date: 2009-10-27
forum: Server Platforms
---

### Post by TheGameAh on 2009-10-27
I've dabbled a bit in Endian, but that was a year ago, and was looking for some opinions on some other firewall type distros.

Basically, I'm looking for a firewall distro that can handle typical firewall functions, as well as possibly VPN connectivity (Radius support would be a plus, in order to use existing names and passwords)

I'm trying to replace our internal Microsoft RRAS server (which I hate).  Was hoping to maybe move that function to the firewall itself.

---

### Post by scorp123 on 2009-10-27
pfSense
[http://www.pfsense.com/](http://www.pfsense.com/)

It's based on FreeBSD. Performs extremely well, even on micro ITX, Soecris and similar small form-factor hardware. And it has a easy-to-use web GUI.

---

### Post by Adina on 2009-10-27
> **scorp123 said:**
> pfSense
[http://www.pfsense.com/](http://www.pfsense.com/)

It's based on FreeBSD. Performs extremely well, even on micro ITX, Soecris and similar small form-factor hardware. And it has a easy-to-use web GUI.

what he said. And M0n0wall which I believe is made by the same people as pfsense. I have tried both and I'm currently using m0n0wall and I think It's great, very easy to set up and configure and very stable. If you want a distro that's linux you should try zeroshell.

---

### Post by Iowan on 2009-10-27
I downloaded a copy of Smoothwall, but haven't installed it anywhere yet.  pfSense does sound interesting.

---

### Post by druhboruch on 2009-10-27
IPCop works very well for me.

---

### Post by scorp123 on 2009-10-27
> **Iowan said:**
> I downloaded a copy of Smoothwall SmoothWall is rather limited. e.g. last time I took a look there was no way of editing your own custom rules for outgoing traffic. The default was that all outgoing traffic was always allowed ... and that's it.

pfSense, m0n0wall and ZeroShell give you way way more control over your network.

---

### Post by windependence on 2009-10-27
+3 for pfsense. I even have some fairly large customers using it as a gateway box. You can install squid right from the web GUI and filter internet use also. Very nice.

-Tim

---

### Post by fastiopt on 2009-10-27
I'm using ClarkConnect. It works very well for me! i don't know about the RADIUS support, but you can configure vpn connectivity very easily ;)

I think it's worth a look!

---

### Post by dmizer on 2009-10-27
Here's one based on Ubuntu: [http://ebox-platform.com/](http://ebox-platform.com/)

I also use ClarkConnect, but I'm considering a move to ebox. I've also used [Untangle](http://www.untangle.com/) which had a fantastic interface and loads of well written wiki articles.

---

### Post by Sporkman on 2009-10-27
To round this out, here's a distrowatch list:

[http://distrowatch.com/search.php?category=Firewall&origin=All&basedon=All&desktop=All&architecture=All&status=Active](http://distrowatch.com/search.php?category=Firewall&origin=All&basedon=All&desktop=All&architecture=All&status=Active)

---

### Post by HaOsLsE on 2009-10-28
Nice...some good replies here... I knew of a few of these.  I was just gonna look into another myself and was browsing around I've been on pfSense for a couple years now.  It is stable and easy to build.  I use them for the company I work for too...I guess I've built around 50 of them.  Simple, good support, and has all the features I need.

I guess I'm bored a bit and want to look at something linux based to install on one server I'm having returned to me that I don't use anymore.  Seems fun to build a decent linux box out of it....well to some of us...this is fun.  :)

****EDIT****
I Just looked at that EBOX...that package looks sweet!! Think that may be for me!! Thanks! LoL...probably will load it tonight.

---

### Post by Lars Noodén on 2009-10-28
> **HaOsLsE said:**
> Nice...some good replies here... I knew of a few of these.  I was just gonna look into another myself and was browsing around I've been on pfSense for a couple years now.  It is stable and easy to build.  I use them for the company I work for too...I guess I've built around 50 of them.  Simple, good support, and has all the features I need.

I guess I'm bored a bit and want to look at something linux based to install on one server I'm having returned to me that I don't use anymore.  Seems fun to build a decent linux box out of it....well to some of us...this is fun.  :)

@ HaOsLsE : you can figure out what you want in the router or firewall, beyond iptables, and then roll it into [busybox](http://linux.die.net/man/1/busybox).

---

### Post by TheGameAh on 2009-10-28
Thanks guys, a lot of good data here.  I'm playing with pfSense in a Virtualbox session now.  Solid stuff, almost overwhelming the amount of features it has.

Having some trouble setting up a VPN server, but I'll keep playing.

I'm looking for one specific feature for sure in a firewall distro, but it might not be possible.  We use Active Directory (shudder) for authentication, as most of our machines are Windows.  We use RRAS, tied into a radius server, so it's all the same password.

Can the VPN side on the firewall tie into this AD Radius server, so that when users log in, it's their familiar username/password?

---

