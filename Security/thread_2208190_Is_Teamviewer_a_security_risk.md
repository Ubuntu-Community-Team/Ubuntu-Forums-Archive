---
title: "Is Teamviewer a security risk"
date: 2014-02-26
forum: Security
---

### Post by Odyssey1942 on 2014-02-26
I have recently learned about TeamViewer, which allows you to remotely connect to another TeamViewed enabled computer, either to retrieve files or operate the "home" computer. Possibly a very convenient thing on occasion.

I do not understand very much about open ports, "listening", and "calling out", but I am surmising that if one calls one's home computer from a distant computer using TeamViewer (perhaps any remote conncection) that the home computer must be listening, and therefore must have an open port.

If I understand it, Ubuntu doesn't normally open ports to "listen" for incoming connections, so if this is what TV is doing, does this represent a significant security risk? And if so can it be mitigated?

---

### Post by uRock on 2014-02-26
Hello,

 I have moved your thread to the Security Discussions sub-forum, where it may get the best results.

You can use the netstat command to see what ports are currently listening. 

Have you forwarded ports through your router? If not, then it is likely the system can't be seen from the outside world. If you have, then you may want to place rules in your firewall allowing only the IP addresses you know you will be connecting from to be able to connect to your system and denying all others. This link may be helpful in configuring your system's firewall, [https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)

---

### Post by papibe on 2014-02-26
Hi Odyssey1942.

Setting up remote access to a machine is not a security risk, as say running IE on XP.

However, it opens a security ***concern***. Having said that,  a lot of people, including me, allow home remote access through ssh.

The most common ways someone could gain access to your machine are:
[LIST]
[*]your phone/laptop gets stolen with the remote access password saved for convenience, or
[*]a brute force attack.
[/LIST]
The second case it is very unlikely to happen on a home Internet connection (VPS are usually attacked though). There are common practices to dealing with that situation. Take a look at [fail2ban]("https://help.ubuntu.com/community/Fail2ban"), and [iptables]("https://help.ubuntu.com/community/IptablesHowTo").

Hope that helps. Let us know how it goes.
Regards.

---

### Post by CharlesA on 2014-02-26
What papibe said. If you do set up TeamViewer for 24/7 access, be sure to use a super strong password. Any form of remote access can be attacked, but if you have a strong password, it should be "OK"

The better thing to do is not launch teamviewer unless you need it.

---

### Post by mekon2 on 2014-02-27
Any recommended alternatives to Teamviewer? I want to access my Ubuntu desktop at home from work.

---

