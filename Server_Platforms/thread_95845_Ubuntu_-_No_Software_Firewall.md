---
title: "Ubuntu - No Software Firewall?"
date: 2005-11-27
forum: Server Platforms
---

### Post by Ted_Smith on 2005-11-27
Hi

Sorry - new to Ubuntu from Windows...

I note that Ubuntu doesn't ship with a Firewall. I read [this]("http://www.ubuntulinux.org/support/documentation/faq/firewall") which informed me no firewall is present, followed by a few users concerns.

I use Ubuntu at home for 'home based' stuff. I also do webamstering from home, but my sites aren't hosted on my PC, although the files are kept on it and uploaded via FTP to my commercial host. I have a LinkSys Router that connects me to the net and it has a Firewall of it's own, and my Linux PC just connects to the net via it.

On my Windows SO I have ZoneAlarm as well, just in case.  

Do I need to worry about finding, downloading and installing a software Firewall on my Ubuntu Linux PC?

Thanks

Ted

---

### Post by Leif on 2005-11-27
firestarter is available in the repos. there are how-to's in the forums about it.

---

### Post by abandoned_hussam on 2005-11-27
Actually ubuntu uses iptables which does the job if I'm not mistaken. But if you need a firewall configuration tool, you can always use firestarter which is a config tool for iptables.

---

### Post by LordHunter317 on 2005-11-27
Ubuntu in a default doesn't need a firewall running, so it enables no iptables rules.

Iptables is installed, setup whatever rules you wish.

---

### Post by Biased turkey on 2005-11-27
[QUOTE=Ted_Smith]Hi

Sorry - new to Ubuntu from Windows...

I note that Ubuntu doesn't ship with a Firewall. I read [this]("http://www.ubuntulinux.org/support/documentation/faq/firewall") which informed me no firewall is present, followed by a few users concerns.

I use Ubuntu at home for 'home based' stuff. I also do webamstering from home, but my sites aren't hosted on my PC, although the files are kept on it and uploaded via FTP to my commercial host. I have a LinkSys Router that connects me to the net and it has a Firewall of it's own, and my Linux PC just connects to the net via it.

On my Windows SO I have ZoneAlarm as well, just in case.  

Do I need to worry about finding, downloading and installing a software Firewall on my Ubuntu Linux PC?

Thanks

Ted[/QUOTE]

Here we go again  :)  lol
from the Ubuntu wiki:
[http://www.ubuntulinux.org/support/documentation/faq/firewall]("http://www.ubuntulinux.org/support/documentation/faq/firewall")

Since Ubuntu doesn't run any daemons that listen to the outside world by default (the postfix install only listens on localhost) there's no need for a default firewall.

The rationale is that if a user's got a need for installing a world-facing daemon, they'll be aware that they should configure a firewall/ACL for it too.

If you don't have a local network ( LAN ) don't bother to install any firewall.
If you are paranoiac, I would suggest to install "firestarter"

---

### Post by towsonu2003 on 2005-11-28
[QUOTE=Biased turkey]
If you don't have a local network ( LAN ) don't bother to install any firewall.
[/QUOTE]

needed to correct this, but may prove to be controversial... but... I would say:
if you don't have any outside-world connection (dialup, wireless, ethernet, broadband, any network) you won't need firewall :)

*ducks*

---

### Post by Ted_Smith on 2005-11-28
Thanks guys - I did read the FAQ you refer to as per my original post

In my case, it's simply a case that I have a router with a firewall in it and my Linux PC is connected to it in the same as as My Windows OS. The router is connected to the Internet. In the near future I intend to add at least another 3 machines to this router so I will have a LAN effectively. It could be argued that in the technical sense I have a LAN running now, but with only one PC on it. 

> if you don't have any outside-world connection (dialup, wireless, ethernet, broadband, any network) you won't need firewall 

As i said in first post, I do have etethernet and broadband etc. 

I'm only paranoid in the sense that I like to do banking etc online. I realise I have my router firewall but on my Windows OS I have ZoneAlarm as a precaution. I so used to Windows secuirty issues that I'm worried about my new Linux setup. 

