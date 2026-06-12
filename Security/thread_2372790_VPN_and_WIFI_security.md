---
title: "VPN and WIFI security"
date: 2017-09-28
forum: Security
---

### Post by pointy2 on 2017-09-28
Recently, a horrid discovery was made that my Windows 10 laptop was deeply compromise by targeted attacks. After a new SSD with Ubuntu 16.04 (updated) installed, my concern is to keep the hacker away from my data and www usage.   As a road warrior, I do a lot of travel and utilize many hotspots along the way. I've looked into the VPN market and would like to know if these encrypt data from the modem, or only after it reaches the wireless router. As for my browser, Firefox 55.0.2 for Ubuntu is installed with several extentions as NoScript, HTTPS Everywhere, Ghostery, and a few others. I have heard of WireShark (to get a better understanding of network protocols) , but haven't installed it as of yet.   I have the firewall installed, as well as ClamTK. I can't seem to get the RKHunter installed and configured properly. Needless to say, I am of the (newly) paranoid (a known person is tracking my movements), after discovering the  malicious attacks on the pc.

---

### Post by TheFu on 2017-09-29
The most secure computer setup I know that still connects to the internet is a chromebook running ChromeOS.  It won't have much privacy, but security and privacy aren't the same things.

As for the VPN question - the answer is "it depends" - it depends on how YOU configure the VPN client and server.  If you run the VPN client on your laptop and connect to a VPN server "in the cloud" - preferably one that you manage and own, then it can be fairly secure.  This assumes the VPN server isn't using a cheap VPS that doesn't care about security at all.  Best to use a colocation setup with a dedicated server machine (not shared) and perhaps in a different country.  

If you use a paid VPN service, please be certain it is very reputable.  I would google for proof that the company has done what you desire.  There are a few companies that have withstood legal attempts to get access to traffic from state-nation requests.  However, those same companies tend to also block some of the most popular reasons for using a VPN service.

Also, someone with physical access to your machine for more than 10 seconds can place a beacon onto it that pings a system they control every few minutes, every hour, every day, every week, unless you fully encrypt the HDD and boot from media you have with you **ALWAYS**.  

OPSEC is hard, BTW.  If it isn't the PC, it is the smartphone.  Smartphones are 1000x easier to hack than a fairly secured PC.

---

### Post by pointy2 on 2017-09-30
Thank you for this reply, I'm happy to know that my uestion was coherant and understood, as I am now a student of computer security on the fast track. I've looked in to the VPN providers, and uickly came to realize that many are not sufficient for serious privacy and security. With that said, I've decided on one that will and can provide a piece of mind with their paid service. As a (potential) compromise, I have no real concern of any physical install of a beacon, since this is a new SSD with a fresh install. On the Win10 side, SpyBot has a good program called Anti-Beacon, that shuts down any of the communications from the pc to MS at least. How it works with spyware, is not known by me. Back to the Ubuntu topic.........  VPN and Tor seem to be the secure route at public wifi hotspots. As for phones, I've changed numbers and bought 4 phones during the course of 6 months, to avoid being stalked. I must have been incredibly blind to deceit, by not understanding that tracing a number to find the  geo location is the easiest of all spywares. Now, my attempt at forensics will hopefully be able to track the sender of maleware.

---

### Post by wildmanne39 on 2017-09-30
*Thread moved to **Security for better support**.*

---

### Post by patrikmellq on 2017-10-14
One old proven program that will show you if any one do anything with your computer - forget about root-kit hunter or any other program - i strongly recommend Tripwire to monitor your system - if you search the forum you will find a 100% complete guide how to install and tailor Tripwire to become best friend with your Ubuntu distro

I will explain what Tripwire does - Tripwire give all existing files on your system a key number sequence and save all does key values into a database - now if some one get into your computer and change any file then Tripwire will show you exactly that - Tripwire can not prevent intrusion but Tripwire can show that one intrusion has happen without the hacker or script-kid can hide there intrusion because you save the Tripwire Database Blue Print on a removable usb key - so they can not change the database as they can not reach it - with that solution you can feel safe checking your system and know if some one has made changes on your system

Another secure way to browse the web without a hacker to reach your computer using weak spots with softwares connecting to internet is FireJail
Firejail is software that run programs from a isolated box - so if some one find a weak spot with one of your program you connect to internet with - then they can not reach your Ubuntu system that way

Cheers

---

### Post by patrikmellq on 2017-10-15
@ TheFu thanks for recommendation using Chrome OS - i look at the security part and it work with better solution then firejail - i like it so much so i will try to install it on my laptop :-)

---