### Post by IvoGuerreiro on 2014-02-27
Teamviewer for me it work perfectly, but if you want something different give a look at Remmina.
[http://remmina.sourceforge.net/](http://remmina.sourceforge.net/)

---

### Post by SeijiSensei on 2014-02-27
I gave TeamViewer a run the other day as I was curious about connecting to a desktop machine from my Android.  Other than trying to navigate a full desktop on a 4" screen, it worked well.

It doesn't look to me like it opens any ports on the target computer at all.  Perhaps TeamViewer works like GoToMyPC, where all the communications are mediated via an online server?  It also looks to have some pretty heavy encryption as well. From the webpage: "TeamViewer is a highly secure remote maintenance solution. Your connections are established via fully encrypted data channels using 2048-bit RSA key exchange and 256-bit AES session encoding."

---

### Post by bashiergui on 2014-02-27
> Other than trying to navigate a full desktop on a 4" screen, it worked well.LOL sounds perfect :-D

---

### Post by SeijiSensei on 2014-02-27
I was just curious to see how well it works.  Personally I'd rather carry my 10" ASUS netbook.

I have also thought about connecting the phone to a television with an HDMI cable and adding a Bluetooth keyboard and mouse.  That might make for a lightweight computing option while travelling.

---

### Post by CharlesA on 2014-02-27
> **SeijiSensei said:**
> I was just curious to see how well it works.  Personally I'd rather carry my 10" ASUS netbook.

I use it if I need to do support for my Aunt. It works well and is fairly responsive even over low bandwidth links.

I've used it off my 14" laptop before, but I don't think I could stand using it on a 4" phone.

---

### Post by sammiev on 2014-02-27
I use TeamViewer from time to time and really like it, but I could never even dream of using it on a 4" screen. LOL

---

### Post by bashiergui on 2014-02-27
> **SeijiSensei said:**
> I have also thought about connecting the phone to a television with an HDMI cable and adding a Bluetooth keyboard and mouse. That might make for a lightweight computing option while travelling.
I like that idea, wouldn't be a bother to drag it around with me. Would make airport security checks easier, too.

---

### Post by Odyssey1942 on 2014-02-28
OK. I decided to run GRC.com's open ports test and it ran the test on the first 1024 ports without TeamViewer running. All ports green.

Started TeamViewer and ran the GRC test again. All ports still green.

Does this mean that TV is using a port numbered 1025 or higher, or how can this be?

How do I determine what port/s TV employs? Can't find anything within TV.

---

### Post by bab1 on 2014-03-01
> **Odyssey1942 said:**
> OK. I decided to run GRC.com's open ports test and it ran the test on the first 1024 ports without TeamViewer running. All ports green.

Started TeamViewer and ran the GRC test again. All ports still green.

Does this mean that TV is using a port numbered 1025 or higher, or how can this be?

How do I determine what port/s TV employs? Can't find anything within TV.

GRC tests the WAN side interface of your router.   You are not testing the host running TeamViewer at all.

---

### Post by Odyssey1942 on 2014-03-01
Bab, I am truly a babe in the woods here, so please forgive any basic misunderstandings on my part, but I am not concerned about threats from inside my LAN, only from outside. So if my home computer is running TV host, and I want to access it from outside via TV client, should I not be concerned about the risk on the WAN side?

---

### Post by The Spectre on 2014-03-01
I have used TeamViewer for years on both Ubuntu and Windows and have never had a problem.

It can easily connect from Ubuntu to Windows and from Windows to Ubuntu. i have never tried MAC.

The TeamViewer Quick Support is extremely useful when you just want to temporarily connect to someones computer because it is run without being installed.

I have several friend that run into problems on their computer (Windows) from time to time and the TeamViewer Quick Support is perfect for these situations.

If you really want to secure TeamViewer you can create a Black- and Whitelist so only certain IDs and Partners can log into tour Computer...

[ATTACH=CONFIG]250790[/ATTACH]

---

### Post by Odyssey1942 on 2014-03-01
Thanks for that. I do have restricted access set up. My concern has to do with attracting unwanted attention. If there is an open port, as I understand it, this might attract attention and attacks. I am assuming that what some malcreant can see (open port) might be a target for various kinds of attacks, whereas a stealth port might not be as interesting.

Not that there is anything on my computer of interest to anyone other than me, but some folks seem to want to have a look around where they have no business doing so, and if nothing of interest found, then do some damage as revenge for wasting their time. I just don't want to be a target for any reason.

---

### Post by SeijiSensei on 2014-03-01
As I said before, Teamviewer does not open any ports on your machine.  To be sure, I just started up my copy now and scanned the machine with nmap.  There are no additional open ports.  

I believe Teamviewer uses the same architecture as GoToMyPC.  The connection between the two machines is mediated by a server on the Internet.  There is no direct connection from the outside to the controlled computer.

---

### Post by bab1 on 2014-03-01
> **Odyssey1942 said:**
> Bab, I am truly a babe in the woods here, so please forgive any basic misunderstandings on my part, but I am not concerned about threats from inside my LAN, only from outside. So if my home computer is running TV host, and I want to access it from outside via TV client, should I not be concerned about the risk on the WAN side?
As I said before "*GRC tests the WAN side [COLOR="#800080"]**interface of your router**[/COLOR].*  You are not testing your local computer at all.  It's kind of like looking at the front door of your house and surmising that the bathroom door is locked.

I'm not going to comment on whether you *should* use TeamViewer other than to say it does use a server in the middle scenario.  You are reliant on the TeamViewer server not being breached.  That means you are reliant upon an entity you don't control.

---

### Post by CharlesA on 2014-03-01
> **SeijiSensei said:**
> 
I believe Teamviewer uses the same architecture as GoToMyPC.  The connection between the two machines is mediated by a server on the Internet.  There is no direct connection from the outside to the controlled computer.

Just confirming this. This is how it is able to bypass the firewall unless the firewall is set up for outbound filtering.

So basically, TV creates a connect to their server and the connection back is "related" so it doesn't need to open any ports up. Quite nice tbh.

---

### Post by Odyssey1942 on 2014-03-01
Thanks for all the good guidance. In my rather simplistic view:

1) I know of no reason why anyone might target my home computer for "invasion". (Even if someone does hack into my system, there is not much there of interest to anyone else.) And,

