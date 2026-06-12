---
title: "Hidden backdoor in my AT&amp;T 2Wire Modem/Router"
date: 2011-08-11
forum: Security
---

### Post by Z3ro3X on 2011-08-11
This isn't related to Ubuntu but I wasn't sure where to ask.  My 2Wire router/modem I got from AT&T for my DSL has port 3479 TCP open and I can't figure out how to close it.  It's open to the entire internet.  From a quick google search it's some port AT&T can use to update the modem's firmware or something.  Which seems like a huge security hole to me.  Consider how in bed AT&T is with government agencies it seems like a easy way for the government to get into my home network just by using what seems to me a backdoor put there by AT&T.  Anyway to close this or secure it.  Right now I'm using the hardware as my main router for my home network.  I have Linsys I modded with DD-WRT.  I'm thinking of re-configuring my network to use the DD-WRT router as the main router and the 2wire just as a modem.  The 2wire is a hybrid modem/router and I'm kind of lazy and don't feel like re-configuring my entire network if I can just close the port.  Any help, advice or suggestions would be appreciated.

---

### Post by jramshu on 2011-08-11
Go to 2wires website and ask why you can't close it. I'd also get with AT&T and ask them. There isn't much info out there about it, except it's basically a service port for updates and such.

Sorry I couldn't be of more assistance to you.

---

