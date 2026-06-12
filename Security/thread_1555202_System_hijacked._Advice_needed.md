---
title: "System hijacked. Advice needed"
date: 2010-08-17
forum: Security
---

### Post by Firejack on 2010-08-17
Hello all,
I have a media server setup running Ubuntu 10.04 LTS, XBMC 9.11 and TVheadend 2.11. Up until a few weeks ago it had been running fine. Recently I've had issue like terminals open for no reason and then firefox when I've connected via VNC. Tonight I've been looking through the history in Firefox and since mid July there are lots of websites that have been visited that I cannot explain. Download sites like Rapidshare, credit card sites, porn sites and various speed test sites like speedtest.net.

Now there is absolutely no chance anyone has visited those sites in my house. There hasn't been a mouse or keyboard installed for months! My machine is the only one with VNC installed and its password protected.

Checking my router log its flooded with DoS attack messages and port scans. Most worryingly a UPnP rule has been configured on my router to allow TCP port 5900 to be forwarded to my media server. So I guess someone has been using VNC to login to that machine. Unfortunately I didn't have a password on VNC as I didn't think it was accessible ](*,)

So what do I do now? How can I work out who has been using my computer over VNC and for what? How do I find out how they got access in the first place? How to do stop them?

I've disabled UPnP for the time being on my router.

Thanks all!

---

### Post by FuturePilot on 2010-08-17
1) If you used System > Preferences > Remote Desktop and checked the box "Configure network automatically to accept connections" it will use UPNP to create a forward.

2) Take the computer off line immediately, image it so you can inspect the image later, and reinstall.

---

### Post by cariboo on 2010-08-17
+1, vnc/remote desktop, is one of the number one ways to get your system hacked. Even if you are running a remote desktop client/server internally, a strong password is always a must.

I run XBMC Live, there are no extra programs installed, but what is needed to run XBMC. There is no DE installed, so there is no need for vnc. I use ssh with private/public keys to access the computer if any maintenance is needed after the initial setup.

---

### Post by cdenley on 2010-08-18
As far as I know, Vino (Remote Desktop) does no logging, so there is no chance for you to determine what IP's they were connecting from. It probably wouldn't help you anyway, as most would probably be from other systems like yours which were themselves compromised. You can't really know for sure everything your attackers may have done to your system, so the only safe thing to do is to reformat and start fresh.

---

### Post by Grenage on 2010-08-18
> **Firejack said:**
> So what do I do now? How can I work out who has been using my computer over VNC and for what? How do I find out how they got access in the first place? How to do stop them?

I've disabled UPnP for the time being on my router.

Your computer was most likely compromised by a bot, which systematically scans IP address blocks and looks for VNC servers.  If successful, the bot will attempt to install software, or configure your machine to act as a relay/bot.

uPnP rules are automatically created by the service, that's it's purpose.

Don't bother trying to find out where the attack came from, it will probably be another compromised home machine, sitting in Chinese basement.

Reinstall the OS, unless you're confident enough that you've cleaned it thoroughly (reinstall the OS).  If you must use VNC, use a non-standard port, and use the mother of all passwords.  SSH is preferable, especially with a key.

---

### Post by movieman on 2010-08-18
> **Grenage said:**
> uPnP rules are automatically created by the service, that's it's purpose.

UPnP NAT Traversal is one of the worst ideas ever, precisely because so many people do end up opening routes through their router without even realising. Anyone who actually needs to run a server that's Internet-accessible should be competent enough to figure out how to forward the port through their router.

---

### Post by Grenage on 2010-08-18
> **movieman said:**
> UPnP NAT Traversal is one of the worst ideas ever, precisely because so many people do end up opening routes through their router without even realising. Anyone who actually needs to run a server that's Internet-accessible should be competent enough to figure out how to forward the port through their router.

I couldn't agree more, but practicality usually wins.  The average MSN user doesn't want to read up on IP systems, just so they can receive a file.

---

### Post by FuturePilot on 2010-08-18
> **movieman said:**
> [s]upnp[/s] NAT [s]traversal[/s] is one of the worst ideas ever

FTfY ;)

---

### Post by uRock on 2010-08-18
Imagine how many systems would be compromised without NAT.

---

### Post by Firejack on 2010-08-18
> **FuturePilot said:**
> 1) If you used System > Preferences >  Remote Desktop and checked the box "Configure network automatically to  accept connections" it will use UPNP to create a forward.Gah this looks my undoing. The account I created when I installed Ubuntu had the Configure option off. On the user I was using day to day for media playback/internet browsing, this option is on. Strange I would of thought unchecking on the account with Administrator rights would of disabled this too.
In some ways this is good news. Since they were on a standard desktop user account it really limits their access. Is it safe to assume my media servers integrity is intact and its just that one user account I should remove to secure my system again?