2) Even if I leave TV running on my home computer so that I can reach it unattended from away, the fact that it is running does not increase the visibility of my home computer to those using some scanner or whatever tools to find likely targets,

3) So UNLESS TV's security is breached, I am not at greater risk with # 2 in place than if it is not running.

Would this be generally correct?

BTW, I have tried to make the connection from a city about 90 miles away and it worked like a charm. Not speedy, but sufficient for my purposes. And the slowness could have been caused by the Internet connection in the away city.

---

### Post by CharlesA on 2014-03-01
Yes to all. You'll be fine.

---

### Post by untrustytahr on 2014-03-01
> **Odyssey1942 said:**
> OK. I decided to run GRC.com's open ports test and it ran the test on the first 1024 ports without TeamViewer running. All ports green.

Started TeamViewer and ran the GRC test again. All ports still green.

Does this mean that TV is using a port numbered 1025 or higher, or how can this be?

How do I determine what port/s TV employs? Can't find anything within TV.

Most home routers/firewalls are what is called stateful.  This is a fancy way of saying that it keeps track of the requests that the computers in the lan have made.  It puts these requests in a table called a NAT/PAT table.  When the wan interface receives a response, the router will check to see if there is a corresponding request in the table.  If there is, it allows the packet to pass.  If not, it rejects it.  When you started TV, your computer made a connection request to a central server.  It is the response from this server that it lets back in (even though all 65535 ports may appear closed).

---

### Post by untrustytahr on 2014-03-01
> **SeijiSensei said:**
> I believe Teamviewer uses the same architecture as GoToMyPC.  The connection between the two machines is mediated by a server on the Internet.  There is no direct connection from the outside to the controlled computer.

The initial connection made through the proxy.  Direct UDP connection is then established (see UDP hole punching).  There is a lot of overhead in TCP to push a desktop across it.

---

### Post by untrustytahr on 2014-03-01
> **bab1 said:**
> As I said before "*GRC tests the WAN side [COLOR=#800080]**interface of your router**[/COLOR].*  You are not testing your local computer at all.  It's kind of like looking at the front door of your house and surmising that the bathroom door is locked.
__
Yes and no.  Under normal circumstances, you are correct, but if the router is UPnP and an application opened and forwarded a port, then grc would reach the computers network interface and the response would be indicative of it's state.

---

### Post by Odyssey1942 on 2014-03-02
BTW, Thanks to all with a special nod to untrustytahr for the clear explanation of stateful packet inspections. That made it understandable how this can work and still not have open ports.

However, that Bab1 repeated "As I said before "GRC tests the WAN side interface of your router."" makes me wonder if I am missing something. I am only concerned about the WAN side, i.e. external attacks, but should I be thinking about the LAN side? I.e., how would TV create a problem for me on the LAN side if all ports are stealhed?

I marked this Closed pre-maturely and will try to "unclose" to finish out this most interesting conversation.

---

### Post by untrustytahr on 2014-03-02
> **Odyssey1942 said:**
> . I am only concerned about the WAN side, i.e. external attacks, but should I be thinking about the LAN side? I.e., how would TV create a problem for me on the LAN side if all ports are stealhed?
.

Sorry, I did have a reply to that, but I appearantly forgot to paste it back up....

Yes, you also concern yourself with the LAN side.  Good network security is divided into layers.  The outside security perimeter is the main front line of security but it does nothing once someone has already breeched it.  Let's say someone else on your network clicked on a malicious email link and their computer became compromised... What would stop the attacker from using that compromised computer to hop to other computers on the lan?

