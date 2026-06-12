---
title: "I was hacked"
date: 2018-10-09
forum: Security
---

### Post by MikeCyber on 2018-10-09
Hi
someone has placed a rootkit/remote desktop via a old, rarely used website login based on a dictionary word. How has he done that? I only managed to boot from CD, changed passwords and still need to reinstall all os including bios...
Thanks and regards
ps is it normal to have a BCD folder in the system-reserved/Boot directory?

---

### Post by TheFu on 2018-10-09
Not enough facts to say anything.  Act like we are 12 and need proof.

---

### Post by MikeCyber on 2018-10-09
Return-Path: <Aaron@smith793.edu>
X-Originating-IP: [5.239.113.129]

That sounds bad. Many problems with that ip. I wont boot windows anymore but format all. Enough work for the next days and lost data...

---

### Post by TheFu on 2018-10-09
So, you don't want any help figuring out what might have happened by providing facts?

---

### Post by MikeCyber on 2018-10-09
i only boot from cd. i have no facts only that email askin to pay. read above ive asked how such can be done. bios and ubuntu is flickering because of rootkit

---

### Post by lisati on 2018-10-10
> **MikeCyber said:**
> That sounds bad. Many problems with that ip. I wont boot windows anymore but format all. Enough work for the next days and lost data...

A quick bit of research indicates that a device that has recently used that IP address has likely been compromised. Your best defense is to report incoming emails originating from that address to the relevant provider, and stay well clear of opening any attachments contained therein.

---

### Post by MikeCyber on 2018-10-10
Yes I was aware and never opened any unknown email attachments. That's why I'm surprised and wonder how he could place a rootkit only by knowing one of my old, simple web passwords. Is there a know vulnerability in 18.04?
Aargh wanted to delete MBR but deleted also partition table. Hopefully gparted can repair that...
Any help on how to flash the Bios on my Asus Z87Pro? Thanks

---

### Post by TheFu on 2018-11-08
Any system that isn't patched routinely will quickly become hackable.  In the last 12 months, there have been 2 remote access attack vectors to gain root that any linux system connected to the internet would be susceptible.   If you layer on an unpatched web server with a bonehead password, then it is just a little easier.

Once on the system, there are almost always methods to elevate to root.  Every OS has bugs.
Security of 18.04 is unproven.  Only time can provide any assurance for security.  18.04 replaced a few fundamental networking packages. Those new packages have a very short time in the world to prove their security unlike the prior packages which had years - some had decades - of avoiding attacks.

Don't forget that a careless admin can setup a system in a way that allows all sorts of non-admin users to gain higher privileges.  Strong file and directory permissions are central to Unix security, but a user and admin can override the defaults without consideration.  For example, web-admins often setup upload directories with 777 permissions, because it is easier than doing it right.

