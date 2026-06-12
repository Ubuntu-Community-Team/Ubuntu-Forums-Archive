---
title: "My router got hacked again for 3 times this year"
date: 2011-11-03
forum: Security
---

### Post by nec207 on 2011-11-03
In the past year I have gone through 3 routers !! It keeps getting hacked.If not the user name and passwords changes , routers name or firmware changes.:(
 
I have seen lights on the router and modem go cracy with no on on the internet !!! Now when I try to log in the router it saying server log in !!! I have not set up any server !! 
 
What is going one.
 
 
I don't think I'm securing the router the proper way 
 
 
So my question how do you secure the router and what programs do you have running to make sure it is secure? What are good routers to buy ? Some routers say it has firewall and security . How do I know what is good firewall and security the routers has. 
 
What should I be looking for in good firewall and security.
 
 
This all started after I move to a apartment building in a densely packed neighborhood by 3 high schools .Yes I change the routers name and user name and passwared to log into the routers setting so not sure how this happend.

---

### Post by SparTacux on 2011-11-03
What model of modem router have you got?
Did your ISP provide your router? - Do they upgrade the router via remote management?

Have you done any firmware updates yourself by downloading firmware from a download site?

Does the router have any remote management enabled - usually port 8080?

Do you access the internet via wireless connection and if so what wireless security protocols are you using?

---

### Post by nec207 on 2011-11-03
>  
What model of modem router have you got?
 
Did your ISP provide your router? - Do they upgrade the router via remote management?
 

netgear router
modem motorola the ISP gave me.
 
>  
Have you done any firmware updates yourself by downloading firmware from a download site?
 

 
no should I ?
 
>  
Does the router have any remote management enabled - usually port 8080?
 

not sure ?
 
> Do you access the internet via wireless connection and if so what wireless security protocols are you using?
 
It is a wireless router.

---

### Post by dFlyer on 2011-11-03
My first response, did you change the default router admin/password when you set up the router? If you didn't most default login is admin for the name and password for the password which will allow anyone to access the router.

---

### Post by VeeDubb on 2011-11-03
> **nec207 said:**
> It is a wireless router.

It could be that you've just had really bad luck with routers and they've failed, not that they've actually been hacked, but it does sound more like your neighbors are hacking you to steal internet.

What security protocol are you using for your wireless connection?  WEP, WPA?  If you're using WEP, you need to switch to WPA.  WEP is incredibly easy to break.

---

### Post by Goldiescorpio on 2011-11-03
I also think someone is just playing with you.
Like stated by others, change the admin password and wireless security to at least WPA, better WPA2...

Just reset your router, push a pin in the hole for like 10seconds, probably all lights will be shining and then let go of it and it resets and reboots. Immediately change admin Passw and Wifi security.

You can also enable mac filtering so only devices YOU add can access the network.

Good luck!

Grtz!

---

### Post by nec207 on 2011-11-03
> **VeeDubb said:**
> It could be that you've just had really bad luck with routers and they've failed, not that they've actually been hacked, but it does sound more like your neighbors are hacking you to steal internet.
 
What security protocol are you using for your wireless connection? WEP, WPA? If you're using WEP, you need to switch to WPA. WEP is incredibly easy to break.
 
 
It is WPA 2.
 
Do you think I used a weak password.
 
now I have to reset the router or get new one has I cannot log into the router.The other time the routers name got changed.
 
And what is up with this server log in ? I have set up no server.

---

### Post by Goldiescorpio on 2011-11-03
Maybe there is a function to set up a webserver? Mine has...
Reset and do the things stated above and you will be relatively safe...

GL

Grtz!

---

### Post by nec207 on 2011-11-03
> **Goldiescorpio said:**
> Maybe there is a function to set up a webserver? Mine has...
Reset and do the things stated above and you will be relatively safe...
 
GL
 
Grtz!
 
It is a cheap router and it does not say firewall on the box ? what firewall should the router have and how should the firewall work.

---

### Post by Goldiescorpio on 2011-11-03
Nec207,

Can you pêrhaps specify the router type it is a netgear ....
So I can look up the specs and try to help you any further.

Grtz

---

### Post by Goldiescorpio on 2011-11-03
There is no different section/page/tab in your router where you can enable/disable the firewall?

Grtz!

---

### Post by nec207 on 2011-11-03
> **Goldiescorpio said:**
> There is no different section/page/tab in your router where you can enable/disable the firewall?
 
Grtz!
 
How does this work? My router does not have a firewall.

---

### Post by Dangertux on 2011-11-03
I'm tempted to make a joke about the router not being sandboxed...However, that would just be rude ;-)

That being said. Basic wireless security dictates the minimum.

- Strong Admin Password
- Strong User Password (if your router supports it)
- Disable UPNP
- Disable WPM (if you don't need it)
- Locate the router so the signal isn't ridiculously strong outside of your house.
- Enable Logging in to the router only over HTTPS (if it supports this)
- Disable remote administration (administration from the outside world , defaulted to port 8080 usually)
- Disable the telnet server if it has one
- Disable the TFTP server if it has one.
- You can toss in MAC address filtering, but it's really a waste of time. 
- WPA/WPA2 with a strong pass phrase (use all 63 characters)

Hope this helps.

---

### Post by 1clue on 2011-11-03
First, I'm assuming you have a relatively recent router.  Wireless G or later.

Flash upgrade:  Go to the web site for the router, see what firmware upgrades are available and if anything applies to you then go get it.  One side effect of that is that it resets all the settings to default values, so you wipe out whatever somebody did.

Reset to defaults:  Do a 30-30-30 reset:
[LIST=1]
[*]Start with power on and everything running.
[*]Hold the hardware reset button for 30 seconds.  Do not let go.
[*]While still holding the reset, pull the power cord out.  Continue holding the button and count another 30 seconds.
[*]Plug it back in, while still holding the reset button.  Wait another 30 seconds.
[*]Release the reset.
[/LIST]

That reset process will wipe the settings of pretty much any wireless router out there.  You then have to use the default password and reconfigure everything.

[LIST=1]
[*]Plug in your workstation to the router using a physical cable.
[*]Go to [http://192.168.1.1](http://192.168.1.1)
[*]Enter default password (admin/admin usually works)
[*]Make it so you cannot administer the router from the Internet.
[*]Make it so you cannot administer the router from wireless.
[*]Use a strong password.  I generate a dsa encryption key and copy out about 15-25 characters of that, memorize it and it's my password. I have several of them I rotate through so every password changes in a reasonable amount of time, only a few accounts can be reached by any one password and I don't need to remember one ridiculously complicated password for each account.
[*]Do not use the default wireless keys.  Usually there is a button to generate new ones, so it's not like you need to make up your own.  Just don't use what came with the system.
[*]Do not use passwords/WEP keys/whatever that are based on words in any language, no matter how mangled.
[*]If possible, change the administrative username.
[*]Go through the features.  If you don't need it, turn it off.
[*]If you allow anonymous access to your network, make sure it only gives access to the Internet, not the rest of your network.
[/LIST]

---

### Post by SparTacux on 2011-11-03
The worst case scenario is that someone logged into your router using default admin password then enabled remote managment and maybe even downloaded a compromised firmware update for further use. 

If in doubt do factory reset as already mentioned. Set new password. Maybe do a firmware update just to be sure.

---

### Post by 1clue on 2011-11-03
By the way, my password policy applies to workstations on the network as well.

If you have inane passwords on any account on your system, and especially if you have a cheat sheet like "passwords.txt" or anything equally obvious, you'd just as well open everything up and let the world have your credit cards.

If somebody on your network has weak passwords, then make sure they can't change any security settings on anything at all.  You can't protect them from themselves, but you CAN protect yourself from them.

---

### Post by SparTacux on 2011-11-03
Here's an interesting article to wet your appetite


NEW WORM CAN INFECT YOUR MODEM / ROUTER
[http://apcmag.com/Content.aspx?id=3687](http://apcmag.com/Content.aspx?id=3687)

Netgear is on the list.  I suspect my modem router was compromised donkeys ago  ;-)

How would you sniff & inspect traffic on compromised modem. Maybe some sort of wire tap device between modem and phone line?

---

### Post by SparTacux on 2011-11-03
It could be worthwhile doing a nmap scan on both the LAN and WAN side of your router to check for open ports.

I have a cheap modem router and you can scan the LAN side of it by scanning the IP of the gateway address which is in my case 192.168.0.1. The command to scan my modem is:

nmap -PN -p- 192.168.0.1

The results from this nmap scan is:

Starting Nmap 5.00 ( [http://nmap.org](http://nmap.org) ) at 2011-11-03 22:22 GMT
Interesting ports on 192.168.0.1:
Not shown: 65528 closed ports
PORT      STATE    SERVICE
80/tcp    open     http
1863/tcp  filtered msnp
5050/tcp  filtered mmcc
5190/tcp  filtered aol
32764/tcp open     unknown

HTTP 80 is open so I can log in to the router with my password and access the web interface from my computer. I haven't a clue what port 32764 is for - HELP  ;-)

You could also scan the WAN side of your router from the internet and do a full port scan in a similar way. You'd need a computer with a dongle to do that or use somebody else's computer and scan your router from there. Check it out and see what ports are open. If remote management is disabled then I presume you won't find port 8080 open, etc.

I'm curious if a compromised router ( with a compromised firmware change )  would give false firewall data to SYSLOG etc.  Not too sure of what other exploits you could achieve with a compromised router - maybe installation of password sniffers, etc. I'll leave that to your imagination. :-)

---

### Post by nec207 on 2011-11-03
> **SparTacux said:**
> The worst case scenario is that someone logged into your router using default admin password then enabled remote managment and maybe even downloaded a compromised firmware update for further use. 
 
If in doubt do factory reset as already mentioned. Set new password. Maybe do a firmware update just to be sure.
 
 
The router has no firewall . It is a very cheap router . It is a netgear wireless N-150 router WNR1000
 
 
My Passward was quote of one of the robocop movies. So the passward was 16 characters with no space.
 
Like some one trying to read MyPasswardwasquoteofthe with no space !!! Hard to do.
 
 
Do I need a Cisco router? Are these netgear and Linkesys routes typical customer junk that have no firewall or security.

---

### Post by 1clue on 2011-11-03
Chill out about the firewall thing.

The cheapest routers do one of two things:
[LIST=1]
[*]Map everything to a 192.168.x.y network and not allow anything at all to originate from the Internet.
[*]Straight map one IP address, so your computer directly connects to that and must act as the router.
[/LIST]

From the sound of it, you're the first category.  If you have a 192.168.x.y address then that's what is going on.  If you have some other address which does not fall into the private network ranges, then you would be complaining about your directly connected system being hacked, not your router.

I would be hesitant to run NMAP through the Internet.  At least some ISPs watch for that sort of thing.  You can tell them you're testing your own equipment and that will remove legal problems, but they don't like that sort of activity anyway.

---

### Post by 1clue on 2011-11-03
Look on page 2-22 of your manual.

---

### Post by Goldiescorpio on 2011-11-03
Your manual is [here]("ftp://downloads.netgear.com/files/WNR1000_SM_WW_23Jan09.pdf") ;-)

---

### Post by iavor on 2011-11-03
If you follow Dangertux and 1clue steps on securing your router, you will be fine. 
I find that keepass password generator to be very good at generating extremely strong passwords.

EDIT: If you think your router is that bad.. you can start looking for alternatives. I personally prefer router that's capable of flashing to DD-WRT or Tomato.

---

### Post by CharlesA on 2011-11-03
> **iavor said:**
> If you follow Dangertux and 1clue steps on securing your router, you will be fine. 
I find that keepass password generator to be very good at generating extremely strong passwords.

EDIT: If you think your router is that bad.. you can start looking for alternatives. I personally prefer router that's capable of flashing to DD-WRT or Tomato.
+1 on both accounts.

---

### Post by 1clue on 2011-11-03
I don't think it's really an old router.  Just a lower end one.  If I'm not mistaken I saw one still on the shelf at Fry's a day or two ago.  It's wireless N.

To be perfectly honest, I think the low function home routers are safer than most higher function ones, once you start monkeying with settings.  The default settings almost always deny any externally initiated sessions and that's the biggest group of "enemies" out there.

All you really need to do is tighten down the wireless side and you're pretty good.

BTW, -1 on dd-wrt.  It's the most closed open-source project I know of.  The main developer does virtually nothing and doesn't accept changes from anybody.  I waited around for forever to get an update that was more functional and finally re-flashed my OEM firmware in disgust.

---

### Post by CharlesA on 2011-11-03
> **1clue said:**
> 
BTW, -1 on dd-wrt.  It's the most closed open-source project I know of.  The main developer does virtually nothing and doesn't accept changes from anybody.  I waited around for forever to get an update that was more functional and finally re-flashed my OEM firmware in disgust.

Aye. I haven't really seen much development on it. I'm running it on my DIR-615 but that's mostly cuz I didn't really like Tomato.

---

### Post by nec207 on 2011-11-03
>  
Chill out about the firewall thing.
 
 

The cheapest routers do one of two things: [LIST=1]
[*]Map everything to a 192.168.x.y network and not allow anything at all to originate from the Internet.
[*]Straight map one IP address, so your computer directly connects to that and must act as the router.QUOTE]
[/LIST]
What do you mean? I think what some people mean by buying a good router with good firewall is the router that will lock all traffic but the appropriate computers the admin sets up for the router only and no other computers can use that router and the use of logging .
 
Meaning if people are hacking my router ,unauthorized use of the router ( by not improved computer) or trying to log into the router by password guessing it will alert me.
 
sorry this router does not do that.
 
 
It is no different than people who try to hack the NSA or CIA you leave bread crumbs when one tries to hack that they can easy find you. But I do not have a cisco router that can do that or I would have done a IP trace on the hacker and know who is doing that.
 
My routers does not alert me or has that feature to alert me when there is unauthorized use of the router ( by not improved computer using the router ) or trying to log into the router settings by password guessing .
 
Look the routers does not even alert me if there is port scanning going on.

---

### Post by 1clue on 2011-11-03
I was really hoping for a positive note on Tomato.  I haven't tried it but was hoping it was at least somewhat better than dd-wrt.

I don't really like the Cisco/Linksys firmware that much on my WRT610n, but as yet I don't see a lot of options.  I just picked up an E4200 for the office and that at least has IPV6, but that's not much consolation for home.

---

### Post by 1clue on 2011-11-03
> **nec207 said:**
> What do you mean? I think what some people mean by buying a good router with good firewall is the router that will lock all traffic but the appropriate computers the admin sets up for the router only and no other computers can use that router and the use of logging ....


My Cisco doesn't do any of that either.

When you're talking about a "good" home or small business wireless router, you generally mean lots of features and reasonably easy configuration.

Really, as far as your situation goes, you want two things:
[LIST=1]
[*]You want to be able to access the Internet from your home.
[*]You want to keep your router and your network secure enough to prevent the bad guys from owning your stuff.
[/LIST]

You haven't mentioned needing a VPN or complex remote access to your local network.

Your router does something that is called IP masquerading.  You are probably getting an IP address of 192.168.x.y, or 172.16.x.y, or 10.x.y.z.  Those are reserved private network allocations, meaning that they will never be routed to the Internet.  Somebody from the Internet, in other words, cannot access one of your computers unless you specifically arrange for that to happen.

In your case, your router does some of that but not much of it.  If you leave your settings alone, your home network is probably safe from any reasonably expected attacks.  If the CIA wants the junk on your hard drive you might be in trouble, but in that case they'll probably come through the door anyway.

When you start adding features to the mix and turning those features on, then suddenly there's a whole lot more code to protect, and a "good" appliance will safely protect what you are exposing.  Since you aren't exposing anything you don't need to worry about it and your cheap router is fine.

Likewise, when I and others on this thread are telling you to turn things off that you don't need, we're doing so specifically because what is not there can't be hacked.  If you leave it running you either have to tolerate the risk or you have to address each security problem, which you don't know how to do.  So turn it off and you won't need to worry about it.

FWIW, my Cisco has a whole lot more features than yours does, and really only one of them is turned on.  Everything else is turned off because I don't want to have to worry about it.

All the important-but-basic stuff like an encrypted wireless network and such your router has.  Turn it on, that stuff is good because it's providing extra security and has little or no security exposure.

This stuff you're talking about in your post is something that SOME businesses put in place.  Stateful packet inspection is something I've read up on but have no real reason to implement.  It's much more trouble than the data on my network is worth.  Brute force attacks, well that could happen if you have a sophisticated neighbor through your wireless, but if you leave all the access-from-the-Internet features turned off you really won't likely see anything come from there.

---

### Post by nec207 on 2011-11-03
>  
This stuff you're talking about in your post is something that SOME businesses put in place. Stateful packet inspection is something I've read up on but have no real reason to implement. It's much more trouble than the data on my network is worth. Brute force attacks, well that could happen if you have a sophisticated neighbor through your wireless, but if you leave all the access-from-the-Internet features turned off you really won't likely see anything come from there.

 
wow I thought a good router with good firewall does that ? Is that not the meaning of firewall.
 
Back in the old days when I was using windows 98 I used zone-alarm dam that thing was good .I use to love what zone alarm did . Just try port scanning or trying to connect to my computer and I would get a pop up.
 
 
 
> When you start adding features to the mix and turning those features on, then suddenly there's a whole lot more code to protect, and a "good" appliance will safely protect what you are exposing. Since you aren't exposing anything you don't need to worry about it and your cheap router is fine.
 
 
What features do you mean? The only features we need is to lock down the router and the network and have some firewall and reporting of the packets going in and out of the router and on the network  ( LAN ) .
 
So I can see all traffic and analyze the punk on the street doing this too me.

---

### Post by 1clue on 2011-11-03
If you start talking to business IT types, there's not really a single consistent definition of "firewall."  Conceptually it's simple.  Keep the bad stuff out so you can have a safe network.  Realistically the way to do that depends greatly on what you're trying to protect, what you're trying to let through, how big your network is and what sort of traffic you get.

Stateful packet inspection generally means you're using a proxy.  That's software which doesn't simply forward a packet, it accepts packets on a certain port or set of ports, inspects them for validity, logs whatever you're interested in and then forwards the packet to a different interface.  Or does absolutely anything else you want to do with it.

All the proxies I've had contact with were a separate device from what was referred to as the "firewall."

Generally I see this sort of thing:
[LIST=1]
[*]Router.  This is an analog of your cable modem.  It doesn't do anything except connect you to your ISP.  Commercial models allow monitoring, failover and remote configuration.
[*]Packet filter.  What most people think of as a "firewall."  It accepts, rejects or denies traffic based on the contents, origin or destination of single packets.  Commercial models allow monitoring, failover and remote configuration as well as a whole lot of other things based on who built it.
[*]Proxy.  Handles monitoring and security based on sessions in addition to anything the packet filter might handle.
[*]VPN endpoint.  Handles encrypted tunnels to/from some remote location or locations.
[*]Switch.  Splits traffic into networks and handles high-speed routing between machines.  Also can have failover and all sorts of rules similar to what a packet filter might have.
[/LIST]

On a large network, they generally have each of those things as separate hardware.  On an Enterprise network you might have an arrangement that doesn't really fit into any of those categories.

You have more security if you layer your security.  That way if the bad guys break into your outer defense, they still have a long way to go to get to the inner defense.  The advantage of a proxy or separate packet filter is that the software available on it is limited and very difficult to use to hack into the network it protects.  Because of that the bad guy not only needs to breach the security of the device, they need to install new software on it and convince it to execute that software in a way they can control.

---

### Post by 1clue on 2011-11-03
Sorry if I sound like I'm avoiding your answers.  If you read up on security, you find out that there's a whole lot of generalizations when you talk about strategy and crystal clarity when you talk about specifics.

Yes, you can get logging and alarms and all sorts of neat stuff.  The way you get that stuff varies wildly from manufacturer to manufacturer.

The commercial Cisco gear I managed had the ability to mirror one ethernet port over to another read-only port.  We hooked the PIX to the main port and a PC up to the mirror port.  The PC ran some commercial software to make sense of what was going through the PIX.  That machine was reachable through another network card to the IT staff and that's how we handled all the alarms and such.  The Cisco gear didn't have anything to do that directly.

---

### Post by Dangertux on 2011-11-03
Don't confuse the definition of Stateful Packet Inspection with Deep Packet Inspection.

SPI looks at a packet to make sure it conforms to standard rulesets for establishing a connection or data stream. Often times SPI is made out to be "better" than it actually is. 

DPI on the other hand will in fact look at the data in the packet and match it against known malicious data signatures and block or allow based on that. This is likened to IPS.

Hope that helps.

---

### Post by 1clue on 2011-11-03
I haven't had any exposure to DPI.  Is that done as a stream-based measure or as a packet-based measure?  Or both?

---

### Post by Dangertux on 2011-11-03
They're usually done on a stream level since concurrent packet matching reduces false positives. Packet by packet matching is still possible, though most sysadmins shy away from it since a smart attacker will just fragment anyway to bypass it.

---

### Post by nec207 on 2011-11-04
>  

Generally I see this sort of thing: [LIST=1]
[*]Router. This is an analog of your cable modem. It doesn't do anything except connect you to your ISP. Commercial models allow monitoring, failover and remote configuration.
[*]Packet filter. What most people think of as a "firewall." It accepts, rejects or denies traffic based on the contents, origin or destination of single packets. Commercial models allow monitoring, failover and remote configuration as well as a whole lot of other things based on who built it.
[*]Proxy. Handles monitoring and security based on sessions in addition to anything the packet filter might handle.
[*]VPN endpoint. Handles encrypted tunnels to/from some remote location or locations.
[*]Switch. Splits traffic into networks and handles high-speed routing between machines. Also can have failover and all sorts of rules similar to what a packet filter might have
[/LIST]
 
Most of the things you listed my router does not do.

---

### Post by Rodney9 on 2011-11-04
You can check your ports here - [https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)

---

### Post by SparTacux on 2011-11-04
> **Rodney9 said:**
> You can check your ports here - [https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)


That's a pretty good way of testing the WAN side of your router without any legal issues from your ISP. 
Good call.

Allow Shields up to do a full port scan.

If I attempted this on my system my router SHOULD block all incoming traffic since I have a deny all incoming connections rule by default. If remote management is enabled ( port 8080 by default ) then shields up should spot it and report the port as OPEN?

---

### Post by SparTacux on 2011-11-04
> **1clue said:**
> 
BTW, -1 on dd-wrt.  It's the most closed open-source project I know of.  The main developer does virtually nothing and doesn't accept changes from anybody.  I waited around for forever to get an update that was more functional and finally re-flashed my OEM firmware in disgust.

If one guy can reverse engineer a router and provide an alternative firmware then so can anyone with the right skills and knowledge. I suspect Governments ( with huge financial budgets ) are capable of doing this too. Hacking modems/routers COULD BE  more common than one thinks? I'm trying to get my head around the possibility that it could be done and what you could actually achieve by hacking a modem. Second thoughts are how you would check the modem/router to see if it has been hacked - how would you rootscan a modem? Many of these are Linux systems in themselves. How could someone check the firmware to see if it legit or not?

From an hackers point of view you could throw in software to modify packets to crash networks and cause denial of Service or maybe corrupt packets that exploit known vulnerabilities on the target computers on the network ( In this case Ubuntu ). This is all conjecture and bordering on Paranoia - but still possible?

---

### Post by Dangertux on 2011-11-04
> **SparTacux said:**
> If one guy can reverse engineer a router and provide an alternative firmware then so can anyone with the right skills and knowledge. I suspect Governments ( with huge financial budgets ) are capable of doing this too. Hacking modems/routers COULD BE  more common than one thinks? I'm trying to get my head around the possibility that it could be done and what you could actually achieve by hacking a modem. Second thoughts are how you would check the modem/router to see if it has been hacked - how would you rootscan a modem? Many of these are Linux systems in themselves.

From an hackers point of view you could throw in software to modify packets to crash networks and cause denial of Service or maybe corrupt packets that exploit known vulnerabilities on the target computers on the network ( In this case Ubuntu ). This is all conjecture and bordering on Paranoia - but still possible?

Possible yes. Plausible or likely, no. SOHO routers are a terrible target for that type of thing, largely because nobody cares and its much easier to get people on iframe based browser exploits.

Enterprise class routers don't work quite the same at the hardware level so it would be more difficult to make this type of attack work. 

In short, it's not worth the effort.

---

### Post by Thewhistlingwind on 2011-11-04
> **1clue said:**
> 

I would be hesitant to run NMAP through the Internet.  At least some ISPs watch for that sort of thing. 

Because only bad people use nmap. ;)

Silliness.

---

### Post by SparTacux on 2011-11-04
> **Thewhistlingwind said:**
> Because only bad people use nmap. ;)