It's not that TV would be causing the problem... it's what's on the other computers on the lan.  That is one reason why many people divide their networks up into multiple subnets to isolate computers (as well as the normal congestion allieviation).

---

### Post by Odyssey1942 on 2014-03-02
Thanks, and you said something that may help me with something I have been wondering about: 
```
why many people divide their networks up into multiple subnets to isolate computers
```

Is there a sticky or some other sort of "tutorial" that will explain how to do this? It's probably very simple for you to do, but a bit of a mystery for me.

---

### Post by CharlesA on 2014-03-02
I haven't bothered with subnetting for security reasons, but I also don't allow unknown machines on my network.

I have looked into it in the past the separate my VMs from the physical machines but it didn't look as easy as I thought it would be.

---

### Post by bab1 on 2014-03-02
> **Odyssey1942 said:**
> Thanks, and you said something that may help me with something I have been wondering about: 
```
why many people divide their networks up into multiple subnets to isolate computers
```

Is there a sticky or some other sort of "tutorial" that will explain how to do this? It's probably very simple for you to do, but a bit of a mystery for me.

Isolating a network may or may not be because of security reasons.  Some of these that are not completely due to security are: delegation of authority (departmental), the type of subnetwork (data, transit, temporary, etc.) or technical reasons (collision or broadcast domain).  Security is only part of the equation.  I have worked with 16 bit networks (65536 IP addresses) down to  29 bit networks (8 IP addresses).  There are few hard rules as to use of these sized networks (and sub-networks).  Experience and understanding the possibilities are important.

You can start with understanding the TCP/IP stack (OSI model)  and Ethernet (for LAN use).

---

### Post by SeijiSensei on 2014-03-02
For one machine behind one server, a lot of this discussion is overkill.

OP, the only way open ports on an Ubuntu machine behind a firewall can be seen from the Internet is if you choose to forward those ports on the router.  Suppose you were running a web server on TCP port 80.  You might want to make this server visible to the entire globe.  In that case you would use port forwarding to accept inbound traffic on your router and pass it back to the web server.  Port forwarding essentially makes an open port publicly visible.

I don't see you intending to do anything like that.  So, to answer your original question, no, Teamviewer is not a "security risk" if you mean "can someone maliciously connect to my machine via the exposed Teamviewer port?"  There is no exposed port because of the way the application is designed.  Could there be vulnerabilities in the software itself?  Of course, but I suspect they would have been discovered and fixed already.

I appreciate that people here often want to give a "complete" explanation with all the nuances that any security question requires, but often that isn't a helpful answer for a simple question like the OPs.

---

### Post by Odyssey1942 on 2014-03-02
SS, thanks for your always incisive and to-the-point guidance. With enormous respect, I think Charles post #22 did establish this.

What I haven't stated is that our LAN has 5 computers on it and we do our banking online. In addition, we have frequent house guests who use our WiFi and you know how scary that might be. Also there are any number of devices such as AIO network printers, media server type devices, Direct TV DVR's, slingbox, etc.

So it isn't as simple as you have imagined, but your post was very informative nonetheless.

And thus answers to the subnet question are definitely interesting.

---

### Post by SeijiSensei on 2014-03-02
I do my banking online; I have a few qualms about doing so, but my network isn't one of them.  I'm always more concerned about trusting institutions beyond my control.  IT security is generally underfunded by corporations since it's seen only as a cost.  Lax security at Sony required us to cancel a credit card after its [Playstation Network was cracked]("http://www.theguardian.com/technology/gamesblog/2011/apr/27/playstation-network-hack-sony").

My house has a couple of servers, a PS3, a "smart" TV, some workstations, and Android phones, all connected to my network.  I don't see any of this as a security threat.  The most vulnerable device is the wifi router.  I use WPA encryption with a complete mixed-case sentence including punctuation as a pass-phrase.  It's both personally memorable and unlikely to be in a [rainbow table]("http://en.wikipedia.org/wiki/Rainbow_table").

I just used the invaluable tool [nmap]("http://insecure.org/nmap/") (available from the repositories) to scan my external router from the Internet.  I ran the scan from a server on the Net to which I have access, but not one I have granted any special permissions on my router.  After five minutes of "stealth" scanning by nmap, not one of the 1,680 tested ports was open.  This is a stock router from Verizon with no additional hardening.