I will try out FireStarter but I just wanted to understand why it was claimed it wasn't necessary - I got rather confused by the FAQ.

---

### Post by Danielle on 2005-11-28
hi, can you tell me what the default setup is for iptables? if your address was scanned would you be visible? what would happen if you were pinged? would you respond with icmp 8? thanks

---

### Post by Delkster on 2005-11-28
[QUOTE=Danielle]hi, can you tell me what the default setup is for iptables?[/quote]
All connections accepted.

> if your address was scanned would you be visible?
Yes. Since there are no services/daemons listening to tcp or udp ports visible from outside, all ports are closed, but as far as I understand, by default Linux responds to such a connection with the appropriate 'connection rejected' message. (I can't check right now, though, as I'm behind a hardware firewall that hides the ports.)

> what would happen if you were pinged?
AFAIK it would be responded.

---

### Post by Danielle on 2005-11-28
[quote=Delkster]I can't check right now, though, as I'm behind a hardware firewall that hides the ports.[/quote]
thanks, Delkster :) i think that was where i was getting confused - most people who say they don't need an iptables frontend probably have a router.

---

### Post by Danielle on 2005-11-28
hi, Ted Smith. you would only need a software FW if you wanted to guard against outward bound connections. your router will protect you from threats coming from the internet. so really you'd need a software FW only if you think you might have malware already installed on you computer which would then try to "call home" or if you think there's a chance of malware being installed in the future. HTHs :)

---

