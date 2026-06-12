---
title: "stopping PING response"
date: 2008-12-21
forum: Security
---

### Post by nss0000 on 2008-12-21
Gents:

Running x64HH_8.04.1 fully patched.

I'm trying to stop my system from responding to WWW <PING> query. This evidently cannot be done from the GUFW firewall interface.

SO:  I have made a recommended entry in /etc/sysctl.conf:

             net.ipv4.icmp_echo_ignore_all=1

But, the Gibson SHIELDS-UP site still claims my system responds to <PING>.
Where have I gone (not even?) wrong ?

---

### Post by albinootje on 2008-12-21
> **nss0000 said:**
> 
SO:  I have made a recommended entry in /etc/sysctl.conf:

             net.ipv4.icmp_echo_ignore_all=1


Did you also use the sysctl command to apply those changes ?
And is your Ubuntu-box transparently open to the Internet ?
Or is there a cable-modem or DSL-modem with its own firewall in between ?

---

### Post by bodhi.zazen on 2008-12-21
See this page :

[https://help.ubuntu.com/community/Uncomplicated_Firewall_ufw](https://help.ubuntu.com/community/Uncomplicated_Firewall_ufw)

There is a section on ping ...

and do not forget, if you have a router, services like Shields Up are scanning your router, not your computer. To scan your computer you need to scan from a second box on your LAN.

---

### Post by nss0000 on 2008-12-21
ALB:

Did you also use the sysctl command to apply those changes ? 

WHAT <sysctl> command? I edited the file and saved changes.

And is your Ubuntu-box transparently open to the Internet ?

Actually SHIELDS-UP sez I am invisable except fpr <ping>

Or is there a cable-modem or DSL-modem with its own firewall in between ?

Both a DSL-modem and a router sit between my-box and the WWW.

---

### Post by albinootje on 2008-12-21
> **nss0000 said:**
> ALB:

Did you also use the sysctl command to apply those changes ? 

WHAT <sysctl> command? I edited the file and saved changes.

Okay. Read in a terminal : man sysctl  (Use "q" to quit).

And perform :
```

sudo /sbin/sysctl -p /etc/sysctl.conf

```
> 
And is your Ubuntu-box transparently open to the Internet ?

Actually SHIELDS-UP sez I am invisable except fpr <ping>

Or is there a cable-modem or DSL-modem with its own firewall in between ?

Both a DSL-modem and a router sit between my-box and the WWW.

Please reread the previous posting by bodhi.zazen
If there's a DSL-modem and router in between scanning for pings from the internet concerning your machine behind the firewall doesn't make sense.
You would need to ping it from within your LAN with another machine.

---

### Post by rhcm123 on 2008-12-21
> **albinootje said:**
> Okay. Read in a terminal : man sysctl  (Use "q" to quit).

And perform :
```

sudo /sbin/sysctl -p /etc/sysctl.conf

```


Please reread the previous posting by bodhi.zazen
If there's a DSL-modem and router in between scanning for pings from the internet concerning your machine behind the firewall doesn't make sense.
You would need to ping it from within your LAN with another machine.

Most dsl routers can be configured to auto drop ping requests.
also, Shields up is designed for scanning windows machines, so they over-hype a few things, like ping replies. Open ports are more worrisome.

---

### Post by jerome1232 on 2008-12-21
> **nss0000 said:**
> 
Both a DSL-modem and a router sit between my-box and the WWW.

That means your router is what's responding to the pings, most can be told to not respond to pings on the internet side.

---

### Post by gTinker on 2008-12-21
[QUOTE=rhcm123]Most dsl routers can be configured to auto drop ping requests.
also, Shields up is designed for scanning windows machines, so they over-hype a few things, like ping replies. Open ports are more worrisome.[/QUOTE]

This information is something that probably doesn't get considered often enough. There is extremely little additional security provided by not answering pings. As soon as you try to surf to any site, the black hats see your packets out there in cyberspace and know there is something connected to your IP address. Perhaps in the early days this kind of obscurity was helpful, today, not so much. If nothing else they will do a FIN scan and find you that way. Or some other stealth scan.

---

### Post by bodhi.zazen on 2008-12-21
> **gTinker said:**
> This information is something that probably doesn't get considered often enough. There is extremely little additional security provided by not answering pings. As soon as you try to surf to any site, the black hats see your packets out there in cyberspace and know there is something connected to your IP address. Perhaps in the early days this kind of obscurity was helpful, today, not so much. If nothing else they will do a FIN scan and find you that way. Or some other stealth scan.

+1

Security through obscurity is no security at all.

Similar arguments apply to when people say there are no linux viruses because linux only has 1 % of the market. 

Linux security is not based on obscurity.

---

### Post by gTinker on 2008-12-21
[QUOTE=bodhi.zazen]Similar arguments apply to when people say there are no linux viruses because linux only has 1 % of the market. [/QUOTE]

And +1 on that. 

The scary thing is that so many "technical" authors keep repeating this stuff, it's as if they don't research what they are writing about, no wonder normal users stay confused about the topic. It's darn difficult to find intelligent discussion about the topic.

---

### Post by nss0000 on 2008-12-21
J:

Yes, the MAN-page for sysctl is beyond my skill. Yes I have tried unsuccessfully to address the router. No I don't believe that ANY obstacle-to or report-of casual intrusion is wasted.

Clearly intrusion prevention/detection is an area where the Linux lusr_desktop is still primative. But, then <printing> was once nearly undoable also. I faithfully await the automagic <ping> supression. 

Thanks to the many able responders -- I will know what to look for when the utility becomes available.

---

### Post by albinootje on 2008-12-21
> **nss0000 said:**
> J:

Yes, the MAN-page for sysctl is beyond my skill. 

I think i also gave you the command to apply the settings you made to /etc/sysctl.conf.

> Yes I have tried unsuccessfully to address the router. No I don't believe that ANY obstacle-to or report-of casual intrusion is wasted.

Clearly intrusion prevention/detection is an area where the Linux lusr_desktop is still primative. But, then <printing> was once nearly undoable also. I faithfully await the automagic <ping> supression. 

Thanks to the many able responders -- I will know what to look for when the utility becomes available.

There is no need at all to disable answering ping-requests on a Linux-desktop.
If you really think it is needed, and you want a GUI for it, let others know it at [http://brainstorm.ubuntu.com](http://brainstorm.ubuntu.com)

Just my 0.02E cents.

---

### Post by jerome1232 on 2008-12-21
> **nss0000 said:**
> J:

Yes, the MAN-page for sysctl is beyond my skill. Yes I have tried unsuccessfully to address the router. No I don't believe that ANY obstacle-to or report-of casual intrusion is wasted.

Clearly intrusion prevention/detection is an area where the Linux lusr_desktop is still primative. But, then <printing> was once nearly undoable also. I faithfully await the automagic <ping> supression. 

Thanks to the many able responders -- I will know what to look for when the utility becomes available.

If a computer is behind a router there's nothing the computer can do to stop the router from responding to ping requests....

---

### Post by bodhi.zazen on 2008-12-21
> **nss0000 said:**
> J:

Yes, the MAN-page for sysctl is beyond my skill. Yes I have tried unsuccessfully to address the router. No I don't believe that ANY obstacle-to or report-of casual intrusion is wasted.

Clearly intrusion prevention/detection is an area where the Linux lusr_desktop is still primative. But, then <printing> was once nearly undoable also. I faithfully await the automagic <ping> supression. 

Thanks to the many able responders -- I will know what to look for when the utility becomes available.

I appreciate what you are doing, but I think your efforts are misguided.

First, as has been pointed out, it is your router and not your desktop that is responding to ping.

Second, the linux firewall is very sophisticated, It is called iptables.

Third, as I pointed out, UFW will configure your firewall. UFW is installed by default and as the link I gave you pointed out, UFW blocks ping by request.

Fourth, as I said earlier, if you want to scan your desktop you need to scan it from a second computer on your LAN, not Shields up.

---

### Post by rhcm123 on 2008-12-21
> **gTinker said:**
> This information is something that probably doesn't get considered often enough. There is extremely little additional security provided by not answering pings. As soon as you try to surf to any site, the black hats see your packets out there in cyberspace and know there is something connected to your IP address. Perhaps in the early days this kind of obscurity was helpful, today, not so much. If nothing else they will do a FIN scan and find you that way. Or some other stealth scan.

My point exactly. I don't worry about the shields up notices though, as i haven't even seen the site updated in quite some time. It dosen't even mention vista, and all the tools havent been recently updated. It seems abandoned. I don't even recall the main page ever changing.

However, your confidence is slightly misplaced. If you do manage to stealth your ip and drop ping requests, then the traffic will come from your ISP's block of IP addresses.

> **bodhi.zazen said:**
> +1
Similar arguments apply to when people say there are no linux viruses because linux only has 1 % of the market. 


I am in such a debate about linux secuirity in another thread it isn't even funny. Anyways, to fix this issue. Most routers can be configured (on linksys, i belive it is the secuity tab, then block anonymous wan requests) to drop WAN ping requests. I use dd-wrt and all i would have to do is check that little box and i'm done. However, I don't because I need to occasionally use ping to test outside connections to my home server equipment.

---

### Post by nss0000 on 2008-12-22
I have no access to my router though I am also sure a more skilled person could find it. A few GOOGLED multi-tuples xxx.yyy.etc do not provide access. I don't know where-from <pings> may originate, but killing any subset seems a good idea. Yes SHIELDS-UP is not a Linux site, but lusrs may not always choose "PORTs" in a storm ... hehe.

But, seriously ... nobody admins my home-boxes, but me. For this task I have very modest skills , no talent and enough years on *nix to know it is completely unlearnable. I DO have work to accomplish. I do what I can.

---

### Post by jerome1232 on 2008-12-22
> **nss0000 said:**
> I have no access to my router though I am also sure a more skilled person could find it. A few GOOGLED multi-tuples xxx.yyy.etc do not provide access. I don't know where-from <pings> may originate, but killing any subset seems a good idea. Yes SHIELDS-UP is not a Linux site, but lusrs may not always choose "PORTs" in a storm ... hehe.

But, seriously ... nobody admins my home-boxes, but me. For this task I have very modest skills , no talent and enough years on *nix to know it is completely unlearnable. I DO have work to accomplish. I do what I can.

An easy way to figure out the address of your router is to run route, whatever it says the default gateway will be the address of your router.

So just fire up you favorite webbrowser and enter that ip that route said was your gateway.

This is an example of mine, the gateway (router) is highlighted in blue
```
 route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     2      0        0 wlan0
link-local      *               255.255.0.0     U     1000   0        0 wlan0
[COLOR="Blue"]default         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0[/COLOR]
```

Though honestly this really is a futile effort, closed ports are closed ports. You have a router (which drops incoming traffic btw) then your computer that has a firewall configured to drop incoming traffic, then you have your computer which (unless you've installed some servers) isn't listening for those connections in the first place and will drop any incoming traffic that reaches it.

---

### Post by nss0000 on 2008-12-22
BZ:

I could find no (recognizable) instruction in your UFW reference. In general Linux instructions are unreadable for me. Actually it's only OUTSIDE <pings> I wish to defeat so I guess my entire approach is <not even wrong>. 

I see no reason why an OS could not automagically CHAT with a router and configure it, but that is a technical issue beyond me. The technical issues here are in-general well-beyond my skill level. When they may be performed automagically I will say MAKE IT SO. Thanks for your comments.

---

### Post by nss0000 on 2008-12-22
J:

AS you can see the evil.*nix.goddess within my AMD_kit will have none-of-this foolishness.

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
link-local      *               255.255.0.0     U     0      0        0 eth1
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         launchmodem     0.0.0.0         UG    100    0        0 eth0
default         *               0.0.0.0         U     1000   0        0 eth1

---

### Post by bodhi.zazen on 2008-12-22
> **nss0000 said:**
> BZ:

I could find no (recognizable) instruction in your UFW reference. In general Linux instructions are unreadable for me. Actually it's only OUTSIDE <pings> I wish to defeat so I guess my entire approach is <not even wrong>. 

I see no reason why an OS could not automagically CHAT with a router and configure it, but that is a technical issue beyond me. The technical issues here are in-general well-beyond my skill level. When they may be performed automagically I will say MAKE IT SO. Thanks for your comments.

I was not trying to be rude, just get you back on track. You are trying to configure your desktop (and doing it the hard way) when you should be configuring your router.

As explained in the link I gave you, UFW blocks ping.

At any rate, to configure your router you need to log into it. What router do you have ? It may also be your router does not have this option. But again, you are confusing router functions with Linux on your desktop.

Boot to windows and you will get the same results. Again the results you are getting from Shields Up are from your router, not the OS or firewall you are running on your desktop or server.

---

### Post by gTinker on 2008-12-22
[QUOTE=nss0000]I see no reason why an OS could not automagically CHAT with a router and configure it, but that is a technical issue beyond me. The technical issues here are in-general well-beyond my skill level. When they may be performed automagically I will say MAKE IT SO. Thanks for your comments.[/QUOTE]


Okay, it seems that we have been throwing around terms and instructions that you aren't yet familiar with, that can happen in sections of the forum where most people are a bit more advanced than you characterise yourself. Sorry.

I will answer this question for you, the problem is that the various router manufacturers don't build the interface to the configuration as a standard, thus it's difficult-to-impossible for software in the OS to do the kind of automagic you desire. Most of them do choose default setups that will "work" out of the box for a system configured the way Windows computers are configured. But that means lax security and here in the open source world, we usually care more about security.

I will mention that the stuff we are talking about would be covered in the documentation that came with your router. It would tell you what internal LAN IP address to type into your browser's search bar to get to the configuration page and it would explain a bit about what the options mean. They are not all the same and we have no idea of what you have because you didn't mention it.

The bottom line:
It's your router that is responding to pings not your computer.
Most of us agree that blocking pings isn't a big security advantage and not blocking them isn't a big risk.
We can't help you if you choose to not learn anything new about your system or how it works. 
Neither us nor GNU/Linux is a "lusr" (your term).

---

### Post by nss0000 on 2008-12-22
Gents:

Again I would like to thank all posters to this thread. Re-reading all the posts, I have been convinced my original thought of dissembling <ping> was a poorly imagined task. I've stopped trying to do it.

This thought occurs to me: to the casual desktop lusr there's a large "asymmetry" in the tasks performed by HH_8.04.1 Ubuntu computing environment. 

Make no mistake -- I count on Ubuntu for important daily work: writing lectures, reading N.G.s, running simulations and even producing at times lots of "scientific-C" code. Ubuntu has become really important to me because I can TRUST it to perform needed tasks: a very long list of non-trivial tasks. 

And there lies the confounding asymmetry in Ubuntu. There is no method or regime(?) to form a reasonable expectation about which tasks will in-fact be performed! The <ping> issue is one small example. For another ...

Recently I discovered that HH_8.04.1 automagically installs and configures WINE. Oh how nice; I had failed many times before to do this manually.  Then, one single [terminal] command installs my favored M$ version of xSPICE I had long maintained on a legacy Windows-box. For that program everything including the printer and file interface just works.  

Quite amazing! It changes and improves the way I work. But ...the <ping> task does not just work! I trust you see the asymmetry: what was important and impossibly hard becomes trivial -- what appears trivial is not only impossible, but not worth doing! Ubuntu decides and Ubuntu provides ... I understand the latest Ubuntu v8.1 automagically configures the LOCAL network ... in my case 3-boxes that have long defied my (best) attempts to connect. Perhaps that function will be back-ported to v8.04. 

I feel like the savage in "The Gods must be Crazy". Thanks again to all responders.

---

### Post by cariboo on 2008-12-22
I was just looking at the listing you got from the route command, and I see you have your router aliased to launchmodem, Open Firefox and in the address bar type:

```
http://lanuchmodem
```

If that doesn't work, try:

```
https://launchmodem
```

You of course will have to enter your username and pasword to access the management interface.

Jim

---

### Post by Vantrax on 2008-12-22
> **nss0000 said:**
> Gents:

Running x64HH_8.04.1 fully patched.

I'm trying to stop my system from responding to WWW <PING> query. This evidently cannot be done from the GUFW firewall interface.

SO:  I have made a recommended entry in /etc/sysctl.conf:

             net.ipv4.icmp_echo_ignore_all=1

But, the Gibson SHIELDS-UP site still claims my system responds to <PING>.
Where have I gone (not even?) wrong ?


I was trying not to comment on this but please please ignore everything Gisbon says. The man knows very little about real security and is well known in the industry as a FUD expert. People are right about the site detecting your router not your machine (unless you have a non private IP).

If you do want to learn about real security look at places like [http://www.securityfocus.com](http://www.securityfocus.com) and [http://www.pauldotcom.com](http://www.pauldotcom.com). 

Again, please do not go of Steve Gibson sayso. The man is great at getting media attention, but I doubt he could build a linux box without help.

---

### Post by nss0000 on 2008-12-22
> **cariboo907 said:**
> I was just looking at the listing you got from the route command, and I see you have your router aliased to launchmodem, Open Firefox and in the address bar type:

```
http://lanuchmodem
```

If that doesn't work, try:

```
https://launchmodem
```

You of course will have to enter your username and pasword to access the management interface.

Jim
CBOO:

 YEP: [http://launchmodem/](http://launchmodem/) works ... and leads to a BellSouth DSL page! Them being my ISP/DSL supplier. Actually many pages with lots of "connectivity" details. Looks like BS.inc have taken over my router .. must be std. proceedure(?).

Just to say I saw it I LOOKED among-the-pagesfor a place to disable <ping>. Nothing, but actually an offer to USE <ping> for system testing. 

You will be amused I'm sure -- I already KNEW about those pages, had the address stored elsewhere,  but had no-idea they had anything specifically to do with my router. I viewed the router as on MYSIDE while the modem starts THEIRSIDE.

---

### Post by rhcm123 on 2008-12-24
> **nss0000 said:**
> CBOO:

 YEP: [http://launchmodem/](http://launchmodem/) works ... and leads to a BellSouth DSL page! Them being my ISP/DSL supplier. Actually many pages with lots of "connectivity" details. Looks like BS.inc have taken over my router .. must be std. proceedure(?).

Just to say I saw it I LOOKED among-the-pagesfor a place to disable <ping>. Nothing, but actually an offer to USE <ping> for system testing. 

You will be amused I'm sure -- I already KNEW about those pages, had the address stored elsewhere,  but had no-idea they had anything specifically to do with my router. I viewed the router as on MYSIDE while the modem starts THEIRSIDE.

How did you configure your network without access to your modem? Just curious, as I have messed around with so many settings it's unfunny.

---

### Post by nss0000 on 2008-12-25
rhcm:

I did nothing to configure my "network". I connected modem-to-router, and router to each-of-three boxes. Then I turned on the first Ubuntu box and fed it the DD_6.06 CD.

Stuff happened. Don't remember doing much else. I may have been prompted for a few mystery alpha-numerics, but they seem to have been trivial. Ubuntu does WWW_connection automagically. The 2nd Ubuntu box just slipped in. I had to get some BS_help for my legacy WinME-box, but then that's Windows not Linux.

Now ... I have NOT/NEVER been able to get my 3-boxes to talk to eachother, but that's LAN_stuff and incomprehensible to the casual lusr. I don't even consider trying worthwhile and the RISK of trashing what_works_already large. 

I do understand that HH_8.1 does LAN automagically also. As it should.

---

### Post by jerome1232 on 2008-12-25
> **nss0000 said:**
> rhcm:

I did nothing to configure my "network". I connected modem-to-router, and router to each-of-three boxes. Then I turned on the first Ubuntu box and fed it the DD_6.06 CD.

Stuff happened. Don't remember doing much else. I may have been prompted for a few mystery alpha-numerics, but they seem to have been trivial. Ubuntu does WWW_connection automagically. The 2nd Ubuntu box just slipped in. I had to get some BS_help for my legacy WinME-box, but then that's Windows not Linux.

Now ... I have NOT/NEVER been able to get my 3-boxes to talk to eachother, but that's LAN_stuff and incomprehensible to the casual lusr. I don't even consider trying worthwhile and the RISK of trashing what_works_already large. 

I do understand that HH_8.1 does LAN automagically also. As it should.

What do you mean by "talk" to each other? You mean sharing files? sharing printers?

If that's what you mean you have to actually install some type of file server on the computers that you want to serve files (That's true of 8.10 as well). 

Whether it be samba (I perfer this when there's a mix of Linux and Windows), nfs, sshfs (I prefer this in a pure Linux environment), ftp or sftp.

It would be poor security to have the operating system sharing your files to the network by default don't you think? (Think about taking your laptop to a wifi hotspot, this would give everybody at the coffee shop the ability to access your files)

---

### Post by nss0000 on 2008-12-25
J1213:

What do you mean by "talk" to each other? You mean sharing files? sharing printers?

***Well ... yes.  

If that's what you mean you have to actually install some type of file server on the computers that you want to serve files (That's true of 8.10 as well).

***Well I'm sure your currently correct, since my boxes don't offer to do that swapping of function/data themselves.

Whether it be samba (I perfer this when there's a mix of Linux and Windows), nfs, sshfs (I prefer this in a pure Linux environment), ftp or sftp.

***WEll yes I've heard those proggy_names. SAMBA has foiled me more-than-once.

It would be poor security to have the operating system sharing your files to the network by default don't you think? (Think about taking your laptop to a wifi hotspot, this would give everybody at the coffee shop the ability to access your files)

***Well ... no. It's the OS(environments) responsibility to provide MAXIMUM benefit to me, the lusr. My current x64HH_8.04.1 already installs, configures and updates both itself and a raft of desktop applications. It automagically connects me to various HW_peripherals  and to the WEB. 

Ubuntu also makes additional functions available ( such as WINE ) with minimal effort appropriate to the casual lusr. In no case am I-the-lusr held responsible for system security, beyond the most modest dis-respect for the goodness of humans. Most children learn this by age 12.

True enough, I consider laptops & wireless technology a frivolous venture and will have none-of-it. My home-kit are all wired with red/green/blue cables and if you want to listen-in locally I keep a 357-cal Dan Wessen  to discourage the effort.  

So on my home kit I have-no-issue with Ubuntu establishing, configuring and expressing for-my-use all the LAN functions it can muster. Its skill is surely far beyond mine.

---