I have another router running [dd-wrt]("http://www.dd-wrt.com/") behind that one.  It provides my actual network services, both wired and wireless.  That router handles DHCP address management and includes a custom static route for connections to my online servers.  That traffic is forwarded to a server on my network which maintains an OpenVPN tunnel with my server at Linode.  That local server also provides private DNS resolution on the local network and handles all my mail.  

From the point of view of machines on my local network, the Verizon router is just another hop between them and the Internet.
```

Seiji@GhostWorld:~$ traceroute -n 8.8.8.8
traceroute to 8.8.8.8 (8.8.8.8), 30 hops max, 60 byte packets
 1  192.168.0.1  4.216 ms  4.165 ms  4.165 ms     (ASUS router with dd-wrt)
 2  192.168.1.1  4.168 ms  4.145 ms  4.112 ms     (Verizon router at my house)
 3  96.252.37.1  12.996 ms  15.517 ms  15.529 ms  (Verizon router upstream)
    [ The Internet ]
15  8.8.8.8  43.514 ms  39.743 ms  39.593 ms

```

That's my home network in a nutshell.  I'm not protected against a physical wiretap, or even a malicious piece of Javascript downloaded in the background to Firefox.  I have some protections against those in my browser, and I generally don't browse the back alleys of the Internet where malware lurks.  I will say that the only time my browser was compromised by a Javascript was when I tried to close it after reading the *New York Times!*  All of a sudden [Antivirus 2010]("http://www.pcworld.com/article/159974/supposed_antivirus_program_spreads_malware.html") appeared and told me I had all sorts of infected "DLL" files residing in C:\Windows that needed cleaning.  Seeing as I was on an Ubuntu machine, I laughed out loud.

---

### Post by Odyssey1942 on 2014-03-02
SS, I have every confidence that your system, whatever it might consist of, is hardened, very hardened. That happened because you have the knowledge and understanding to make it so. OTOH, I am only a beginner, and just beginning to get a glimpse into the complexity that may take years of gaining understanding, to begin to successfully address. So all my questions are from behind a veil through which I cannot see clearly, but they do come from thinking about, and trying to find solutions to those mysterious, and not understood, problems.

If subnets can help isolate our house guests, who use our WiFi, from any problems that they might generate, all the better. There are probably much better solutions of which I don't have the benefit of an insight or a clue (as in the subnet tidbit) yet, but I keep asking, and learning, and am very grateful for your guidance, as for those of others. Mine was not at all intended to be critical of you.

---

### Post by SeijiSensei on 2014-03-02
I didn't feel criticized at all.  I was trying to give you an idea of the sorts of questions I had when I was connecting things up in my house.  I hope it was helpful.

---

### Post by Odyssey1942 on 2014-03-03
Having had a bit of time to think about the description of your set-up, I have a couple of questions that I think are still within the scope of this thread. If not I can start a new one.

1) Do you have the second router because you do not feel that the Verizon router can give you either the control or the security that you want from your router? (Since it did not show an open port after 5 minutes of nmap scanning, it must be pretty good? Or is that because of the setup behind the Verizon router?)

2)```
 I use WPA encryption with a complete mixed-case sentence...pass-phrase
``` From context, this is in your WiFi access point, no? If so, is this  pass-phrase for access by users, or the admin pass-phrase? I assume the former, but if not, is the pass-phrase you have for user access similarly complex? OTOH, if so, do you have a similarly complex pass-phrase for admin access?

```
I have another router running dd-wrt behind that one. It provides my actual network services, both wired and wireless.  
``` 

3) dd-wrt to give you improved capability/performance of the router, or what? 

4) I assume that you prefer not to have PnP (I may not have that right, but it's the automated, easy admission for users thingy) enabled? If so, is that another reason for dd-wrt?

5) do you have PnP on your WiFi access point?

```
That router handles DHCP address management ....
``` 

6) I believe I understand enough about DHCP to think that this would be necessarily handled by the second router, but if not please elaborate on this

```
...and includes a custom static route for connections to my online servers. That traffic is forwarded to a server on my network which maintains an OpenVPN tunnel with my server at Linode. 
```