Silliness.


Well - I'm gonna have to be really bad !

I tried GRC.Com and shields up and the scan all ports option only scans the first 1000 or so ports. If you want more than that it will allow you to scan ports you mention BUT only 64 ports at a time. You would have to spend hours doing it 64 ports at a time.

nmap to the rescue ;-)

---

### Post by SparTacux on 2011-11-04
> **Goldiescorpio said:**
> I also think someone is just playing with you.
Like stated by others, change the admin password and wireless security to at least WPA, better WPA2...

Just reset your router, push a pin in the hole for like 10seconds, probably all lights will be shining and then let go of it and it resets and reboots. Immediately change admin Passw and Wifi security.

You can also enable mac filtering so only devices YOU add can access the network.

Good luck!

Grtz!

Just to get this thread back on track - I'd go along with this.
All the hacked modem stuff is probably over the top in the case.

I suspect you are spooking yourself ( because you don't know what is happening ) or someone else is spooking you and maybe got access to your router via wireless and logged on and changed some settings or maybe you accidently allowed remote management and they got in that way. Maybe one of your computers is compromised and giving away details of wireless password and router logon password. There are a number of possible variables.

As far as getting a good router. Get one with logs that show who has accessed the router , One with a Firewall capable of loging all traffic in and out of it and sending that data to your computer via SYSLOG. Extra benefits would be details of attached computers, Network traffic details, etc. Many routers have this sort of stuff these days. 

Hope this helps

---

### Post by nec207 on 2011-11-04
>  
Generally I see this sort of thing: 
[LIST=1]
[*]**Router. This is an analog of your cable modem. It doesn't do anything except connect you to your ISP.** Commercial models allow monitoring, failover and remote configuration.
[*]Packet filter. What most people think of as a "firewall." It accepts, rejects or denies traffic based on the contents, origin or destination of single packets. Commercial models allow monitoring, failover and remote configuration as well as a whole lot of other things based on who built it.
[*]Proxy. Handles monitoring and security based on sessions in addition to anything the packet filter might handle.
[*]VPN endpoint. Handles encrypted tunnels to/from some remote location or locations.
[*]**Switch. Splits traffic into networks and handles high-speed routing between machines**. Also can have failover and all sorts of rules similar to what a packet filter might have
[/LIST]
 
 
I'm going to say only in bold is what my router can do.It is cheap router.It has no firewall or nothing.

---

### Post by haqking on 2011-11-04
> **nec207 said:**
> I'm going to say only in bold is what my router can do.It is cheap router.It has no firewall or nothing.

you said you have a  netgear wireless N-150 router WNR1000 in post #19

It does have a firewall.

People have posted the link to your manual.

Like the previous thread on security, you are not listening or reading what people post.

Your router has a firewall !

---

### Post by MrLeek on 2011-11-04
This might be a step too far for the OP at this moment in time, but does updating the firmware using DD-WRT make things more secure? 

Or is it just as safe (more so to be honest as it's hard to mess it up) to only use the official firmware upgrade? Assuming basic knowledge here I would say the latter...

---

### Post by CharlesA on 2011-11-04
> **MrLeek said:**
> This might be a step too far for the OP at this moment in time, but does updating the firmware using DD-WRT make things more secure? 

Or is it just as safe (more so to be honest as it's hard to mess it up) to only use the official firmware upgrade? Assuming basic knowledge here I would say the latter...

I wouldn't really say more secure per-say, but the reason I run it is because I wanted some features that the default firmware didn't have (local dns for one).

Flashing a third-party firmware can potentially brick your router and while it isn't exactly rocket science, bad things sometimes happen. I'd stick with the basic firmware in that case.

---

### Post by 1clue on 2011-11-04
> **nec207 said:**
> I'm going to say only in bold is what my router can do.It is cheap router.It has no firewall or nothing.

It has a firewall.  That's referenced along with other security measures on page 2-22 of your user manual.

You don't need a proxy or any of that other stuff.  You just need strong passwords and you need to prevent configuration of your device by wireless or internet.  Make sure it can only be configured through a local ethernet port.

The list I gave you that you quoted is what I see in businesses with 100+ people in them.

> **MrLeek said:**
> This might be a step too far for the OP at this moment in time, but does updating the firmware using DD-WRT make things more secure? 

Or is it just as safe (more so to be honest as it's hard to mess it up) to only use the official firmware upgrade? Assuming basic knowledge here I would say the latter...

No it doesn't inherently make things more secure.  DD-WRT is a Linux distribution for routers.  If you're a Linux hack, then you will be more familiar and you will be able to do the sort of things you can with Linux-based kernel routing.  You will also be susceptible to the stupid security mistakes that people make with Linux.  Nobody will be looking over your shoulder anymore to make sure things are right.  If you know what you're doing then you can make things secure.

---

### Post by Dangertux on 2011-11-04
I really think too much emphasis is being put on the firewall aspect here.

 Firewalls are great, but regardless of whether you are using Linksys Linux 2.4/6 (Pretty much any Cisco/Linksys SOHO router) , Dlink's version or DD-WRT you're basically just interfacing with netfilter/iptables anyway.

I'm not aware of any low end SOHO router (under $500) that will provide you any more functionality in terms of a firewall than any $50 router you can buy at Best Buy.

If you look at what a NAT router does in terms of a firewall you have a couple of basic things going on.

DNAT/SNAT  - this is what allows you to "share" your internet access. Which looks like this

```

iptables -A FORWARD -i eth1 -s 192.168.1.0/255.255.255.0 -j ACCEPT
iptables -A FORWARD -i eth0 -d 192.168.1.0/255.255.255.0 -j ACCEPT
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE

```Where 
192.168.1.0/24 iis our network 
eth1 is our LAN interface
eth 0 is our WAN interface

Port Forwarding - This goes hand in hand with the first, and basically allows you to forward inbound requests to the router, to the appropriate machine with the requested service. For instance a request to external ip on port 22 could be forwarded to 192.168.1.5 this would essentially look like this

```

iptables -t nat -A PREROUTING -p tcp -i eth0 -d $externalip --dport 22 -j DNAT --to 192.168.1.5:22
iptables -A FORWARD -p tcp -i eth0 -d 192.168.1.5 --dport 22 -j ACCEPT

```Where
192.168.1.5 is the machine hosting the SSH service
$externalip is our external interface's ip address
port 22 is the port we're forwarding.

That is the basic functionality provided by all SOHO routers. This is what makes a router a router. Additionally when they are referring to a "Stateful Packet Inspection" firewall they are referring to this line.

```

iptables -A INPUT  -m conntrack --ct-state  RELATED,ESTABLISHED -j ACCEPT

```This is basically going to insure that connections are solicited before allowing them to be completed. Of course this can be abused : [read here for how and why]("http://dangertux.wordpress.com/2011/10/03/a-firewall-is-not-a-catch-all/")

So when you really break it down none of the so called "firewalls" are really doing anything terribly amazing. Like I said if you get into IPS/DPI devices you are talking about hundreds of dollars if not more, and the odds of you having that in your home, are slim to say the least.

Some more expensive routers may do nifty things like apply iptables rate limiting to thwart port scans and brute force attacks, but really a smart attacker will slow down and fly right under the rate limiting if they really want to.

Another important thing to note about SOHO routers is the often misnomered DMZ , which actually stands for data management zone not demilitarized zone. Some cheaper routers essentially port forward  everything to the DMZ while the DMZ remains routable to the internal network. This is done because cheaper routers utilize two interfaces as opposed to three. A True DMZ will not be routable from the internal network. So if you can get this feature in a SOHO router it's actually worth the money if you're planning on running a server.

Another common misconception is that "having" a feature inherently increases your overall security. A VPN will do nothing for you unless you properly utilize it, of course that requires you even are in a situation where a VPN would benefit you. If you don't need or use it properly it's just another service to secure. 

All in all, you have to look at the practices by which you're securing your router before blaming its functionality or lack thereof. Hopefully this wall of text will be useful to someone.

---

### Post by nec207 on 2011-11-04
> **haqking said:**
> you said you have a netgear wireless N-150 router WNR1000 in post #19
 
It does have a firewall.
 
People have posted the link to your manual.
 
Like the previous thread on security, you are not listening or reading what people post.
 
Your router has a firewall !
 
I have seen no link in this thread to the manual or anyone replying to my post saying what my router can do or cannot do .
 
Or what this firewall can do so called my router has or basic firewall. 
 
It is inappropriate to bring the other thread into this thread.
 
On last note using passphrase ,user name or passward of quote of movie 16 to 32 characters is that okay or does it need to be longer like 32 to 64 characters .

---

### Post by Dangertux on 2011-11-04
> **nec207 said:**
> I have seen no link in this thread to the manual or anyone replying to my post saying what my router can do or cannot do .
 
Or what this firewall can do so called my router has or basic firewall. 
 
It is inappropriate to bring the other thread into this thread.
 
On last note using passphrase ,user name or passward of quote of movie 16 to 32 characters is that okay or does it need to be longer like 32 to 64 characters .

You really should read my last post...If you do you will find that by definition of what your router does it likely has a firewall. Unless they modified netfilter/iptables and removed all of the USEFUL features.

---

### Post by haqking on 2011-11-04
> **1clue said:**
> Look on page 2-22 of your manual.

> **Goldiescorpio said:**
> Your manual is [here]("ftp://downloads.netgear.com/files/WNR1000_SM_WW_23Jan09.pdf") ;-)

> **nec207 said:**
> I have seen no link in this thread to the manual or anyone replying to my post saying what my router can do or cannot do .
 
Or what this firewall can do so called my router has or basic firewall. 
 
It is inappropriate to bring the other thread into this thread.
 
On last note using passphrase ,user name or passward of quote of movie 16 to 32 characters is that okay or does it need to be longer like 32 to 64 characters .


Read the quotes above then and the rest of the posts about how to secure things.

In conjunction with your manual use the advice given.

---

### Post by CharlesA on 2011-11-04
> **nec207 said:**
> 
On last note using passphrase ,user name or passward of quote of movie 16 to 32 characters is that okay or does it need to be longer like 32 to 64 characters .

It is better to have a semi randomized passphrase since you only need to type it in once per device.

---

### Post by nec207 on 2011-11-04
>  

**Generally I see this sort of thing: **[LIST=1]
[*]**Router. This is an analog of your cable modem. It doesn't do anything except connect you to your ISP. Commercial models allow monitoring, failover and remote configuration. **
[*]**Packet filter. What most people think of as a "firewall." It accepts, rejects or denies traffic based on the contents, origin or destination of single packets. Commercial models allow monitoring, failover and remote configuration as well as a whole lot of other things based on who built it. **
[*]**Proxy. Handles monitoring and security based on sessions in addition to anything the packet filter might handle. **
[*]**VPN endpoint. Handles encrypted tunnels to/from some remote location or locations. **
[*]**Switch. Splits traffic into networks and handles high-speed routing between machines. Also can have failover and all sorts of rules similar to what a packet filter might have **
[/LIST]
 
 
 
 
> Read the quotes above then and the rest of the posts about how to secure things.
 
In conjunction with your manual use the advice given. 
 
 
I have but it does not explain in bold above what my router can do or cannot do.I'm reading that post above in bold and getting confused because I do not think my router does that.
 
That is why I will like some one here to look at it and read what is in bold above and explain what my router can do or cannot do in bold above. Do to I do not think my router does that what is bold above.

---

### Post by haqking on 2011-11-04
> **nec207 said:**
> I have but it does not explain in bold above what my router can do or cannot do.I'm reading that post above in bold and getting confused because I do not think my router does that.
 
That is why I will like some one here to look at it and read what is in bold above and explain what my router can do or cannot do in bold above. Do to I do not think my router does that what is bold above.

Well i am not researching your model of router, but from a previous glance it does them all.

As do most home routers these days

---

### Post by Dangertux on 2011-11-04
> **nec207 said:**
> I have but it does not explain in bold above what my router can do or cannot do.I'm reading that post above in bold and getting confused because I do not think my router does that.
 
That is why I will like some one here to look at it and read what is in bold above and explain what my router can do or cannot do in bold above. Do to I do not think my router does that what is bold above.


The truth here is quite simply this.

A router is a terrible security appliance. If you're relying on it for anything more than creating a WPA/2 protected wireless networking and masquerading you're fooling yourself.

It's centralized, it's over relied on and it's generally easy to bypass. I don't care if you have a linksys deskwarmer or a Cisco 3900 ISR. It's one appliance, it is not the end all be all, if you're relying on it for that. You're being silly.

Secure your system PROPERLY, secure your router to the best of your ability using the functionality at hand. Remember, functionality you don't have is functionality that can't be exploited.

And for goodness sake, please at least TRY to listen to advice when you ask for help. It really seems like you just want to argue most of the time.

---

### Post by nec207 on 2011-11-04
> **Dangertux said:**
> The truth here is quite simply this.
 
A router is a terrible security appliance. If you're relying on it for anything more than creating a WPA/2 protected wireless networking and masquerading you're fooling yourself.
 
It's centralized, it's over relied on and it's generally easy to bypass. I don't care if you have a linksys deskwarmer or a Cisco 3900 ISR. It's one appliance, it is not the end all be all, if you're relying on it for that. You're being silly.
 
Secure your system PROPERLY, secure your router to the best of your ability using the functionality at hand. Remember, functionality you don't have is functionality that can't be exploited.
 
And for goodness sake, please at least TRY to listen to advice when you ask for help. It really seems like you just want to argue most of the time.
 
 
I think what is confusing me is when people say get good router with a good firewall I keep thinking of what is in bold below.
 
And yes this is what I will like my router to do.
 
Because I do not know really how firewalls work or much about routers I'm getting confused what I think it should do and do not think it does that.When people say get good router with a good firewall I think of this in bold.
 
 
**good firewall is the router that will lock all traffic but the appropriate computers the admin sets up for the router only and no other computers can use that router and the use of logging .**
 
**Meaning if people are hacking my router ,unauthorized use of the router ( by not improved computer) or trying to log into the router by password guessing it will alert me.**
 
**My routers does not alert me or has that feature to alert me when there is unauthorized use of the router ( by not improved computer using the router ) or trying to log into the router settings by password guessing .**
 
**router that will lock all traffic but the appropriate computers the admin sets up for the router only and no other computers can use that router and the use of logging .**
 
I what a router that can do this

---

### Post by CharlesA on 2011-11-04
> **nec207 said:**
> 
I what a router that can do this

Look into spending a load of money on it then.

Or just secure it properly, keeping in mind what haqking and dangertux have said.

---

### Post by Dangertux on 2011-11-04
Well. You seem to know what you're looking for and you seem to know your router doesn't provide that functionality. So what is it you want from us? You have 6 pages full of good advice on securing the router you have. However it seems like you want a piece of equipment with more functionality, so why not just buy it?

Alternatively, build your own router using the linux distro of your choice and add whatever functionality you want, or create a smoothwall router.

---

### Post by lisati on 2011-11-04
> **nec207 said:**
> I have seen no link in this thread to the manual or anyone replying to my post saying what my router can do or cannot do .

Whoa there! Please take a deep breath, and read [post 22]("http://ubuntuforums.org/showpost.php?p=11422798&postcount=22") in this thread. It has the link to the manual for your router. We don't mind trying to help but I get the sense that people's patience is beginning to wear thin.

---

### Post by CharlesA on 2011-11-04
> **Dangertux said:**
> 
Alternatively, build your own router using the linux distro of your choice and add whatever functionality you want, or create a smoothwall router.

That's a very good idea, actually.

---

### Post by 1clue on 2011-11-04
> **lisati said:**
> Whoa there! Please take a deep breath, and read [post 22]("http://ubuntuforums.org/showpost.php?p=11422798&postcount=22") in this thread. It has the link to the manual for your router. We don't mind trying to help but I get the sense that people's patience is beginning to wear thin.

Mine sure is.

I've referenced the page in your user manual that tells you where the features are we're talking about.  You have not opened your manual to see it.  You have not clicked on the link to that manual to read it online.  I strongly suspect you have not clicked around in the admin screen of your router to see all the configuration pages.

Your router has all the features necessary to secure it as well as any average home user needs.  You have the security features to prevent some loser from hacking it from the next apartment over.  You have several pages of advice on exactly how to do that, and several links to your user manual and even page numbers in that manual to see EXACTLY how to do what we're talking about.

Your router's user manual has a section called "firewall."  Go read it, and then stop telling us you don't have one.

If you insist on having the features you're talking about, then prepare to pay more for a security device than the total value of all the electronic equipment in your house and of the house next door.  And then pay somebody $250 an hour with a 2-hour minimum to configure it, because if you can't figure out how to configure your home device from the admin screen, the user manual and the advice on this forum then there's no way you'll figure out how to configure the device you're describing.

Don't bother with dd-wrt.  If you can't find the features on your existing router's screen then you won't find the ones in dd-wrt either.

---

### Post by SparTacux on 2011-11-04
I know this is changing topic again...

On the subject of hacking routers - I spotted this link about attacking routers through browser exploits.

[http://hackademix.net/2010/07/28/abe-patrols-the-routes-to-your-routers/](http://hackademix.net/2010/07/28/abe-patrols-the-routes-to-your-routers/)

I suppose you could create a firewall rule to block access to the router gateway address on port 80 from the computer you use to browse the internet to nail this attack.  What do you guys think?

---

### Post by Dangertux on 2011-11-04
> **SparTacux said:**
> I know this is changing topic again...

On the subject of hacking routers - I spotted this link about attacking routers through browser exploits.

[http://hackademix.net/2010/07/28/abe-patrols-the-routes-to-your-routers/](http://hackademix.net/2010/07/28/abe-patrols-the-routes-to-your-routers/)

I suppose you could create a firewall rule to block access to the router gateway address on port 80 from the computer you use to browse the internet to nail this attack.  What do you guys think?


Samy Kamkar presented that idea 2 years ago at Black Hat. The presentation was titled "How I met your Girlfriend" 

In any case , it has been long since corrected in most routers. The flaw stems from this. The webserver in the router listening as such

```

0.0.0.0:80

```

this way if a malicious server rebinds its hostname to 192.168.0.1 it could forward a request to the router itself.

Fixing the binding on the service prohibits the SOP from being violated even in the event of XSS.

---

