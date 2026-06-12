---
title: "I'm pretty sure I've been hacked. Any information would be helpful."
date: 2017-12-18
forum: Security
---

### Post by lukmoumar on 2017-12-18
I recently registered a domain name and had it point to a server on my home network.

 I thought it would be an easier way to share things with family and friends. And I would often disconnect the machine entirely unless someone needed it. 

I did do the normal and easier things to make it secure, but I still think it would have been a cakewalk if someone really wanted access. 

Now I have several reasons to believe someone has been accessing my network. I've received notifications for hijacking/unauthorized/etc. 

Last night I noticed all of the computers were all processing at a high rate. I couldn't even browse the internet and things were not...normal?. It seemed like a mitm attack. I also got a notification on an Android phone of an attempt at "hijacking." I checked system monitor and immediately noticed that there were 10 instances of things running when I normally saw one. And it was like that on every machine, and on seemimgly unrelated applications. I thought for a moment them pulled the plug on the cable modem and CPU usage went to 90- 100% and stayed there until finally I unplugged everything. 

Now, I'm using my unrooted Android to post. Over cell service. 

Im confident that I can reinstall/wipe/virus scan my files OS's. Ive got some burned disks of live recovery/live USB stuff. 

What else can I do? I have heard that it's possible to infect the firmware/hardware. I've also got a bunch of Android phones, IoT stuff etc. I'm going to obtain the firmware and flash bios/anything I can. On the Android's that were rooted, I was going to flash the stock ROMs on them, or trash them if I didn't have any easy option to install working ROMs on the others. Also have a smart TV etc. I was going to flash the firmware on the router, but what about the cable modem I rent from my isp?

I am happy that I'm doing this now before completing several projects. I'm certainly going to spend more time setting up security protocols in the future. 

Any help/guidance/thoughts would be very much appreciated. 

Thank you

---

### Post by vasa1 on 2017-12-18
Is your problem related to any official flavor of Ubuntu?

---

### Post by Habitual on 2017-12-18
Router and Wifi Security come to mind. weak passwords?
Shared or guessable passwords.

Not enough particulars to make a detailed assessment.
Reasons aren't evidence.
Good Luck. Try the [Ubuntu Security]("https://ubuntuforums.org/showthread.php?t=510812") mega-thread.

---

### Post by anontrust on 2017-12-19
> **Habitual said:**
> Router and Wifi Security come to mind. weak passwords?
Shared or guessable passwords.

Not enough particulars to make a detailed assessment.
Reasons aren't evidence.
Good Luck. Try the [Ubuntu Security]("https://ubuntuforums.org/showthread.php?t=510812") mega-thread.

the ubuntu security thread is awesome, but some link are outdated or missing, sould be nice if someone could update it

---

### Post by TheFu on 2017-12-29
You never said what "service" was being used on the server or any of the steps taken to protect it.

IoT is a joke when it comes to security.  I keep those things on a "guest" subnet here.  They aren't allowed on any subnets with real computers.  Android is worse.  It cannot be secured and as soon as 1 3rd party app is installed, all bets are completely off.  Keep it on the "likely hacked" subnet.

If you have non-technical people with laptops/desktops, they need their own subnet too.  The point of this is to keep them away from the more dangerous IoT and android devices, but not allow them access to your more secured systems.

Then you need an internet server subnet. This needs to be firewalled off from everything else, to prevent hacked servers from having free range on the other subnets of your home.  It needs to be patched weekly, backed up daily with versioned backups, and any public facing services need to have access locked down to only those clients that need access.  Using a VPN for any dangerous services is highly recommended too.  Of course, I'd never allow any Windows systems direct internet access, but that's me. I don't think I can secure Windows and I don't believe anyone else can, including MSFT.

The subnetting needs to be managed by network equipment.  Don't trust vlans.  Those are just suggestions, not real security.

For a home user, only 2 services should be available on the public interfaces.  
a) ssh, with firewall locks down to only those places where you KNOW you will be.  Add fail2ban and never, ever, ever, use passwords for access, only ssh-keys.  With ssh, you can have pretty much any access needed from anywhere in the world, including remote desktops, remote file systems, remote file transfers, SOCKS proxy, and server management. ssh does about 50 other things too.
b) VPN (openvpn or libreSwan).  libreswan is likely more secure than openvpn. That is opinion, not a proven fact, yet.  Full VPNs are better for non-technical people and limited devices.

I've learned to never let any php webapps generally available on the internet over the years.  At the last company where I worked, that was corporate policy.  If we needed a php webapp, then access to it required full vpn connectivity.  I trusted the security team there. They were very smart about limiting risks to our systems.

Security is always a moving target.  In general, don't allow access to anything for people who don't need access. Use multiple layers to secure any asset.  Never trust just 1 layer to work.  Test the security.  Versioned backups are by far my best security technique.  With 120 days of daily backups, it is possible to see which files change from day to day.

---