7a) Not trying to be nosy, but wanting to better understand your setup, are your "online servers" handling functions unrelated to your home network (i.e. for business purposes, or ?) If wrong, how to they augment your home network?

7b) Is this server maintaining the OpenVPN tunnel a sole purpose device, and if so, virtual or mechanical? If not, what other functions does it serve?

```
That local server also provides private DNS resolution on the local network....
``` 

8) I don't understand this, could you please elaborate a bit? I thought DNS was something provided by a worldwide network of public servers for this purpose. Is yours to speed up the process for the ones that you frequent or what? (I.e., sort of a caching function?)

```
....and handles all my mail.
``` 

9) So you have your own mail server and I assume for a domain that you control so that mail comes from "yourname@SeijiSensei.com" or whatever? Do you do this in preference to an online service such as gmail.com for any particular reason?

I have numbered all of the above to facilitate your reply. Apology for the long list, but really want to better understand yours for the purpose of learning from it. If any of it you do not wish to comment on for any reason, no problem.

---

### Post by SeijiSensei on 2014-03-03
> **Odyssey1942 said:**
> Having had a bit of time to think about the description of your set-up, I have a couple of questions that I think are still within the scope of this thread. If not I can start a new one.

1) Do you have the second router because you do not feel that the Verizon router can give you either the control or the security that you want from your router? (Since it did not show an open port after 5 minutes of nmap scanning, it must be pretty good? Or is that because of the setup behind the Verizon router?)
Partly it is "defense-in-depth," partly it's because I don't like mucking around in my ISP's router.

> 2)From context, this is in your WiFi access point, no? If so, is this  pass-phrase for access by users, or the admin pass-phrase? I assume the former, but if not, is the pass-phrase you have for user access similarly complex? OTOH, if so, do you have a similarly complex pass-phrase for admin access?
I use the web GUI for administrative access.  That password is unique.  The long pass-phrase is the one required for anyone to use the access point.  Since most devices will remember the pass-phrase, users only need to enter it once.

> 3) dd-wrt to give you improved capability/performance of the router, or what? 
dd-wrt is a Linux derivative so I'm comfortable with that.  It also offers a variety of more advanced controls than ordinary home routers.

> 4) I assume that you prefer not to have PnP (I may not have that right, but it's the automated, easy admission for users thingy) enabled? If so, is that another reason for dd-wrt?
UPNP can be a major security hole; I have nothing that requires it.  Do you?  I certainly wouldn't enable UPNP just to make life convenient for guests.

> 6) I believe I understand enough about DHCP to think that this would be necessarily handled by the second router, but if not please elaborate on this
Yes, the ASUS router faces the local network and handles DHCP.

> 7a) Not trying to be nosy, but wanting to better understand your setup, are your "online servers" handling functions unrelated to your home network (i.e. for business purposes, or ?) If wrong, how to they augment your home network?
Yes, the servers at Linode provide public services like web hosting and email.  The one with OpenVPN acts as a hub for a number of tunnels I have running in different locations.  They enable me to see machines behind a client's firewall, for instance.

> 7b) Is this server maintaining the OpenVPN tunnel a sole purpose device, and if so, virtual or mechanical? If not, what other functions does it serve?
No, as I said it handles mail and local DNS.  It also runs Samba and NFS in parallel for file and printer sharing.

> 8) I don't understand this, could you please elaborate a bit? I thought DNS was something provided by a worldwide network of public servers for this purpose. Is yours to speed up the process for the ones that you frequent or what? (I.e., sort of a caching function?)
I have a domain (actually a number of them).  My public DNS server resides on the virtual machines at Linode.  The server in my house has a different set of host-to-address mappings for the same domain that point to local resources. On the public internet, mail.mydomain.com points to a server at Linode.  At home, that name points to the local server.  It also does caching of requests, of course, but that's not it's primarily purpose.

> 9) So you have your own mail server and I assume for a domain that you control so that mail comes from "yourname@SeijiSensei.com" or whatever? Do you do this in preference to an online service such as gmail.com for any particular reason?

I've run my own mail, and some mail services for clients, since 1995.  I also manage email listservers that run on my mail servers.  I have no reason to change.