### Post by HermanAB on 2017-10-16
Hmm, since WPA2 is now officially broken, you should also consider setting up a socks proxy server to ensure that nobody shoulder surfs when you are connected over WiFi:

[http://www.aeronetworks.ca/2017/10/socks-proxy-setup.html](http://www.aeronetworks.ca/2017/10/socks-proxy-setup.html)

---

### Post by TheFu on 2017-10-16
> **patrikmellq said:**
> @ TheFu thanks for recommendation using Chrome OS - i look at the security part and it work with better solution then firejail - i like it so much so i will try to install it on my laptop :-)

ChromeOS that isn't on a Chromebook is NOT any more secure than a limited Ubuntu desktop.  It is the combination of both the SW and the HW that makes for the security.  Of course, privacy is almost non-existent.

Firejail is a neat tool.  I use it daily, but as with most things related to security, there are subtle considerations.  The same applies to HW-VMs, paravirtual-VMs, and containers.

I hear people asking about security believing that the TAILS distro is secure. It is easy to undo most of the security that TAILS provides, by making poor choices online.  Being anonymous online is very, very, hard.

---

### Post by inerstellar-cowboy on 2017-10-17
Google's sandbox solution is great, but it depends on how comfortable you are with being exposed to Google's all seeing eye. I wish you luck with your security

---

### Post by HermanAB on 2017-10-17
Well, when you run Linux, you don't need to be quite as paranoid as when you run Windows.  The difference being that Linux is secure out of the box.  You can make it insecure by installing random junk, but unlike Windows, it will be perfectly fine at first and it will remain fine if you are careful when you experiment with it.

While there are supposedly super secure versions like tails and chromeos and whatnot, they are not actually any better than any other newly installed Linux/BSD system and those special versions can be buggered up also, same as the others if you try hard enough.

So, why don't you just relax and enjoy your Ubuntu system?  You will be fine!

You should read this page, it largely applies to Linux too, since all share the majority of the same applications and all try to be secure out of the box:
[https://www.openbsd.org/security.html](https://www.openbsd.org/security.html)

---

### Post by pointy2 on 2017-10-20
> **patrikmellq said:**
> One old proven program that will show you if any one do anything with your computer - forget about root-kit hunter or any other program - i strongly recommend Tripwire to monitor your system - if you search the forum you will find a 100% complete guide how to install and tailor Tripwire to become best friend with your Ubuntu distro  I will explain what Tripwire does - Tripwire give all existing files on your system a key number sequence and save all does key values into a database - now if some one get into your computer and change any file then Tripwire will show you exactly that - Tripwire can not prevent intrusion but Tripwire can show that one intrusion has happen without the hacker or script-kid can hide there intrusion because you save the Tripwire Database Blue Print on a removable usb key - so they can not change the database as they can not reach it - with that solution you can feel safe checking your system and know if some one has made changes on your system  Another secure way to browse the web without a hacker to reach your computer using weak spots with softwares connecting to internet is FireJail Firejail is software that run programs from a isolated box - so if some one find a weak spot with one of your program you connect to internet with - then they can not reach your Ubuntu system that way  Cheers  Thanks for this recommendation. I have looked at FireJail and have read about TripWire, but have yet to install them on 16.04. They both seem promising for my (needs). My thoughts are not to install this software until I have ample time for the learning curve. Security (and privacy) is my #1 objective, and can't really see using anything Google related. I have a hard enough time thwarting a psycho stalker.....

---

### Post by pointy2 on 2017-10-20
> **HermanAB said:**
> Well, when you run Linux, you don't need to be quite as paranoid as when you run Windows.  The difference being that Linux is secure out of the box.  You can make it insecure by installing random junk, but unlike Windows.   So, why don't you just relax and enjoy your Ubuntu system?  You will be fine!  You should read this page, it largely applies to Linux too, since all share the majority of the same applications and all try to be secure out of the box: [https://www.openbsd.org/security.html](https://www.openbsd.org/security.html)  Yeah, Windows is super scary to me, now. I had a dual boot Win/Ubuntu installed on my Flex4, and have decided to re-scrub the SSD to do a full Ubuntu install, then run Win on Virtualbox. I need Win for the Adobe design programs.   "sit back and enjoy your new machine"....is what the tech guy told me upon reconfiguring it.

---

### Post by HermanAB on 2017-10-22
On Virtualbox, you can 'unplug' the network cable of the Windows VM.  Then you won't have security hassles there either.

---

### Post by pointy2 on 2017-11-05
....don't want Windows anywhere near my laptop. As for Ubuntu, I found a page on the forum that outlines some good security administration tools and tips. 
[https://help.ubuntu.com/community/Security](https://help.ubuntu.com/community/Security). I am looking in to hackintosh on usb or partition to run when needed.

---