> **FuturePilot said:**
> 2) Take the computer off line immediately, image it so you can inspect the image later, and reinstall.Network cable is already unplugged. I have no urgent need to reinstall right away. Want to double check what has happened first.

> **cdenley said:**
> As far as I know, Vino (Remote Desktop) does no logging, Dammit. Any other logs I should check? Knowing when my system was hacked will give me a smaller time frame to search for possible problems.

I looked in my bash history in my home folder and there doesn't appear to be much beyond basic commands in their. Anyone way to check they didn't access my sudo password. I guess failed sudo passwords are logged somewhere?

Also checking through my UPnP port mapping history a bit more I've noticed one strange port to a Windows workstation I have here. Its forwarding TCP+UDP 4556 to the Windows machine. Seems a bit strange.

Ah ha.. Just found out what the file was uploaded/downloaded from Rapidshare, KnD.exe . Stored several times in different folders. Will scan that in a bit and find out what it is.

Thanks for the input everyone :)

---

### Post by FuturePilot on 2010-08-18
> **uRock said:**
> Imagine how many systems would be compromised without NAT.

NAT was never intended to be a firewall. The fact that it acts as one is a side effect of the way that it is designed. IPv6 has done away with NAT. NAT breaks too many things and it's the reason we have UPNP NAT traversal in the first place.

---

### Post by cdenley on 2010-08-18
> **Firejack said:**
> Since they were on a standard desktop user account it really limits their access. Is it safe to assume my media servers integrity is intact and its just that one user account I should remove to secure my system again?

Not Really. Privilege escalation vulnerabilities are a bit common. Some script kiddy wouldn't have been able to get root, but if they knew what they were doing, it is certainly possible. Allowing attackers to have shell access to any account, regardless of how unprivileged, removes any guarantee that your system is safe.
> **Firejack said:**
> 
Dammit. Any other logs I should check? Knowing when my system was hacked will give me a smaller time frame to search for possible problems.

You can check /var/log/auth.log. The absence of suspicious events in the logs in no way means your system is clean. If an attacker knows what they are doing, they will cover their tracks.

---

### Post by uRock on 2010-08-18
> **FuturePilot said:**
> NAT was never intended to be a firewall. The fact that it acts as one is a side effect of the way that it is designed. IPv6 has done away with NAT. NAT breaks too many things and it's the reason we have UPNP NAT traversal in the first place.
Trust me, I know why it was made, but it does end up saving some people from themselves. I wish IPv6 was better covered in the Cisco CCNA classes.

---

### Post by endotherm on 2010-08-18
> **FuturePilot said:**
> NAT was never intended to be a firewall. The fact that it acts as one is a side effect of the way that it is designed. IPv6 has done away with NAT. NAT breaks too many things and it's the reason we have UPNP NAT traversal in the first place.
but remember NAT and Stateful Packet Inspection go hand-in-hand. we won't be abandoning SPI firewalling regardless of IP version, so I imagine we will have NAT like approaches for a very long time coming.

URock: its been widely noted that much of where IPv6 is failing, is on the human side. no one understands it as well as they should. the problem is it wasn;'t made for humans to workwith like v4. imagine typing in:
```
ping 2001:0db8:3c4d:0015:0000:0000:abcd:ef12 
```not gonna happen.

lastly, op, backup and rebuild.

---

### Post by alphaamanitin on 2010-08-18
Please update with more info, if it comes along.  These types of threads are pertinent to my interests as I am starting my first attempt at a home server.  I am using FreeNAS but reading these makes you think and thinking is always good.

AlphaA

---

### Post by Firejack on 2010-08-18
/var/log/auth.log and auth.log.1 only go back around 10 days. Can't see anything suspicious in that period.

The *.exe file is identified as Spyware.ADH, IRC_ZAPCHAST.AB, Obfustat.TED.


Right then. Think I'm reasonably happy no real harm was done to my media server. Anything else I need to do before re-formatting? Apart from backup of course.

---

### Post by mr-woof on 2010-08-18
I'm still a bit confused on how they got in to your system, did you have any ports forwarded to the media box?

---

### Post by cdenley on 2010-08-18
> **mr-woof said:**
> I'm still a bit confused on how they got in to your system, did you have any ports forwarded to the media box?

UPnP creates port forward rules on the router. He checked the box in "Remote Desktop" which does this.

---

### Post by gradinaruvasile on 2010-08-18
You can also use x11vnc - it can be launched to listen on localhost only and use ssh forwarding (with a client like Remmina). You can even log in through it. The built in remote desktop is crap.