---

### Post by CharlesA on 2014-03-03
> **SeijiSensei said:**
> 
dd-wrt is a Linux derivative so I'm comfortable with that.  It also offers a variety of more advanced controls than ordinary home routers.

I am in total agreement with this one, I got started with dd-wrt on a Linksys 54G, moved to a Dlink DIR-615 and now I'm using an Asus RT-N16. So far it blows away the stock firmware or maybe I am just spoiled because it offers features the stock firmware lacks. Hmm.


> UPNP can be a major security hole; I have nothing that requires it.  Do you?  I certainly wouldn't enable UPNP just to make life convenient for guests.

Agreed. I leave it turned off even though I have people tell me you "need" it if you are going to be downloading a torrent or streaming content. I've had no issues.

My set up is similar as far as public web/email/whatever, but I haven't gotten around to getting a full blown DNS server set up at home for testing, so I've been using dnsmasq off the dd-wrt box.

I think the key, like with anything, is compartmentalization. One server runs mail, one server is for the web site, etc.

---

### Post by Odyssey1942 on 2014-03-03
Are these virtual servers or stand alone hardware? If separate computers, that could result in lots of computers running constantly. What would be the disadvantage/s of virtual?

If the answer is complicated, then disregard this question, but I don't understand the purpose of DNS servers within the LAN. As I understand it a DNS server translates a name (e.g., google.com) into an IP # which is how the request gets transmitted over the Internet. In my mind, these servers are "public resources" that are just available out there on the Internet. What is the purpose of having your own?

I have also read that turning UPNP "off" may not be totally effective in eliminating the security risk from having it in the router. Does dd-wrt eliminate UPNP? In answer to SS, I do not regard signing into a WPA/WPA2 access point as a big challenge, and so do not value UPNP, even if it is maybe slightly more convenient for guests.

TIA.

---

### Post by CharlesA on 2014-03-03
> **Odyssey1942 said:**
> Are these virtual servers or stand alone hardware? If separate computers, that could result in lots of computers running constantly. What would be the disadvantage/s of virtual?

If you are asking me, I have one dedicated server (at home), and the rest are virtualized. My VPSes are hosted at RamNode, and are accessible from the public internet, where my home box isn't accessible from the internet at all.

> If the answer is complicated, then disregard this question, but I don't understand the purpose of DNS servers within the LAN. As I understand it a DNS server translates a name (e.g., google.com) into an IP # which is how the request gets transmitted over the Internet. In my mind, these servers are "public resources" that are just available out there on the Internet. What is the purpose of having your own?

Testing. I do a bunch of testing locally before pushing things to production and if you are dealing with SSL certs or the like, that are signed for a specific domain, you will get errors if you do not access the server with that domain. By using a local DNS server set up, you can tell your local machines to connect to the local test machine instead of the public one because the DNS server will have an entry for the local machine and not have to query an external DNS server to get that information.

Also, caching DNS lookups can speed up your browsing.

> I have also read that turning UPNP "off" may not be totally effective in eliminating the security risk from having it in the router. Does dd-wrt eliminate UPNP? In answer to SS, I do not regard signing into a WPA/WPA2 access point as a big challenge, and so do not value UPNP, even if it is maybe slightly more convenient for guests.

dd-wrt still has a setting for UPnP, but it is disabled by default. I don't know why there would be a different between having it disabled and having it not installed in the first place unless the router gets compromised somehow (weak wireless key, default passwords, etc).

---

### Post by SeijiSensei on 2014-03-04
I have one physical server at home and two virtual servers at Linode.

As for DNS, it's quite common for organizations to run a private DNS server in-house that maps to local resources.  In Windows shops using Active Directory, it's pretty much the norm since AD manages DNS for all the machines in a domain.

I don't employ Charles's one-function-per-server rule.  The very first Linux servers we built ran on Dell i386 hardware and handled web, mail, DNS, and firewalling.  Machines were so expensive at the time ($2-3,000 for the hardware alone) that deploying multiple servers was not cost-effective.  Of course, in 1995-1997 no one could imagine a virtual machine running on anything other than an IBM mainframe.

---