### Post by matthew on 2005-11-28
[quote=Danielle]hi, can you tell me what the default setup is for iptables? if your address was scanned would you be visible? what would happen if you were pinged? would you respond with icmp 8? thanks[/quote]Point your browser here and you can run some vulnerability tests and see for yourself what may/may not be at risk. [https://www.grc.com/x/ne.dll?bh0bkyd2]("https://www.grc.com/x/ne.dll?bh0bkyd2")

---

### Post by Danielle on 2005-11-28
[QUOTE=matthew]Point your browser here and you can run some vulnerability tests and see for yourself what may/may not be at risk. [https://www.grc.com/x/ne.dll?bh0bkyd2]("https://www.grc.com/x/ne.dll?bh0bkyd2")[/QUOTE]
hi, i'm using a frontend, but before i configured it i did a port scan and i could see all the ports but two. ssl which was being used and another, i forget. that is more vulnerable then dropping packets.

---

### Post by matthew on 2005-11-28
[quote=Danielle]hi, i'm using a frontend, but before i configured it i did a port scan and i could see all the ports but two. ssl which was being used and another, i forget. that is more vulnerable then dropping packets.[/quote]Wow! I run it and everything says "stealth"--not one port shows up.

---

### Post by Danielle on 2005-11-29
[QUOTE=matthew]Wow! I run it and everything says "stealth"--not one port shows up.[/QUOTE]
yeah but do you have a router? i don't have one that's why i said i was getting confused with everyone saying they don't need it. most people here probably have a NAT router with 2+ computers. i am on a standalone and no router. you probably scanned your router.

---

### Post by Danielle on 2005-11-29
[QUOTE=matthew]Wow! I run it and everything says "stealth"--not one port shows up.[/QUOTE]
yeah but do you have a router? i don't have one that's why i said i was getting confused with everyone saying they don't need a software FW. most people here probably have a NAT router with 2+ computers. i am on a standalone and no router. you probably scanned your router.

---

### Post by matthew on 2005-11-29
[quote=Danielle]yeah but do you have a router? i don't have one that's why i said i was getting confused with everyone saying they don't need it. most people here probably have a NAT router with 2+ computers. i am on a standalone and no router. you probably scanned your router.[/quote]Yeah, I do have a router. You are probably right. It's been a long time since I plugged straight in to the net...I may try it soon (time-pending) and see what I discover. If I get the chance to run some tests I'll post the results.

---

### Post by Danielle on 2005-11-29
[QUOTE=matthew]Yeah, I do have a router. You are probably right. It's been a long time since I plugged straight in to the net...I may try it soon (time-pending) and see what I discover. If I get the chance to run some tests I'll post the results.[/QUOTE]
if i had a router i'd make the same mistake all the time. it's easy to think - the page says it's scanning my FW so it must be. but, i'm sure it probably says something about routers somewhere on the page.

---

### Post by Ted_Smith on 2005-11-29
> hi, Ted Smith. you would only need a software FW if you wanted to guard against outward bound connections. your router will protect you from threats coming from the internet. so really you'd need a software FW only if you think you might have malware already installed on you computer which would then try to "call home" or if you think there's a chance of malware being installed in the future. HTHs 

Thanks Dan - this is why I have ZA on my Windows PC. I hear that Linux is not prone to Malware so I guess I need not worry, but I also suppose it's only a matter of time until it perhaps is (seeing as Linux is getting more popular for domestic use).

At the GRC website I almost get 100% stealth (I do on 'common ports') but I get a few replying as 'closed' on the 'Test All Ports' test. This iafter I configured my Router to send requests to certain IP ranges to IP's that don't exist in my range. Need I worry about these few ports replying as 'closed'? I realise it makes me visible on the net, but surely if they're closed they're closed - no need to worry? 

Thanks

Ted

---

### Post by Danielle on 2005-11-29
hi Ted. i just tried to post and i wasn't logged in so i hope i don't double post. 

i think closed ports are fine. there are some scans which search for closed ports using FIN and NULL packets. closed ports will reply while open ports will not. but the purpose of the scan is to exploit open ports.

you can use some IDS software like snort, i haven't used it so i can't say much about it.

lastly, if i where you i'd go to a security forum and see what they say there, i can only talk for me but they'd know far far more then me.

---

### Post by ajgreeny on 2005-11-30
Hi Folks

Just seen this thread and took the online scan suggested by mathew at
[https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)
This shows I have ports 21(ftp) and 23(telnet) open.  All others are either closed or reported as in stealth mode.
Should I have any worries about the two open ports and if so should I manually close them?  If the answer to this question is "yes" can you tell me how I do so please.

I think this is a great forum which has got me out of a few holes in the past, and no doubt will in future, knowing my inclination to fiddle with things.  What a good way to learn about Linux, though.
Many thanks

---

### Post by Danielle on 2005-11-30
hi, ajgreeny :) were you using telnet or downloading at the time of the scan? if you weren't then the ports should not have been open and it could be a problem. i don't know very much about Ubuntu so i can't help you close the ports, disabling telnet and ftp will be a great help until you either close the ports or find out what's going on.

i would disconnect from the internet and do some scans using f-prot, Bitdefender, rkhunter and chkroot. that's me though :-) it might be better if you can ask someone who knows Ubuntu if there might be a reason for the ports to be open.

another thing i'd do is do a search for any suspicious looking log files - very large, or in an odd place.

try and get some help from an Ubuntu expert asap just so you know not to worry. HTHs

---

### Post by prizrak on 2005-12-12
I'll try explaining a little simpler than the FAQ maybe it'll be easier to understand. You generally connect to network services (file sharing, FTP, websites, etc...) through virtual ports. Everytime you use any of those services you initiate a connection on a certain port to a system that "listens" to those connections. Meaning that if anyone initiates the connection to the specified port, the listening computer will allow the requesting computer access to the said port. The security repercussion (sp?) of this is that anyone connecting on the said port can use it to get into the system (not necesserily on ANY of them but some). The default Ubuntu install will not listen to anything on the network which means that all your ports are closed until you do something to open it (i.e. go to the web, dl something over BT, telnet, etc...) which means that anyone trying to request the connection will get a refusal to connect effectively learning that the port is closed. What a firewall does is stealth your ports. What that does is it makes anyone who tries to get into your computer think that the computer doesn't exist on the network, basically it will look your machine is down. It makes you safer because then the possible attacker will not try to do something to get into the machine since it  "doesn't exist" however generally speaking it makes little difference since getting into a system with closed ports isn't trivial and only someone determined would try to and someone determined will get around the firewall anyway. Another thing to keep in mind is that routers tend to have a rudimentary firewall in place that will stealth the ports no matter what OS you are using behind it. That said if you are on wireless I would suggest installing firestarter starting the firewall. Reason being, it is easy to connect to the wireless network directly bypassing the internet and w/e security features your router has, making your system more vulnerable.

---

### Post by M3ta7h3ad on 2005-12-12
[QUOTE=Ted_Smith]Thanks guys - I did read the FAQ you refer to as per my original post

In my case, it's simply a case that I have a router with a firewall in it and my Linux PC is connected to it in the same as as My Windows OS. The router is connected to the Internet. In the near future I intend to add at least another 3 machines to this router so I will have a LAN effectively. It could be argued that in the technical sense I have a LAN running now, but with only one PC on it. 



As i said in first post, I do have etethernet and broadband etc. 

I'm only paranoid in the sense that I like to do banking etc online. I realise I have my router firewall but on my Windows OS I have ZoneAlarm as a precaution. I so used to Windows secuirty issues that I'm worried about my new Linux setup. 

I will try out FireStarter but I just wanted to understand why it was claimed it wasn't necessary - I got rather confused by the FAQ.[/QUOTE]
I dont believe IPTables blocks programs from phoning home which I believe is the only possible threat you would be under unless you declare certain ports open on your ubuntu machine, in your router (most commonly called "virtual servers" or "port forwarding/mapping").

Even on windows (which isnt that insecure, its mostly just propaganda speak), you will experience next to no threat from the outside world being behind a NAT router (which is what I presume your setup as), mainly due to the fact that your internal machines cannot be contacted by the outside world as only your router can be seen.

in short.. until they include a firewall that prevents trojans and other evil nasties from creating outbound connections (dont believe iptables does this), there is no point in installing or configuring iptables if your behind a NAT router.

---

### Post by prizrak on 2005-12-14
[QUOTE=M3ta7h3ad]I dont believe IPTables blocks programs from phoning home which I believe is the only possible threat you would be under unless you declare certain ports open on your ubuntu machine, in your router (most commonly called "virtual servers" or "port forwarding/mapping").

Even on windows (which isnt that insecure, its mostly just propaganda speak), you will experience next to no threat from the outside world being behind a NAT router (which is what I presume your setup as), mainly due to the fact that your internal machines cannot be contacted by the outside world as only your router can be seen.

in short.. until they include a firewall that prevents trojans and other evil nasties from creating outbound connections (dont believe iptables does this), there is no point in installing or configuring iptables if your behind a NAT router.[/QUOTE]
Iptables is set by default to blacklist the outgoing traffic, however it can be configured to whitelist it. If you wanna be hardcore it can be done in CLI if you don't you can use firestarter to do so.

---

### Post by JBBxWolf on 2005-12-15
[QUOTE=Ted_Smith]Thanks guys - I did read the FAQ you refer to as per my original post

I'm only paranoid in the sense that I like to do banking etc online. I realise I have my router firewall but on my Windows OS I have ZoneAlarm as a precaution. I so used to Windows secuirty issues that I'm worried about my new Linux setup. 

I will try out FireStarter but I just wanted to understand why it was claimed it wasn't necessary - I got rather confused by the FAQ.[/QUOTE]

Remember this tho..  A firewall only protects you from intruders coming to your machine. It does not stop snooping on your network for logins/passwords.     

I think you are looking more for anti-phishing and junk like that.    

A firewall will not make your Online Banking any safer other then keeping your machine safe from intrusions. 

You can look into wallets and other software which will help secure your local accounts and passwords in the event your machine is compromised.

---

### Post by tonderai on 2005-12-21
I ran the test at grc.com because we got the message from gnome saying "a malicious user may be eavesdropping on your session". It gave the following:

> GRC Port Authority Report created on UTC: 2005-12-21 at 16:32:50

Results from scan of ports: 0-1055

    0 Ports Open
 1054 Ports Closed
    2 Ports Stealth
---------------------
 1056 Ports Tested

NO PORTS were found to be OPEN.

Ports found to be STEALTH were: 520, 666

Other than what is listed above, all ports are CLOSED.

TruStealth: FAILED - NOT all tested ports were STEALTH,
                   - NO unsolicited packets were received,
                   - A PING REPLY (ICMP Echo) WAS RECEIVED. 

We are behind a NAT router, so I presume that this represents a scan of that - rather than the individual systems: the scan comes up the same on different systems on the lan and different from internal LAN port scans. 

I was pretty surprised to see 666 and 520 stealthed (I have no idea what the router would use these for). 666 is a port used by the game Doom, and is apparently used by many trojans. 520 is usually used by 'efs'.

Is this a concern? Should I / Can I close these ports?

---

### Post by LordHunter317 on 2005-12-21
[QUOTE=prizrak] The security repercussion (sp?) of this is that anyone connecting on the said port can use it to get into the system (not necesserily on ANY of them but some).[/quote]You can only get in pass the service listening on that port if you've found an exploit.

> (i.e. go to the web, dl something over BT, telnet, etc...) which means that anyone trying to request the connection will get a refusal to connect effectively learning that the port is closed.Of the things you mention, only one would opening a listening port (unless you mean telnet server, which no one should run).

> What a firewall does is stealth your ports. What that does is it makes anyone who tries to get into your computer think that the computer doesn't exist on the network, basically it will look your machine is down.Any attacker worth his salt can tell a "stealthed" machine is actually alive, especially if it runs any services.  

> It makes you safer because then the possible attacker will not try to do something to get into the machine since it  "doesn't exist"But it does, and it's trival to verify.  The stealth properties of firewalls are generally overstated and not worth talking about.  They have a few useful features, but not really relevant to system penetration.

> Iptables is set by default to blacklist the outgoing traffic, however it can be configured to whitelist it. No, by default it does no filtering on any traffic.  It accepts everything in every direction.

[quote=M3ta7h3ad]In short.. until they include a firewall that prevents trojans and other evil nasties from creating outbound connections (dont believe iptables does this),[/quote]It can do it, it's just more trouble than it's worth, as I said.

---

### Post by towsonu2003 on 2005-12-21
[QUOTE=LordHunter317]"In short.. until they include a firewall that prevents trojans and other evil nasties from creating outbound connections (dont believe iptables does this)" --> 
It can do it, it's just more trouble than it's worth, as I said.[/QUOTE]
Here is a link on that [http://ubuntuforums.org/showthread.php?t=99332](http://ubuntuforums.org/showthread.php?t=99332)

---

### Post by davebradford on 2005-12-22
[www.iptablesrocks.org](www.iptablesrocks.org)

---

### Post by perspectoff on 2007-08-09
I agree with most of the posts.

However, many people are installing LAMP servers and web servers with their initial installation.

This requires a good knowledge of port forwarding and port access rules, and using iptables (with or without the Firestarter frontend, which I think is great) is pretty useful for this.

Also, BitTorrent, Miro (Democracy) TV, chat programs (Pidgin), rsync daemon, and a multitude or programs now communicate freely. But I don't always want them to communicate so freely. For example, while I'm learning BitTorrent, I don't want everyone and their brother able to access my files. (I know that doesn't happen by default, but as a newbie I didn't know that).  

That's when closing down some ports that a daemon is listening to (and which I, as a newbie might not know is listening) is worthwhile.

As another example, i may want to restrict the ports for rsync (the remote folder synchronization program) to just within my network. I really need iptables (+/- Firestarter) then.

The down side is that if you enable iptables (which is installed by default) with Firestarter or manually, you must always be aware of your ports. Otherwise, you may forget to open ports and will be scratching your head why a program doesn't work like it should (Samba, Bittorrent, Miro TV, and on and on.)

---