---

### Post by mr-woof on 2010-08-18
so if you have upnp ticked on your router and have no ports forwarded, someone can connect to the router from the outside and create a rule?

---

### Post by rookcifer on 2010-08-18
OP, live and learn.  Don't use VNC, use SSH with key authentication instead.

The Ubuntu security devs seriously need to look at this whole VNC issue.  Really, they do.

---

### Post by bodhi.zazen on 2010-08-18
> **mr-woof said:**
> so if you have upnp ticked on your router and have no ports forwarded, someone can connect to the router from the outside and create a rule?

Yep, that is what UPNP is

[http://en.wikipedia.org/wiki/Universal_Plug_and_Play](http://en.wikipedia.org/wiki/Universal_Plug_and_Play)

So if you enable it on your router, you are allowing traffic through your router.

The balance of power must be maintained, security vs convenience.

---

### Post by mr-woof on 2010-08-18
well bleeding hell, I didn't know that. Learn something new everyday :)

Out of interest, say it was enabled how would you connect to it, via a webpage?

---

### Post by FuturePilot on 2010-08-18
> **mr-woof said:**
> well bleeding hell, I didn't know that. Learn something new everyday :)

Out of interest, say it was enabled how would you connect to it, via a webpage?

With a VNC client.

---

### Post by uRock on 2010-08-18
Linksys systems are nice enough to have UPnP enabled, but only a few clicks to disable it. You would think they would have the default with it being disabled, but then non-technical people would be lost when their apps don't work.

---

### Post by OpSecShellshock on 2010-08-18
> **uRock said:**
> Linksys systems are nice enough to have UPnP enabled, but only a few clicks to disable it. You would think they would have the default with it being disabled, but then non-technical people would be lost when their apps don't work.

Which is weird, because I have perfectly functional day-to-day internet use without UPnP and without any ports forwarded.

---

### Post by bodhi.zazen on 2010-08-18
> **uRock said:**
> Linksys systems are nice enough to have UPnP enabled, but only a few clicks to disable it. You would think they would have the default with it being disabled, but then non-technical people would be lost when their apps don't work.

And it is some of the very same people who wonder why their computer / internet connection is soooo s   l   o   w 

:lolflag:

---

### Post by uRock on 2010-08-18
> **OpSecShellshock said:**
> Which is weird, because I have perfectly functional day-to-day internet use without UPnP and without any ports forwarded.
I had never looked into it before to see what it was. Now we are watching to see that everything works, especially when we boot Windows.
> 
And it is some of the very same people who wonder why their computer / internet connection is soooo s   l   o   w 
With UPnP enabled or blocked?

---

### Post by bodhi.zazen on 2010-08-18
> **uRock said:**
> I had never looked into it before to see what it was. Now we are watching to see that everything works, especially when we boot Windows.

With UPnP enabled or blocked?

People who are lax with security, UPNP or otherwise.

---

### Post by endotherm on 2010-08-18
> **rookcifer said:**
> OP, live and learn.  Don't use VNC, use SSH with key authentication instead.

The Ubuntu security devs seriously need to look at this whole VNC issue.  Really, they do.
a lot of the issue with exposing vnc to teh intarweb, is it's 8 char passwd limit. I agree keys are a better bet than passwords, but even a distributed bruteforce attack would have trouble with a 24 char 4-factor passwd. 

upnp is a risk under even the best set of circumstances, simply because it changes critical configuration without warning or visibility.

URock: upnp shouldn't have anything impact on normal web use. its a framework that allows a client application inside the LAN, to open a port on the firewall dynamically. that way, if you were configuring a bittorrent client, you could just fire it up, without reconfiguring you router to open a port.

---

### Post by uRock on 2010-08-18
> **endotherm said:**
> URock: upnp shouldn't have anything impact on normal web use. its a framework that allows a client application inside the LAN, to open a port on the firewall dynamically. that way, if you were configuring a bittorrent client, you could just fire it up, without reconfiguring you router to open a port.
Thanks for the info. I am anti-torrent, so I don't mind giving the neighborhood thieves one more hurdle to jump if they want to use my network.

---

### Post by mr-woof on 2010-08-18
This is what I thought upnp was for, I didn't realise it could be accessed from the outside interface by firing a vnc client at it. Are they other clients etc that can access it from outside?

---

### Post by alphaamanitin on 2010-08-18
So what would happen to things like my online gaming, chatting, etc if I disabled UPnP on my router?  Would I even notice anything?  And does have a password protected network help?  I have never heard of this before.  Sorry I am kind of hijacking the thread.

AlphaA

---

### Post by noway2 on 2010-08-18
Yesterday I was messing around with using my laptop as a bridge to the wireless Internet access for the Xbox, just for fun.  I established the connection and ran a connectivity test.  The xbox indicated that the firewall settings are "moderate" and suggested that I reset the router.  I admit that I had to look up the meaning of "moderate".  

The search results took me to an MS page that had some troubleshooting tips:
Of course number one was reboot the router.  Number two was turn on uPnP.  Yeah right, sure, uhuh.  

Makes me wonder how many systems get compromised because someone wants to play something on xbox live.

To the OP: if you are curious at all, you could use this machine as a learning experience to investigate with.  I would suggest starting withe the CERT check list which will run you through a number of checks regarding processes, users, and other pieces of information.  At the very least you will learn something about how Linux works.

---

### Post by uRock on 2010-08-18
> **alphaamanitin said:**
> So what would happen to things like my online gaming, chatting, etc if I disabled UPnP on my router?  Would I even notice anything?  And does have a password protected network help?  I have never heard of this before.  Sorry I am kind of hijacking the thread.

AlphaA
I'd say give it a try and see what happens. If it has a negative effect, then enabling UPnP would only take a few minutes.

---

### Post by uRock on 2010-08-18
> **noway2 said:**
> Yesterday I was messing around with using my laptop as a bridge to the wireless Internet access for the Xbox, just for fun.  I established the connection and ran a connectivity test.  The xbox indicated that the firewall settings are "moderate" and suggested that I reset the router.  I admit that I had to look up the meaning of "moderate".  

The search results took me to an MS page that had some troubleshooting tips:
Of course number one was reboot the router.  Number two was turn on uPnP.  Yeah right, sure, uhuh.  

Makes me wonder how many systems get compromised because someone wants to play something on xbox live.

To the OP: if you are curious at all, you could use this machine as a learning experience to investigate with.  I would suggest starting withe the CERT check list which will run you through a number of checks regarding processes, users, and other pieces of information.  At the very least you will learn something about how Linux works.
In my Cisco router there is a whole section on opening ports for gaming and/or regulating them to certain sites and which local host will be allowed to connect with those capabilities. This may be more work than it is worth, but if it protects the rest of the network, then all is fine, IMO.

---

### Post by mastablasta on 2010-08-19
UPnP - Having it off means slow or no torrent = no file sharing.

---

### Post by Grenage on 2010-08-19
> **mastablasta said:**
> UPnP - Having it off means slow or no torrent = no file sharing.

Unless you manually forward the port range configured in the torrent app - which you would, if not using uPnP.

---

### Post by CharlesA on 2010-08-19
> **OpSecShellshock said:**
> Which is weird, because I have perfectly functional day-to-day internet use without UPnP and without any ports forwarded.

Same here, but then I don't normally use torrents. That said, when I do use them, I haven't had any problems.

> **bodhi.zazen said:**
> People who are lax with security, UPNP or otherwise.

+1.

> **alphaamanitin said:**
> So what would happen to things like my online gaming, chatting, etc if I disabled UPnP on my router?  Would I even notice anything?  And does have a password protected network help?  I have never heard of this before.  Sorry I am kind of hijacking the thread.

AlphaA

Probably nothing. I used to screw around with UPNP and port forwarding ages ago when I had a piece of garbage router, but now I only have 1 port forwarded and that's to SSH to my server. Online gaming isn't affected.

> **mastablasta said:**
> UPnP - Having it off means slow or no torrent = no file sharing.

Works fine for me for torrents.. *shrug*

I'll leave it disabled. ;)

---

### Post by endotherm on 2010-08-19
> **alphaamanitin said:**
> So what would happen to things like my online gaming, chatting, etc if I disabled UPnP on my router?  Would I even notice anything?  And does have a password protected network help?  I have never heard of this before.  Sorry I am kind of hijacking the thread.

AlphaA

upnp is only really for apps/protocols that require a server port for recieving unsolicited connections, or "connectionless" streams. bittorrent uses them so that remote peers can connect to you to get file peices. some video conferencing software requires UDP streams incomming, and most lan-play games require a port, at least on the game host box. 

the easiest way to tell if a given application is using upnp to open ports, is to look at it;s setup instructions. if they tell you to configure your router, then it likely does.

keep in mind, almost nothing actually REQUIRES upnp. upnp is just a mechanism for apps to automatically configure your router, so if you just do the configuration yourself, everything will generally work just as well as if upnp was enabled and in use. the exception to this, is apps that open random ports at runtime (transmission has such a feature). since you never know what port it will use beforehand, you can't pre-configure for it.

---

