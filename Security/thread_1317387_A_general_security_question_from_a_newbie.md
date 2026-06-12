---
title: "A general security question from a newbie"
date: 2009-11-06
forum: Security
---

### Post by Himself2007 on 2009-11-06
Hello

I heard once that Linux installed computers don't need security suite, anti-virus, firewalls,etc.
***[SIZE="3"][COLOR="Olive"]Is it true or a myth?[/COLOR][/SIZE]***
If true, can I consider myself safe as I have a router?

Luc[COLOR="Blue"][/COLOR]

---

### Post by BQAggie2006 on 2009-11-06
This is truth. Linux systems typically don't need an anti-virus program because there are few native Linux viruses out there, and even if you get one, they can't really do much damage because of the permission level the average user runs at. Most people that install anti-virus on a Linux machine do so to keep Windows viruses from residing on file and email servers.

As far as firewalls, it's only advisable to use a firewall if you have an internet facing machine running hosting services such as HTTP, FTP, SSH, etc.

What kind of router are you sitting behind?

---

### Post by Himself2007 on 2009-11-06
Hello BQAggie2006

It's a D-Link WBR1310.

Luc

---

### Post by BQAggie2006 on 2009-11-06
Then yes, you should be fine behind the router as it provides NAT and basic firewall capabilities.

---

### Post by Himself2007 on 2009-11-06
Thanks very much for these precisions!

Oh...what is NAT?

Luc

---

### Post by BQAggie2006 on 2009-11-06
NAT stands for Network Address Translation... basically it acts as a gateway between your public IP assigned by your ISP to your modem and the private IP network defined by your router. It translates requests from your private range into a request from your public IP so that external web services know where to send the requested information back to, and then will translate the response to your public IP into the private IP.

---

### Post by Aearenda on 2009-11-06
It sounds like you are safe.

I think it's useful to run anti-virus on a Linux machine only if it is a file server for a lot of unmanaged Windows machines, since it may trap viruses that they miss. 

In general, Linux systems don't need a firewall because they don't open unused ports on the network in the first place. For example, Windows always has file-sharing turned on, even if there are no shares, and needs a firewall to stop it, but Linux only opens file-sharing ports if Samba is installed and enabled (and then you'd be opening the firewall to those ports anyway). In fact, Linux always has latent firewall capability (managed using iptables), but the user interfaces that make it easier to understand and set up are not always installed (Ubuntu has ufw installed, but there are others like firestarter).

All of this depends on sensible user behaviour, of course - don't logon as root (it's disabled by default in Ubuntu), use 'sudo' with care, don't disable 'sudo', use strong passwords, and if you open ssh to the internet for remote management use an rsa key and passphrase not passwords.

---

### Post by cragtom on 2009-11-06
> **Himself2007 said:**
> Hello

I heard once that Linux installed computers don't need security suite, anti-virus, firewalls,etc.
***[SIZE=3][COLOR=Olive]Is it true or a myth?[/COLOR][/SIZE]***
If true, can I consider myself safe as I have a router?

Luc
Hi I am in the UK so I hope some of you know this I have a BT home hub 2 that  can have up to four wired and four wireless connections but this uses a Ethernet cable with the windows laptop on wireless could my desktop become infected???

---

### Post by scaine on 2009-11-06
> **cragtom said:**
> Hi I am in the UK so I hope some of you know this I have a BT home hub 2 that  can have up to four wired and four wireless connections but this uses a Ethernet cable with the windows laptop on wireless could my desktop become infected???

BT Homehub, to my knowledge, has no restrictions to how many wireless connections it allows.  The WEP key is generally written on the underside of the router and as long you type it into your wireless configuration box (on Ubuntu, Mac or Windows), you'll get connected.

It's not clear from your... sentence, whether you're connecting wirelessly, via ethernet (wired), or even if you're using Windows or Ubuntu?

If you're using Windows, make sure you have anti-virus and anti-malware suites installed, even behind a HomeHub router, as simply browsing certain web pages on most stock Windows installs could infect your PC (things are better on Vista and Win7, but I still wouldn't risk it).  If you're using an Ubuntu machine behind your HomeHub, you should be fine, provided you haven't messed with the HomeHub (opened ports) and installed server software on your desktop (like Apache web server for example).

---

### Post by cragtom on 2009-11-06
> **cragtom said:**
> Hi I am in the UK so I hope some of you know this I have a BT home hub 2 that  can have up to four wired and four wireless connections but this uses a Ethernet cable with the windows laptop on wireless could my desktop become infected???
Forgot to say desktop wired(ethernet) duel-boot vista and ubuntu(wubi) laptop with vista wireless using wep 2, both comps have anti-virus,anti spy-ware,ccleaner installed for windows vista but nothing for this comp when using linux

---

### Post by bodhi.zazen on 2009-11-06
You will get various answers from various people.

These things are tools and a better question is what are you wanting to do with them.

Certainly you may wish to use antivirus if you are running a mail or samba server.

Likewise firewalls are extremely helpful if you wish to limit access to servers, such as ssh ...

In general, the vast majority of Desktop users have no need for these tools, but that is not the same as saying they are useless or they have no role for some desktop users or servers.

Please see the stickies :

[Ubuntu Security - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=510812")

---