### Post by SoFl W on 2011-08-11
> Most AT&T U-Verse subscribers receive a 2wire residential gateway  for their subscription to Internet, TV, and VoIP phone service. I  believe most subscribers get a [3800HGV-B]("https://fjallfoss.fcc.gov/prod/oet/forms/blobs/retrieve.cgi?attachment_id=652683&native_or_pdf=pdf"). The  user guide for that model does not mention anything about a TCP Port  3479 being opened or used by default. So I found it strange to see TCP  port 3479 open when I performed a full TCP port scan from the Internet  to my external U-Verse IP:[INDENT]nmap -sSV -n -P0 -p- &#8220;ip&#8221;
[/INDENT]The results look like this if no other TCP ports are open in the firewall:[INDENT] 135/tcp   filtered msrpc
 136/tcp   filtered profile
 137/tcp   filtered netbios-ns
 138/tcp   filtered netbios-dgm
 139/tcp   filtered netbios-ssn
 445/tcp   filtered microsoft-ds
 3479/tcp  open     unknown
 6881/tcp  filtered bittorrent-tracker
 [/INDENT]An nmap UDP scan also returned two open ports:[INDENT] nmap -sSV -n -P0 -p- &#8220;ip&#8221;
  50817/udp open  unknown
 60062/udp open  ntp     NTP v4
 
 [/INDENT]The filtered ports by default make sense as they are used for  SMB/CIFS (135-139 & 445). Port 6881 is interesting to see as it is  the default port for bittorrent. You can forward any other port to host  your torrents, just make sure it matches the client.
 What was most interesting of these results is the open TCP port  3479. A little google hacking and I found that port is labeled as 2wire  RPC and is registered:
   **Port 3479 details:**

 
  Protocol:[COLOR=#777777]TCP & UDP[/COLOR]
 IAMA status:[COLOR=#777777]Official[/COLOR]
 Range:[COLOR=#777777]Registered[/COLOR]
 Traffic:[COLOR=#777777]inbound, outbound, both[/COLOR]
 Notification:[COLOR=#777777]True[/COLOR]
 Related Ports:[COLOR=#777777]3478, 5060, 5062[/COLOR]
 [INDENT]Technical description for port 3479:
 The 2Wire RPC protocol officially registered to use the communication  port 3749 is associated with the Remote Procedure Call (RPC) technology  developed by Microsoft. This process allows for the implementation of a  communication technique for the efficient exchange of data between a  server and client machine. 2Wire is a popular manufacturer of DSL  systems and residential gateway provider.
The 2Wire protocol associated with the system port 3749 is described as a  modified XML based RPC which allows HomePortal devices to create a  communication link with the datacenter. This communication foundation is  used for receiving of contents, updates and programming of related  devices. This protocol intends to mitigate communication issues that may  hamper effective transmission interface.
The products of 2Wire benefiting from this protocol are considered as  the first really intelligent, multi-service and customer installable  devices of the industry.
The implementation of the protocol related to the port 3749 is widely  supported by newer Operating System platforms including communication  applications.
[/INDENT] Interesting information here. I did a quick scan of other AT&T  IPs in the same network and all of them had TCP port 3479 open as well.  There is very little information online about this. However I did find  someone reporting the following errors on the gateway:[INDENT][COLOR=#222222][FONT=Verdana]ERR 2004/03/30 07:24:21 CST xmlrpc: error creating connection to &#8216;rpc.cms.2wire.com:3479&#8242; (216.52.29.106): Connection refused[/FONT][/COLOR]
[/INDENT]Although the post is from 2004. I took a look and that [IP belongs to 2wire in San Jose]("http://infosniper.net/index.php?ip_address=216.52.29.106&map_source=1&overview_map=1&lang=1&map_type=1&zoom_level=7").
 My next steps will be to attempt to sniff what is coming in to this  port. I have a feeling it will be clear text and not use authentication.  More to come&#8230;
 Till next time,
 Jorge Orchilles 


[LINK TO ABOVE]("http://orchilles.com/2011/02/att-u-verse-open-port-3479.html")

---

### Post by Z3ro3X on 2011-08-11
@SoFl W
I all ready found that URL from my initial google search.  It still doesn't tell me how to close it.  I don't care how legit they say it is.  Point is, it's still an open port into my network that can be potentially exploited by crackers or abused by authorities.  I paid for this hardware.  Unless I open up a port on the hardware's firewall there should be no open ports, period.  AT&T has no business opening any ports on MY hardware I paid for or doing anything to it with out my say so.  Thanks for taking the time to help though.  Until I find another solution I may just go ahead and redo my home network.  Take all my clients on the network and put them on the DD-WRT router, turn on it's firewall and connect that to the 2wire gateway.  I'll need to re-configure both routers though, which will be a pain in the butt.

---

### Post by thefasterblueone on 2011-08-11
Use IPtables.
```
man iptables
```

[Examples](http://www.cyberciti.biz/faq/iptables-block-port/)

---

### Post by haqking on 2011-08-11
> **Z3ro3X said:**
> @SoFl W
I all ready found that URL from my initial google search.  It still doesn't tell me how to close it.  I don't care how legit they say it is.  Point is, it's still an open port into my network that can be potentially exploited by crackers or abused by authorities.  I paid for this hardware.  Unless I open up a port on the hardware's firewall there should be no open ports, period.  AT&T has no business opening any ports on MY hardware I paid for or doing anything to it with out my say so.  Thanks for taking the time to help though.  Until I find another solution I may just go ahead and redo my home network.  Take all my clients on the network and put them on the DD-WRT router, turn on it's firewall and connect that to the 2wire gateway.  I'll need to re-configure both routers though, which will be a pain in the butt.


Configure the Firewall on the router to disallow traffic on that port.

As for not trusting them, if ATT are providing you the service anyways, all your packets are going through them , so if they were hell bent on using your backdoor and they couldnt they could just grab the packets anyways.....LOL

---

### Post by jramshu on 2011-08-11
I don't think iptables will work in the modem/router, for Linux boxes after the router yes.  

I don't blame you for wanting complete control of your modem/router, since you do own it. 

JMO

@haqking
You are absolutely right. Didn't think of it that way LOL!!!

---

### Post by haqking on 2011-08-11
> **jramshu said:**
> I don't think iptables will work in the modem/router, for Linux boxes after the router yes.  

I don't blame you for wanting complete control of your modem/router, since you do own it. 

JMO

@haqking
You are absolutely right. Didn't think of it that way LOL!!!

IP Tables will work for his machine and stop traffic from the router.

The router will highly likely be linux based anyways and so actually using IPTables underneath but configurable through the routers own interface and as i said just firewall the traffic on that port.

and to be honest you will always be in the hands of your ISP no matter what you do if you want to use their equipment and connection ;-)

---

### Post by jramshu on 2011-08-11
Yep, I get ya. 

Most routers use Linux but, the iptables are only configurable through the modem/routers firewall configs. I was talking about directly configuring the modem/routers iptables through a Linux box. iptables on the box itself will protect the box but not the network and must be done the way you are saying, through the modem/router firewall configs.

---

### Post by dirtrider1 on 2011-08-13
I had a similar problem with Verizon Fios, the cheap Verizon router they include with that service is the only one they will support. Unfortunately that router also had an open port for "administrative access" that could not be closed . I agree that an ISP generally can see your traffic outside of the LAN if your not using encryption of some sort but that is expected as the Internet is one big open insecure network and rightly so, but that should not apply to your LAN where the entire purpose is privacy and your ISP should have no access. I ended up getting a Linksys router to work in place of the Verizon router but if there is ever a problem the "tech support" can not help unless I reinstall the Verizon router. To the OP I would probably go with your solution of just using the AT&T router as a modem and set up the DD-WRT as your main router/Firewall and just consider anything outside of the Linksys DD-WRT as insecure.

---

### Post by nevius on 2011-08-13
> **Z3ro3X said:**
> This isn't related to Ubuntu but I wasn't sure where to ask.  My 2Wire router/modem I got from AT&T for my DSL has port 3479 TCP open and I can't figure out how to close it.  It's open to the entire internet.  From a quick google search it's some port AT&T can use to update the modem's firmware or something.  Which seems like a huge security hole to me.  Consider how in bed AT&T is with government agencies it seems like a easy way for the government to get into my home network just by using what seems to me a backdoor put there by AT&T.  Anyway to close this or secure it.  Right now I'm using the hardware as my main router for my home network.  I have Linsys I modded with DD-WRT.  I'm thinking of re-configuring my network to use the DD-WRT router as the main router and the 2wire just as a modem.  The 2wire is a hybrid modem/router and I'm kind of lazy and don't feel like re-configuring my entire network if I can just close the port.  Any help, advice or suggestions would be appreciated.

I have called ATT before about other issues regarding the 2wire gateway. They have the ability to remotely administer the router (so that they can do things like help people log into their wireless network without sending a technician to the house). The time when they wanted to remotely access the gateway they recorded me explicitly giving them permission to access it. (i.e. I don't think they are doing anything nefarious with the gateway.)

As it turned out, I had changed the default password for the administrator account and they weren't able to log in. Lesson learned - if you don't want them messing with it, just change the default admin password.

---

### Post by Z3ro3X on 2011-08-14
Thanks everyone for the advice and suggestions.  I found a useful tutorial for turning my hybrid modem/router into a plain modem.  So now I'm using the DD-WRT as my main router.  Which makes things easier this way.  I hated the GUI interface on the 2wire gateway.  I wasn't all that concerned with them sniffing my unencrypted packets.  That's to be expected.  None of the computers on my network have firewalls.  Which is on purpose.  They all share files and resources with all other systems on the LAN.  And I wasn't all that stoked to find out AT&T could access my LAN when ever they wanted.  Considering how in bed AT&T is with government agencies, the FBI or who ever can just wave some scary badge, etc and have AT&T give them access to people's LAN's.  I'm not doing anything to warrant having the FBI have a reason to get into my network.  It's all a matter of princple. lol

---

