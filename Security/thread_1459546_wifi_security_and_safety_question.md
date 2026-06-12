---
title: "wifi security and safety question"
date: 2010-04-21
forum: Security
---

### Post by jj97403 on 2010-04-21
I've been using Ubuntu for several years, but I am a basic computer user with very little understanding of computers.  Ubuntu is so easy and user friendly now, that even somebody like me can use it effortlessly.

Anyway, can anybody explain to me, or refer me to a web site, that explains to a non-technical user if using Ubuntu in public wifi hotspots (Starbucks, Public Library) is any safer than using Windows?

I know it is not safe to use public wifi, but what I'd like to know is Ubuntu safer than Windows, and if so, is it significantly or negligibly safer?  

I've always had the impression (belief) that maybe one of the dangers with public wifi is a hacker could see see "what I see on my own computer screen," and that is one of the ways passwords and data get stolen.  If that is true, does using Ubuntu guard against this threat because a hacker is less likely to hack into an Ubuntu machine, or does this even matter to a hacker?

In short, I have no choice but to do internet-banking and transactions over wifi hotspots, and I wonder if using Linux is somehow safer?  Any insight would be great, and I hope I posted this correctly.  Thanks.

---

### Post by HermanAB on 2010-04-21
Yes Ubuntu is usually safer, because it is very difficult to subvert it with a malicious program.

In terms of WiFi snooping - Linux is technically just as insecure as Windows when you only consider WiFi snooping and ignore all the other insecurities of Windows.

When using Email, always use services that are protected with the Secure Sockets Layer (HTTPS), such as Google Mail.  All bank sites are protected with HTTPS as well.  In general, a protocol name with a 'S' in it is SSL and therefore safe.

So, provided that you avoid dumb ISP webmail like Shaw, Telus, Yahoo and Microsoft mail services, you should be OK.

---

### Post by Helkaluin on 2010-04-21
Public wifi is just that: public. Even if you are accessing via HTTPS it still takes but a simple packet sniffer to know what provider are you using by looking up what IPs you are connecting to. If you are surfing unencrypted traffic than assume every bit of track (in laymen terms: specifically what site you are visiting) can be seen by anyone within wifi broadcast coverage.

Even with HTTPS, be sure that you review the SSL certificate of the website before proceeding. A clear warning is that if you receive a 'Untrusted certificate' warning or similar when you attempt to log in: it is, to say the least, easy to forge such a fake SSL certificate and, if the user chooses to accept such a certificate when connecting, all encrypted traffic could be tunnelled to the attacker in what we call a Man-in-the-middle attack. In such a scenario, given the user accepts the forged certificate, the encrypted traffic can be seen.

In short, keep your eyes open.

---

### Post by 2hot6ft2 on 2010-04-21
The only way to be relatively secure using a public wifi is to tunnel with something like SSH. Otherwise anyone that knows how (and many people do) can do a MITM (Man In The Middle) attack and see everything you do. That was why I looked into and then did the Secure remote desktop how to in my sig. below.

Once I log onto a wifi connection away from home I can create the secure tunnel and do whatever I want to. While given enough time and talent someone "may" be able to gain access to the info. transmitted and received most will just move on to an easier target.

Who wants to spend months or years trying to decrypt something (just to find out it's useless) when they can get something right away that's not encrypted.

---

### Post by OpSecShellshock on 2010-04-21
Remember also that public wi-fi is going to give greater priority to compatibility with as many devices as possible, which means that encryption between your computer and the access point will most likely be either disabled or weak. Oh, and you can't really count on the dns not having been messed with. In that sense, there are risks which are entirely out of your control that have nothing to do with your OS.

---

### Post by Jive Turkey on 2010-04-25
ssh tunneling might be the safest way to go.  It would require that you have an ssh server running on a machine somewhere with either a static ip address or a dynamic dns service.  You could then either do x11 forwarding of the browser itself, or tunnel the traffic through somehow, similar to a proxy.  VPNs are another option but I have yet to find one that works worth a damn for me.

---

### Post by CharlesA on 2010-04-25
You can set up a SOCKS proxy to tunnel all browswer traffic thru the SSH tunnel.

---

### Post by bodhi.zazen on 2010-04-26
> **jj97403 said:**
> Anyway, can anybody explain to me, or refer me to a web site, that explains to a non-technical user if using Ubuntu in public wifi hotspots (Starbucks, Public Library) is any safer than using Windows?

Define "safe".

On a public network, wifi, I would assume your network traffic is monitored. This has nothing to do with what OS you are running and everything to do with the fact that such a network is open or public so anyone can put a packet sniffer on it.

In terms of "safe" it depends on your habits as a user. You can secure firefox and browse with safe habits, again this is also OS independent - NoScript runs on both LInux and Windows and is just as important on both OS, IMO.

In terms of "safe" in that other people can break into your box, by default there are no listening servers and IMO Ubuntu out of the box is more secure then a hardened installation of Windows.

I suggest you read the security sticky at the top of these forums.

---