If you "only boot from cd" then the OS is out of date and unpatched.  That is fine for a client system, but not for a server.  For example, booting from a read-only CD to do online banking is the recommended method for CFOs worldwide. [https://krebsonsecurity.com/online-banking-best-practices-for-businesses/](https://krebsonsecurity.com/online-banking-best-practices-for-businesses/) But running a server is completely different.  Servers need multiple layers of security, constant monitoring, and versioned, automatic, backups so that once an incident happens, research in all the changes over time is possible.

I've been hacked 3 times now, since the early 1990s.  The last was in 2014 while at a security conference - they got in over bluetooth on a 100% patched system. I don't enable bluetooth on any devices anymore after doing more research. 
All the hacks were my failure to properly secure the system.  All of them.   A painter doesn't blame his brush after making an ugly portrait. It is frustrating, but hardly the brushes fault.

---

### Post by mcyber4 on 2018-11-13
Yes that monkey also hacked my Phone via Bluetooth. I've trashed both my old 50.-$ phone and 10y old monitor that I couldn't reset. Luckily my expensive TV doesn't have Bluetooth. I was hacked around 2000 twice on Windows and only last year twice on Ubuntu. Probably by the same baldie, stinky monkey.
Firewall and [LEFT]lynis are on my to do list. Looking around for some intrusion detection and trace apps but consider even chromebooks if they run Linux apps.

[/LEFT]

---

### Post by mcyber4 on 2018-11-17
I'm in the process of updating my 5y old PC and wonder if my cdrom could be hacked alike my Monitor? Something else? Basically I only want to keep my cdrom, casing and power supply. I've not yet tried my cdrom and powersupply, should be no risk I guess? Thanks

---

### Post by HermanAB on 2018-11-18
A default Ubuntu desktop isn't running any services, therefore hacking it over the network is almost impossible.

Some people get compromised by a script kiddie after installing VNC or Apache with a complex PHP application and a 4 letter password.  Real honest to goodness hacks are quite rare.

---

### Post by mcyber4 on 2018-11-18
I was hacked very professionaly. I'm surprised he took all the time to add a hidden partition, manipulated my monitor, changed my window/ubuntu boot etc.
Probably I've opened a support question attachment which downloaded a rootkit from a webserver with my weak Password.
Unfortunately I've reacted very stupidly by deleting the partition table...and couldn't restore all partitions as he seemed to have messed up Things. Hence no traceback this time.

---

### Post by mohicann on 2018-11-18
> **TheFu said:**
> All the hacks were my failure to properly secure the system.  All of them.   A painter doesn't blame his brush after making an ugly portrait. It is frustrating, but hardly the brushes fault.

Interesting, even if you were at a security conference (I mean this is more or less like if you were spied by the NSA or the CIA at an experimental stage). I agree that there is almost always ways to reduce the attack surface, and switching off bluetooth was one of them, but there are also strong attackers that have the keys of your computer even if it is fully patched. At some point, having only a kernel running on a computer is more or less unuseful. As I wrote on another topic, I've already seen a very sophisticated "rootkit kernel" (not a "kernel rootkit") installed on a updated Linux release (it was not my computer, it was something shown as a demonstration). It was very likely something designed by a spying agency (like some stuxnet samples that were still in the wild) sophisticated enough to let you doubt whether or not all this was a joke. This only way to observe its heart pulsing was to tap its connection outside of the computer and those who are skilled enough to reverse-engineer its kernel modifications are probably just a handful. It was detected by changing it with something out of the official releases (this kernel was apparently able to update itself with a newer version of itself, or just a renamed version of itself, in order to remain in place). Just to say that to some extent, there are attackers that will (almost) always be capable to break in, but fortunately these attackers only focused on privileged targets.

> **HermanAB said:**
> Some people get compromised by a script kiddie after installing VNC or  Apache with a complex PHP application and a 4 letter password.  Real  honest to goodness hacks are quite rare.

I wouldn't see script-kiddies at every corner... I shared [this link]("https://github.com/milabs/awesome-linux-rootkits") on another topic and we can wisely expect more in the wild. I would say that these tools, if used, are probably used more cautiously and that's probably why they are less detected. A Linux box can be hacked (or its user can be tricked), and tools to take a Linux box over exists, but their cost-effectiveness is low when it comes to bank credential theft and credit card trafficking (thus on a desktop machine). I tend to think that these tools on Linux are rather spying tools for specific targets than script-kiddies toys targeting the bulk of the users.

---

### Post by mcyber4 on 2018-11-19
Thanks for the interesting rootkit link.

---

### Post by HermanAB on 2018-11-20
When you have a Linux server on the public net, your logs will soon show SSH, VNC and Apache login attempts.  These are automated scripts that perps run, looking for stupidly configured machines to recruit for spam sending.

Once these annoying kids found your machine, you will typically get 10,000 login attempts per hour, continuously.  If you have a cool 4 letter password, then it is game over, pretty quickly.

---

### Post by mcyber4 on 2018-11-20
I don't have a server only desktop not always online! Seems to get even worse! This morning I found on my new Windows laptop a app called rempl. What is that?

---

### Post by mcyber4 on 2018-11-22
I've found hacked jpgs on some servers which probably are the cause. I'm quite surprised that they're crossplatform downloading and installing rootkit and trojans upon viewing, bypassing firewalls etc. on Windows and Linux.-
I've also found a local, hacked .psd but I don't think this time it was the culprit, as I didn't open/view that but only the remote jpgs.
Probably my next purchase will be a Chromebook...

---

### Post by mcyber4 on 2018-12-02
I tried many days to install Windows 8 with the old 18.10 live cd (infected) burnt on win10(infected).
Always got several, always different, weird files within system32 folder like for ex. a asusupdater.exe that comes with a original ms install cd?
I needed the intel network driver for win8 to update to 10 and remarked that they were modified at the download with my live cd. Not always and not always the same files within that zip.
Also that live cd formatted by putting the rootkit into a tiny section of the hd. So I drove one hour to a big kiosk and was prepared to buy any bootable CD and felt relief when I saw a magazine with a 18.10 dvd.
So with the new live disk I found about the hds and that I couldn't fully format those anymore. I've trashed two usb sticks and send to warranty repair my new laptop. All those discs could not be fully formatted.-

So now with the newly bought live cd I now try to format my 1TB SSD and it says for ext4 used 2GB! But for ex. btrfs only 128kb used. That smacks hacked, could that really be such a difference?
Also shutting down the live cd returns i/o errors for splashfs and sr0. Is that a normal bug? Thanks.

That rootkit is very hard to find and duplicates fast in many different ways. Would be such a sad day to see this slide into Ubuntu...

So back to another trial to install Win8.

---

### Post by freemedia2018 on 2018-12-02
> **TheFu said:**
> I don't enable bluetooth on any devices anymore after doing more research. 

I typically remove the bluetooth device from my laptop. Wifi goes with it. If I need wifi (rare indeed) they make external devices. 

Never was a major fan of the technology.

---

### Post by mcyber4 on 2018-12-02
Installed win8 but it still looks weird to me. Is this normal as on the pictures?
REMOTE wan optimizing...I've had my share of remote. :cry:

---

### Post by mcyber4 on 2018-12-03
more weirdness...:cry:
that partition is only visible in Ubuntu but not Win10

---

