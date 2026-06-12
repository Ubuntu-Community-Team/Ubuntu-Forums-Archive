---
title: "Is there any way to stop this guy from doing a port scan attack on me?"
date: 2008-03-14
forum: Security Discussions
---

### Post by FreewareFan on 2008-03-14
This jerk has been at if for well over 12 hours now, and I can't seem to find a way to block his port scans.  I've gone so far as to call my ISP (comcast--two thumbs down), and they tell me they can't do a thing about it.  Right.....  Last time I heard, port scanning was illegal. 

Anyway, is there a way from within Gutsy to get this guy to stop??  Is there anything I can send his way to make him stop?  Dirty tricks are accepted, at this point....

Thanks!

FwF

---

### Post by firestormx37 on 2008-03-14
Could you provide some more information about how you are set up.  Are you directly connected to the internet or are you behind a router?  How do you know that he is port scanning you?  Any other information would be helpful.

---

### Post by FreewareFan on 2008-03-14
I connect to the net via a cable modem.  I know he's port scanning me because Firestarter keeps alerting me of it.  He scans a port every second or two....   At this rate, to scan all 65 thousand plus ports, it will be days before he is done. 

I've already released my IP, and gotten a new one, but the scans continue.  He is probably scanning a large block of ip addresses, would be my guess....

FwF

---

### Post by joshrobinson on 2008-03-14
are you sure your being attacked, and this isnt a normal internet communication? does firestarter hae an option to block the ip address its coming from?

comcast wont let you release your ip, at least not for me, i always have to just wait till they change it

---

### Post by Sef on 2008-03-15
[Webopedia]("http://www.webopedia.com/TERM/p/port_scanning.htm") says:

> Port scanning in and of itself is not a crime. There is no way to stop someone from port scanning your computer while you are on the Internet because accessing an Internet server opens a port, which opens a door to your computer. There are, however, software products that can stop a port scanner from doing any damage to your system.

---

### Post by FreewareFan on 2008-03-15
> **joshrobinson said:**
> are you sure your being attacked, and this isnt a normal internet communication? does firestarter hae an option to block the ip address its coming from?

comcast wont let you release your ip, at least not for me, i always have to just wait till they change it

For well over 12 hours this person has been going from one port, to the next port, to the next port, trying to find an open port.  So, to answer your question, NO, I do not believe this to be a normal internet communication....  

And firestarter will not let me block his ip address.  It's already blocked, by default, all incoming ports are blocked by default...  But, the whole process still ties up some of my cpu cycles, and I'm just tired of firestarter telling me I'm getting scanned....

For me, comcast will certainly let me release and renew to a new IP.  I have to boot back into WinXP and use the cli, but it's certainly doable.  I've done it twice now, but like I said, it does not stop the scan attack...  He must be scanning a large block of comcast ip addresses...

---

### Post by FreewareFan on 2008-03-15
> **Sef said:**
> [Webopedia]("http://www.webopedia.com/TERM/p/port_scanning.htm") says:

Hummm...  Well, I certainly thought it was against the law in the USA.  Live and learn, I suppose......

So, I have no option but to just ride it out for the next couple of days until he scans and probes all 65,535 ports, huh?

OK, thanks.

---

### Post by iansane on 2008-03-15
port scanning is not illegal but the more intrusiv scanning may be,  where certain techniques like fragmenting packets actually try to get past your router or fiewall.  Wireshark could give you the source IP address. I'd be tempted to ping him relentesley but that's probably not a good idea. The source IP from wireshark is probably not his anyway. I have a router set to not respond to pings and whenever I switch from it to my dsl modem I start getting hit constantly. So the router seems to stop it.

---

### Post by Brebs on 2008-03-15
Turn the firestarter warnings off - they are useless. People all over the world are continually trying to hack into Internet-connected PCs.

It's only a problem if your PC has a security vulnerability.

---

### Post by FreewareFan on 2008-03-15
OH, I have his ip address.   67.228.205.235 is where he is coming from.   I don't think he's using a proxy, although it's a possibility I guess....

I sure would like to throw something back at him to make him quit!!

---

### Post by dcstar on 2008-03-15
> **iansane said:**
> port scanning is not illegal but the more intrusiv scanning may be,  where certain techniques like fragmenting packets actually try to get past your router or fiewall.  Wireshark could give you the source IP address. I'd be tempted to ping him relentesley but that's probably not a good idea. The source IP from wireshark is probably not his anyway. I have a router set to not respond to pings and whenever I switch from it to my dsl modem I start getting hit constantly. So the router seems to stop it.

Port probes must have a vaild IP address for the replies otherwise there is no point whatsoever probing ports if you are never going to be notified of an responding one - unless it is a DOS attack, then moving up a port of a time is also pointless.

Most people block them at the router/modem interface and not at the OS level, there are usually "blacklist" features to automatically block any IP address that is detected attacking you.

Most of these attacks could well be coming from "Zombie" systems infected with scumware (spell W-i-n-d-o-w-s for me someone.....), so directly attacking that source will do little to inconvenience the real originator of the problem.

---

### Post by iansane on 2008-03-15
don't know for sure what you could throw back at him but did you do a who is look up on that IP address? Looks like it belongs to a company maybe. It could be some company computer that got attacked and is being used to do dirty work. That's why it's hard to track people down.

try whois look up at  whois.domaintools.com

says Softlayer Technologies inc. out of Dallas Texas.

It be cool if everyone on the forum would ping them all at once. :lolflag:

---

### Post by FreewareFan on 2008-03-15
OK, well, I'll see if I can find the docs to my cable modem, and see if I can get into it to blacklist his ip address.

Thanks.

---

### Post by FreewareFan on 2008-03-15
Hey, I'd like to thank all of you for you ideas and input on this issue!

I think for now, I'm just going to shut off the box, and call it a night.  We'll see in the morning if he's still at it.....  

Thanks again, everyone!

FwF

---

### Post by handydan918 on 2008-03-15
Starting Nmap 4.11 ( [http://www.insecure.org/nmap/](http://www.insecure.org/nmap/) ) at 2008-03-14 22:00 PDT
Interesting ports on one-mark1.net (67.228.205.235):
Not shown: 1671 filtered ports
PORT     STATE  SERVICE
20/tcp   closed ftp-data
21/tcp   closed ftp
25/tcp   closed smtp
53/tcp   closed domain
80/tcp   closed http
113/tcp  closed auth
143/tcp  closed imap
443/tcp  closed https
3389/tcp open   ms-term-serv

Yup. It's a Windows box....but I'm not sure I think it's a bot. Note the absence of ports 135-139, 445 etc...

---

### Post by iansane on 2008-03-15
LOL can anyone say brute force attack? I just used the ubuntu terminal server client and tried to log on as administrator and after several random pw's it didn't lock me out. That service should not be running and open port like that. Oh well, if I had guessed it and gained access, That would be illegal but just seeing that it is there is not. I don't know about trying pw's for fun. Hope the FEDs don't wake me up tonight.:lolflag:

---

### Post by FreewareFan on 2008-03-15
Dood, I don't know what you did, but he cut off his attack just under two hours ago, right about the time you were messing with him....

I don't know if you had anything to do with it or not, but if you did, THANK YOU!!

---

### Post by bollix47 on 2008-03-15
```
OrgName:    SoftLayer Technologies Inc. 
OrgID:      SOFTL
Address:    1950 N Stemmons Freeway
City:       Dallas
StateProv:  TX
PostalCode: 75207
Country:    US

ReferralServer: rwhois://rwhois.softlayer.com:4321

NetRange:   67.228.0.0 - 67.228.255.255 
CIDR:       67.228.0.0/16 
OriginAS:   AS36351
NetName:    SOFTLAYER-4-5
NetHandle:  NET-67-228-0-0-1
Parent:     NET-67-0-0-0-0
NetType:    Direct Allocation
NameServer: NS1.SOFTLAYER.COM
NameServer: NS2.SOFTLAYER.COM
Comment:    abuse@softlayer.com
RegDate:    2007-11-07
Updated:    2008-01-25

RAbuseHandle: ABUSE1025-ARIN
RAbuseName:   Abuse 
RAbusePhone:  +1-214-442-0605
RAbuseEmail:  abuse@softlayer.com 
```

You could try sending an e-mail to [email]abuse@softlayer.com[/email] including the IP address and the times that you are being pinged.

Might not help but worth a try.

Good Luck!

---

### Post by beyboo on 2008-03-15
I think there is a lot of over reaction here. Proabably some bored guy in some damn corporate network using some no brainer port scanning tool like angry ip scanner to while away time. Atleast on a nix box you get to know it, w'doze users are blissfully ignorant :)

[http://ipscan.sourceforge.net/w/Home](http://ipscan.sourceforge.net/w/Home)

---

### Post by Mustard on 2008-03-15
A workaround would be to just turn off the firstarter gui interface.  Firestarter will still be running in tthe background doing it thing.  The number of 'cycles' being stolen would be reduced.

```
sudo /etc/init.d/firestarter status

#this command will confirm from console that firestarter is running

```

You wont have to watch the icon turning red with scary lightning bolts then, as it will all happen silently in the background. :)

---

### Post by JonnyV on 2008-03-15
Who ever it is, is running a very in-depth scan. They have been scanning the ports for my IP overnight and still going according to my soho firewall logs.

---

### Post by EdThaSlayer on 2008-03-15
Why don't you try disconnecting your router or turning it off for lets say tonight. Then reconnect it in the morning.

---

### Post by FreewareFan on 2008-03-15
Yep, he's back at it again...  He's now on port 18532  and still going strong...  Durn, I thought he had given up, but what happened is that he only stopped for like an hour, then started in again, right at the port he left off at.  

At this rate, it's going to take him another two days to get through all 65535 ports.

Oh well, as many of you have said in this thread, not much I can do about it, but either turn off firestarter so I don't know he's scanning, or just ignore him...  For some perverted reason, I just cannot bring myself to turn off firestarter...  I guess if he really manages to break into this box, I wanna know..

Thanks again, everyone, for all your input on this!

FwF

---

### Post by FreewareFan on 2008-03-15
> **EdThaSlayer said:**
> Why don't you try disconnecting your router or turning it off for lets say tonight. Then reconnect it in the morning.

Wouldn't do a thing.  He's scanning a large block of comcast IPs, so the scan would still continue.  He has not singled me out as an individual, I just happen to be within the block he's scanning.....

---

### Post by FreewareFan on 2008-03-15
> **JonnyV said:**
> Who ever it is, is running a very in-depth scan. They have been scanning the ports for my IP overnight and still going according to my soho firewall logs.

You too, eh?  You must live close by where I am, in central Illinois, yes?  Maybe if enough of us comcast customers call in to complain, maybe then they will take some action??

---

### Post by Spoken on 2008-03-15
open up google and search "ip address tracker" and copy and paste his ip into the bar, it will show you on a map where he located lol...funn...

---

### Post by PapaNerd on 2008-03-15
Just to set the record straight:
Any ISP has the capability in their router(s) to block a single IP address.  All they have to do is add a "deny" policy.  They also have the capability of contacting the registered owner of the offending IP and letting them know about the problem (which is frequently a hacked Windoze machine).

Of course, your ISP has to first want to help you, and that is not always the case.  However, most do want to clean up the problems on their own networks.

---

### Post by dcstar on 2008-03-16
> **bollix47 said:**
> 
..........
You could try sending an e-mail to [email]abuse@softlayer.com[/email] including the IP address and the times that you are being pinged.

Might not help but worth a try.

Good Luck!

Or see if they have a web site, and then find a contact and let them know what is happening - chances are the management will want it stopped ASAP even if some tech-head ignores the "abuse" e-mails.

---

### Post by zxscooby on 2008-03-16
[http://www.terminally-incoherent.com/blog/wp-content/uploads/2007/12/hackers.png](http://www.terminally-incoherent.com/blog/wp-content/uploads/2007/12/hackers.png)

---

### Post by zxscooby on 2008-03-16
oops link broken

---

### Post by djamu on 2008-03-16
I use the** fail2ban** package to automatically block persistent login attempts ( script kiddies trying to login with a blank "administrator" account :lolflag: ,guess what they are using...
you can change the amount of valid login attempts + how long that is banned on a / port base 
( in other words someone trying to login on your ssh will be blocked but will still be able to see your webpages... )

in any case **fail2ban** manipulates your iptables, so effectively packets from a certain ip get dropped....
works brilliant..but it doesn't prohibits one from scanning your ports 

to block the scanning itself > disable the ICMP protocol, this will block any ping / most  nmap 
...


:guitar:

---

### Post by iansane on 2008-03-16
> **beyboo said:**
> I think there is a lot of over reaction here. Proabably some bored guy in some damn corporate network using some no brainer port scanning tool like angry ip scanner to while away time. Atleast on a nix box you get to know it, w'doze users are blissfully ignorant :)

[http://ipscan.sourceforge.net/w/Home](http://ipscan.sourceforge.net/w/Home)

Yeah your probably right. I'm in a beginning security class where no one tells us how to do anything and just gives us a bunch of scanning tools and lets us go. No telling how many people we have bothered because of not understanding what we are doing. Just randomly doing all different kinds of scans on random IP ranges. I know it's messed up but that's how they teach the class here in hickville.

---

### Post by iansane on 2008-03-16
> **djamu said:**
> I use the** fail2ban** package to automatically block persistent login attempts ( script kiddies trying to login with a blank "administrator" account :lolflag: ,guess what they are using...
you can change the amount of valid login attempts + how long that is banned on a / port base 
( in other words someone trying to login on your ssh will be blocked but will still be able to see your webpages... )

in any case **fail2ban** manipulates your iptables, so effectively packets from a certain ip get dropped....
works brilliant..but it doesn't prohibits one from scanning your ports 

to block the scanning itself > disable the ICMP protocol, this will block any ping / most  nmap 
...


:guitar:

I think when I check the box that says "Don't respond to ping" in my router that is the same as disabling ICMP at the router, but how can you disable it on the machine itself in the case that you don't use a router and your ISP won't allow access to the DSL/Cable modem?

---

### Post by ibanez on 2008-03-16
A Reactive firewall would be better than Firestarter..
If your Ok with installing and configuring stuff  then give this a try .. 
It will block on any intrusion attempt and can be configured to report the intruder automatically .


1..  IDS ....   [http://snort.org/](http://snort.org/)
 2.. IPS ....   [http://www.chaotic.org/guardian/](http://www.chaotic.org/guardian/)

These two in conjunction with each other make an excellent reactive firewall, I wouldn't be without mine, I run them on my firewall box. If you want better security than Ubuntu alone offers consider using an old spare machine ( Virtually anything will do) & Install Smoothwall on it. then you have the luxury of having both Snort & Guardian installed during the setup of Smoothy. 
I've been running a smoothwall box a couple of years now and wouldn't even consider running without it .. (some of the features adware blocker , Blackhole DNS, IPS, really though ,Smoothwall is as simple or as complex as you want to make it. )

[http://www.smoothwall.org/](http://www.smoothwall.org/).

---

### Post by Patrick-Ruff on 2008-03-16
interesting tools here.  OP: is he still at it?  maybe you should port scan him back! :)

---

### Post by djamu on 2008-03-16
For some of the seasoned sysadmins following is going to be boring (?)

There's a lot of misconception on the true usage of firewalls
Firewalls are not the main defense ( you might disagree after reading the complete post )
Just wonder what it's supposed function is ... > to allow exceptions transfering your network
In other words about the last step in securing your network...
Security should be built up from the socket level to the protocol level.

Lots of people don't realize the power of using the netmask  as a filter or the absense of a gateway definition.

I'll explain > far the easiest to protect your internal server ( only if it under no circumstances it is allowed to talk to the outside  ) is to remove the gateway definition > this prohibits any packet to go outside of your subnet ( defined by the netmask > the internet ), packages still might reach the server but no one will know because no ACK or whatsoever confirmation will travel outside of your subnet ... ( in other words do not ever use netmask 0.0.0.0 )

Then comes netmask 

Then comes disabling services, locking up ports,  ip tables 

& last of all comes a firewall to filter out the exceptions.....

Whether firewall is on a different machine or running inside a virtual machine doesn't really matter, what does matter is that it ( I'm talking very secure environments ) should run another OS so any discovered weakness won't be exposed  on both the firewall & the server... 

In other words if the server runs linux > firewall should be BSD ... my favorites are [Monowall]("http://m0n0.ch/wall/") ( for embedded, dedicated use ) or [Pfsense]("http://www.pfsense.com/") ( which is a Monowall fork with added functionality )


My 5 cents...

---

### Post by Arkaniad on 2008-03-16
Lol, hes in Dallas...... if hes still scanning anyway. check it out---
[http://www.ip-adress.com/ipaddresstolocation/](http://www.ip-adress.com/ipaddresstolocation/)

remember his IP-
67.228.205.235
Have fun.....

---

### Post by Arkaniad on 2008-03-16
Lol- Scan report looks like its an ISP worker
IP address [?]:  	 67.228.205.235  Copy  [Whois]
IP address country: 	ip address flag United States
IP address state: 	Texas
IP address city: 	Dallas
IP postcode: 	75207
IP address latitude: 	32.782501
IP address longitude: 	-96.820702
ISP of this IP [?]: 	SoftLayer Technologies
Organization: 	SoftLayer Technologies
Host of this IP: [?]: 	one-mark1.net [Whois]
Local Time of this IP country: 	2008-03-16 11:46
Probably a little late, but....

---

### Post by djamu on 2008-03-16
for you guys info

that target address ( 67.228.205.235 ) is running Windows 2003 R2 enterprise edition .... so it's likely a business.  ( can't imagine a home user buying such an expensive license )....
so be careful not to do something illegal just because you have that IP , I was able to get to the login screen... not feeling like I should even try something....

Since this turns out to be a security  probing thread ... I wouldn't mind if someone checked out my server... just in case I overlooked something...
I got smtp / ftp / ssh / http / https & whatnot....


:)

---

### Post by twisted_steel on 2008-03-16
It looks like the company is a datacenter with hosting services.  It could just be one of their customers that is doing this.  I'd contact their abuse department if you think it is a problem.

[http://www.softlayer.com/legal.html](http://www.softlayer.com/legal.html)

---

### Post by Patrick-Ruff on 2008-03-16
bah, yeah it seems I learned a lot more about security just by this thread :D

---

### Post by FreewareFan on 2008-03-16
UPDATE:   Yep, he's still at it..  I finally just filtered him out with firestarter, so I don't even get the alerts anymore...  

He's bound to give up sooner or later..

---

### Post by scorp123 on 2008-03-16
> **FreewareFan said:**
>  This jerk has been at if for well over 12 hours now Probably some virus or worm doing this automatically, searching for more Windoze victims, and so on.

> **FreewareFan said:**
>  and I can't seem to find a way to block his port scans.   
 You have a hardware firewall/router?

> **FreewareFan said:**
>  Last time I heard, port scanning was illegal.  I know for a fact that it is *not* illegal in Switzerland and probably in most other European countries. Port scanning is like knocking on a door: You check if anyone would answer. But you don't step in and don't break in ... those latter things would  clearly qualify as "unauthorized intrusion" and thus be illegal. But port scanning alone ... As I said, it's like someone knocking on your doors and asking "anyone at home?".

> **FreewareFan said:**
>  Anyway, is there a way from within Gutsy to get this guy to stop??   How do you know he's port-scanning you? Do you have any logs or something? Can you post that here?

---

### Post by dsluga on 2008-03-17
Amazing. I found this thread through Google when searching for information on the same IP address. 

That same IP address (67.228.205.235) has been port scanning my home machine also. It started last Friday, then the guy took the weekend off, and right at 7:59 CST this morning it started up again. He is in the late 46,000s now. Perhaps he'll just scan up to the max port (65,000 or so) and stop? 

I have emailed [email]abuse@softlayer.com[/email] (retrieved from the WhoIs Information) twice now. Once with a link to this forum. Something weird is going on down there. 

Did he rescan you after finishing ? 

-Dan

---

### Post by penguinpi.com on 2008-03-17
shorewall should be able the block pings and port scans. apt-get shorewall and checkout shorewall.net for a tutorial on how to set it up. you can also blacklist IP addresses in the blacklist file.

---

### Post by dsluga on 2008-03-17
BTW. I am in central Illinois as well and on Comcast.  I just re-read the forum.  

Perhaps this has something to do with the recent Insight to Comcast conversion? Perhaps Comcast initiated it to see what they have? 

For now I am just seriously hardening that machine, enabling stealth mode, and completely blocking all responses to that IP address using IPFW ("sudo ipfw add deny all from 67.228.205.0/24 to me"). I blocked the entire subnet for good measure.  

Chances are it is just Comcast eyeballing the new guys.

---

### Post by DrMega on 2008-03-17
> **FreewareFan said:**
> UPDATE:   Yep, he's still at it..  I finally just filtered him out with firestarter, so I don't even get the alerts anymore...  

He's bound to give up sooner or later..

You'll probably find that "he" is just a dodgy program (a virus perhaps) sitting on somebody's Windows PC.

Unfortunately it is a common prelude to a hijack attempt. What generally happens is someone write a program to do something like this:

1. Start generating IP addresses in sequence: I.e. from 01.01.01.01 to 255.255.255.255.
2. For each address generated, send a ping request.
3. If there is a reply to the ping request, then run a full port scan on that address.
4. When an open port is found, log that IP address and port, and attempt to upload the the malware to the target machine (which then sets about doing the same thing).

The thing is, as long as your machine is well secured, you'll be OK (I believe Ubuntu's default setup is quite solid).

I keep my network hidden behind a hardware router/firewall (only a few quid to buy) so I just leave it to the router/firewall to deal with this kind of thing.

---

### Post by beyboo on 2008-03-17
> **Patrick-Ruff said:**
> interesting tools here.  OP: is he still at it?  maybe you should port scan him back! :)

I like your style :lolflag:

---

### Post by djamu on 2008-03-17
That computer is harmless just ignore it... only the fact that it takes hours for him to scan a port range means he's using some kiddies scan tool, me scanning ( scanning is not illegal ) his entire port range takes about 30 sec & I know exactly what he's running ( Windows 2003 R2 Enterprise )....

Knowing a lot of people come from the windoz platform, you can just leave that habit of thinking you need a firewall.... you don't,  linux is not windows, linux has already a firewall built in ( iptables ) & all ports are closed ( except the occasional ipp printer port )....

and if you really think this is weird, well guess what I got hundreds of those kids / day probing my servers knowing none of them will get in ....


Most people are behind NAT routers which in itself are already really powerfull firewalls, if you're not just buy one ( any ) mind also the differnce between a router a bridge & a switch . These 3 might apparently do the same but their operation is completely different...   


:lolflag:

---

### Post by NightwishFan on 2008-03-17
If someone knocks on your door long enough is that not harassment? I would definitely harass back by then. :)

I will help in anyway you guys would need this kind of probing is annoying.

---

### Post by DrMega on 2008-03-17
> **NightwishFan said:**
> If someone knocks on your door long enough is that not harassment? I would definitely harass back by then. :)

I will help in anyway you guys would need this kind of probing is annoying.

You could always send about a 1MB packet by ping and have it repeat continuously. That would slow down his connection (unless he has set up so that his machine doesn't reply to ping requests). Eventually he might get the message and run a virus scan, whereupon he will no doubt find that his machine is infected with whatever virus it is that keeps port scanning you.

---

### Post by Junglizer on 2008-03-17
Unfortunately all of this scanning is nothing new, however what I would recommend, if you have specific ports open at all, namely 22 for ssh, is to block all non-(your country here) IP blocks for access, do not allow root login and if you can, add your specific IP's that you'll be logging in from anyways. That being said, you don't really have anything to worry about as long as you know that it is going on (it always will) and that you keep in mind to check on it whenever you update or change your system. 

Also in regards to scanning. Scanning is not specifically illegal, however, it is what it "stands for" if you will. In short, why would you need to full port-scan someone other then to try to access their system? So it is perceived that you will be up to no good if you are scanning someone. So keep in mind that certain realms (gov't/large corps) will consider even simple scanning an intrusion attempt.

---

### Post by Junglizer on 2008-03-17
> **DrMega said:**
> You could always send about a 1MB packet by ping and have it repeat continuously. That would slow down his connection (unless he has set up so that his machine doesn't reply to ping requests). Eventually he might get the message and run a virus scan, whereupon he will no doubt find that his machine is infected with whatever virus it is that keeps port scanning you.

This is actually rather less then effective, unless you spoof your own IP to prevent receiving the ICMP response, otherwise you'll end up slowing down your own connection more than anything else as ping waits for a response from the targeted system.

---

### Post by NightwishFan on 2008-03-17
Just remember I am here if you need to make use of me.

---

### Post by Junglizer on 2008-03-17
> **NightwishFan said:**
> Just remember I am here if you need to make use of me.

LOL.

---

### Post by NightwishFan on 2008-03-17
I am kidding............ I hope he stops though.

---

### Post by Junglizer on 2008-03-17
> **NightwishFan said:**
> I am kidding............ I hope he stops though.

Just making sure we're on the same page. Its just bots though, zombied boxes.

---

### Post by FreewareFan on 2008-03-17
Well, for the time being, the scanning has stopped...  I'm not sure if it's because someone finally showed up for work, and found something amiss with their computer, or if it's because the person/bot just finished with whatever they were trying.  

However, in the meantime, due to all the GREAT information in this thread, I've locked down this box as tight as possible.  I don't even respond to ICMP echo requests anymore.  Totally and completely 'Stealth' according to Shields Up.

So, all in all, it has been an adventure in education and awareness on my part.  Once again, I'd like to thank each of you for your information, suggestions, and offers of help.  It's a great community we have here!!!

FwF

---

### Post by FreewareFan on 2008-03-17
> **dsluga said:**
> BTW. I am in central Illinois as well and on Comcast.  I just re-read the forum.  

Perhaps this has something to do with the recent Insight to Comcast conversion? Perhaps Comcast initiated it to see what they have? 

For now I am just seriously hardening that machine, enabling stealth mode, and completely blocking all responses to that IP address using IPFW ("sudo ipfw add deny all from 67.228.205.0/24 to me"). I blocked the entire subnet for good measure.  

Chances are it is just Comcast eyeballing the new guys.

I sort of doubt it's Comcast, as I called them right from the first, after being scanned for 12 hours or so.  They spent some time on the phone with me, trying to do several things, and then finally told me my best bet was to call the FCC. Can you believe that?  Anyways, I don't think it's them, too over the top, even for Comcast.  And if I had any choice but to continue with them, I would take it, but here where I'm at, they are now the only choice, as far as cable goes.  It's not the service that I don't like, it's the company.

But anyways.....  Say, what's this ipfw you are talking about?  I don't seem to find much information within Synaptic about it.  Is this another frontend for the built-in firewall in Ubuntu?

---

### Post by djamu on 2008-03-17
> **FreewareFan said:**
> Well, for the time being, the scanning has stopped...  I'm not sure if it's because someone finally showed up for work, and found something amiss with their computer, or if it's because the person/bot just finished with whatever they were trying.  

However, in the meantime, due to all the GREAT information in this thread, I've locked down this box as tight as possible.  I don't even respond to ICMP echo requests anymore.  Totally and completely 'Stealth' according to Shields Up.


LOL of course it stopped > as soon as you turn of ICMP your nic stops replying to ping & most other scan tools, but that doesn't even mean packages don't reach you anymore ....

:tongue:

---

### Post by scorp123 on 2008-03-17
> **FreewareFan said:**
>  I don't even respond to ICMP echo requests anymore. That's the first thing to do. You should not even have responded to ICMP packets in the first place ;)

---

### Post by Tomatz on 2008-03-17
Bit of info on the above ip address:

IP address [?]:  	        67.228.205.235  Copy  [Whois]
IP address country: 	ip address flag United States
IP address state: 	Texas
IP address city: 	        Dallas
IP postcode: 	        75207
IP address latitude: 	32.782501
IP address longitude: 	-96.820702
ISP of this IP [?]: 	SoftLayer Technologies
Organization: 	        SoftLayer Technologies
Host of this IP: [?]: 	one-mark1.net [Whois]
Local Time:        	2008-03-17 11:29
 

Maby get onto his isp they might have a "word" with him. Unless its some zombie windows box :)

---

### Post by Junglizer on 2008-03-17
> **Tomatz said:**
> Bit of info on the above ip address:

IP address [?]:  	        67.228.205.235  Copy  [Whois]
IP address country: 	ip address flag United States
IP address state: 	Texas
IP address city: 	        Dallas
IP postcode: 	        75207
IP address latitude: 	32.782501
IP address longitude: 	-96.820702
ISP of this IP [?]: 	SoftLayer Technologies
Organization: 	        SoftLayer Technologies
Host of this IP: [?]: 	one-mark1.net [Whois]
Local Time:        	2008-03-17 11:29
 

Maby get onto his isp they might have a "word" with him. Unless its some zombie windows box :)

Usually you can send an email detailing the problem to the default "abuse@<isp>.com/net" and and they'll usually look into blocking some of it or at least look into it a bit more. It's always a better bet to go to where its coming from rather then your provider.

---

### Post by FreewareFan on 2008-03-17
> **scorp123 said:**
> That's the first thing to do. You should not even have responded to ICMP packets in the first place ;)

Hey, that is the default setting for Ubuntu, it's not my doing..  With as secure as Ubuntu sets things up right out of the box, you would think they would take care of this issue also, right?

---

### Post by Tomatz on 2008-03-17
Have emailed his ip to bluetack internet security (with this thread) hopefully they'll put him on a blocklist. Not that it will help you lol :(

---

### Post by djamu on 2008-03-17
> **FreewareFan said:**
> Hey, that is the default setting for Ubuntu, it's not my doing..  With as secure as Ubuntu sets things up right out of the box, you would think they would take care of this issue also, right?

I wonder If you're aware of the difference between protocols... having ICMP enabled is NOT a security thread.. it's a feature to locate nic's ( computers ) on a network. Don't want to be rude but as far as I understand  there's hasn't been an hacking attempt ( Hacking a computer using ICMP alone is impossible ). In other words as long as that scan isn't accompanied by a brute-forece/dictionary UDP/TCP attack nothing is wrong. And for your edification lots of ISP use ICMP to to probe your connection / leases whatever...  

I know it's exiting to think you're getting hacked, but rest assured it's far from that... dealing with  DDOS for example is of an entire different magnitude...

> **Junglizer said:**
>   Usually you can send an email detailing the problem to the default "abuse@<isp>.com/net" and and they'll usually look into blocking some of it or at least look into it a bit more. It's always a better bet to go to where its coming from rather then your provider.

> **Tomatz said:**
> Have emailed his ip to bluetack internet security (with this thread) hopefully they'll put him on a blocklist. Not that it will help you lol :(


same here no hacking attempt is done, so don't expect any reaction, at least you should give them prove of the attempt ( captured packets ) or otherwise anyone should be able to block anyone.
Just imagine me claiming everyone on this site with their IP's tried to hack me. tssstsss that's not going to happen ever....



o_O

---

### Post by Tomatz on 2008-03-17
Yeah i agree but you dont have to be Einstein to work out that if someone is scanning a computer constantly for open ports it is probably due to malicious reasons.  Yeah it in its self is no way a hacking attempt but it could quite possibly be the first step.

---

### Post by Tomatz on 2008-03-17
Most probably he will realize that you have a secure system and firewall soon and buzz off.

---

### Post by djamu on 2008-03-17
> **Tomatz said:**
> Most probably he will realize that you have a secure system and firewall soon and buzz off.

He won't realize anything.. it's an application as it's scanning a whole group of IP's, the only thing that happens is that this particular IP seems to be down ( because the host doesn't get any replies )... now if he was scanning the other protocols, the application would know you turned off ICMP... which is just another proof of how clumsy this attempt is.... and surely is no proof whatsoever you have a safe system.... I talked about some very basic steps to take prior using a protocol filter ( a firewall ) ... disabling stuff at the socket level is always better then filtering...


:wink:

---

### Post by Tomatz on 2008-03-17
> **djamu said:**
> He won't realize anything.. it's an application as it's scanning a whole group of IP's, the only thing that happens is that this particular IP seems to be down ( because the host doesn't get any replies )... now if he was scanning the other protocols, the application would know you turned off ICMP... which is just another proof of how clumsy this attempt is.... and surely is no proof whatsoever you have a safe system.... I talked about some very basic steps to take prior using a protocol filter ( a firewall ) ... disabling stuff at the socket level is always better then filtering...


:wink:
I agree :) Thought you were saying (earlier) that it wasn't a (partial) hack attempt. Sorry for jumping the gun there.  

The guy probably doesn't even know what os he is spending all this time scanning lol.

:)

---

### Post by ice60 on 2008-03-17
i normally find port scans come from someone from the same ISP as me, and they're generally hacked computers with bots or a worm. if you keep being scanned after changing your IP address then it's probably scanning blocks of addresses on the same subnet. what else could it be?

> **scorp123 said:**
> That's the first thing to do. You should not even have responded to ICMP packets in the first place ;)maybe someone will know, but i think one of the icmp RFC's says icmp 0 and 8 should be enabled.

---

### Post by scorp123 on 2008-03-18
> **ice60 said:**
>  maybe someone will know, but i think one of the icmp RFC's says icmp 0 and 8 should be enabled. Not necessarily on a firewall. And I assumed that OP has a hardware router+firewall ... Netgear something, Linksys, whatever. First thing I do on those devices is to make sure that anything ICMP is off. A firewall has no business responding to ICMP probes.

But it seems OP is using their Ubuntu system directly as firewall or is connected directly via a modem? OK that would be a different situation then in regards to my comment above.

---

### Post by FreewareFan on 2008-03-18
> **scorp123 said:**
> 
But it seems OP is using their Ubuntu system directly as firewall or is connected directly via a modem? OK that would be a different situation then in regards to my comment above.

Correct.  I am connected directly via a cable modem.

---

### Post by 3rdalbum on 2008-03-18
Freenode (the IRC server) does port scans while you are connected. They show up in my router's security logs, and they are also mentioned in the Freenode FAQ.

If I get port scanned by anyone other than Freenode, I tend to reply with:

```
sudo ping -f -i 0.1 -l 15 -W 1 <ip-address>
```

Quite illegal, kinda pointless, and it makes my internet connection go slow... but if everyone did it after getting port scanned or an attempted DoS, the attackers would get quite inconvenienced (or the innocent owner of the zombie computer would realise that something was up).

---

### Post by FreewareFan on 2008-03-18
What, exactly, does that command do?

---

### Post by tact on 2008-03-18
> **FreewareFan said:**
> What, exactly, does that command do?

Its initiates a "flood" of pings.   A ping flood.   Depending on your perspective it may give you some kind of joy.  Tho it comes at a cost (eats your bandwidth and maybe some CPU cycles).   :)

---

### Post by FreewareFan on 2008-03-18
Thanks for the info!

I'll keep it for any future use I might have....  You never know.

FwF

---

### Post by Junglizer on 2008-03-18
> **3rdalbum said:**
> Quite illegal, kinda pointless, and it makes my internet connection go slow... but if everyone did it after getting port scanned or an attempted DoS, the attackers would get quite inconvenienced (or the innocent owner of the zombie computer would realize that something was up).

**Warning**
The following is a theoretical explanation of Denial of Service based attacks and is not a tutorial. Attempting these processes is deemed illegal in most countries and I will not be held responsible in anyway. 
**End**

This just comes back to what I mentioned prior. Pinging someone relentlessly with data is worthless as an attack unless you spoof your own IP address, otherwise, given how ping works, you will be flooded with just as much data as them when it acknowledges that their system is up and valid. And in regards to Denial of Service, all that is really effective is DDoS, or distributed denial of service, where in turn you would have said zombied/rooted boxes do the majority of the "heavy-lifting" per say in the attack. You would usually want send fragmented packets as well as spoofing the IP of the host system as to fully flood the target. That being said it usually takes A LOT of traffic to bring something down, especially if it is a server of some sort. You would probably want boxes on multiple net-blocks as to not arouse too much suspicion from one ISP that the zombies are on.

---

### Post by piousp on 2008-03-18
You know, this thread is really educational :popcorn:

---

### Post by mjwhitfield on 2008-03-18
No doubt security is an interesting subject.

---

### Post by myddewji13 on 2008-03-18
> **3rdalbum said:**
> Freenode (the IRC server) does port scans while you are connected. They show up in my router's security logs, and they are also mentioned in the Freenode FAQ.

If I get port scanned by anyone other than Freenode, I tend to reply with:

```
sudo ping -f -i 0.1 -l 15 -W 1 <ip-address>
```

Quite illegal, kinda pointless, and it makes my internet connection go slow... but if everyone did it after getting port scanned or an attempted DoS, the attackers would get quite inconvenienced (or the innocent owner of the zombie computer would realise that something was up).

does this command keep going on forever...or does it eventually stop...or do i have to manually stop it?... (not gonna try it...just curious..lol)

---

### Post by Junglizer on 2008-03-18
Yes it will keep going on forever untill you do ^C to kill it. All pings keep going in Linux, unless otherwise flagged. Windows on the other hand, stops at 3 by default.

---

### Post by myddewji13 on 2008-03-18
^c  = ?

---

### Post by FreewareFan on 2008-03-18
Ctrl + C       It's a terminal interupt.

---

### Post by handydan918 on 2008-03-18
ctrl+c

---

### Post by 3rdalbum on 2008-03-20
> **Junglizer said:**
> 
This just comes back to what I mentioned prior. Pinging someone relentlessly with data is worthless as an attack unless you spoof your own IP address, otherwise, given how ping works, you will be flooded with just as much data as them when it acknowledges that their system is up and valid.

And in regards to Denial of Service, all that is really effective is DDoS, or distributed denial of service, where in turn you would have said zombied/rooted boxes do the majority of the "heavy-lifting" per say in the attack.

Yeah, I realised that what I was doing was kinda pointless. I did notice though that the pings were coming back to me much less often than they were going out, though that's probably just because of unreliable Internet protocols.

In my case, I didn't mind slowing down my own idle internet connection for a while, if it slows down the attacker's.

And finally, my apologies - I should have explained what the command did. For those of you who are wondering, look up "pingflood" on Wikipedia.

---

### Post by Tomatz on 2008-03-21
Has it stopped yet?

---

### Post by FreewareFan on 2008-03-21
Yes.  Stopped about three days ago, not to be heard from since.

---

### Post by Kevbert on 2008-03-21
Have you tried running ShieldsUP!   It works in Ubuntu and can be found here:[http://www.grc.com/default.htm]("http://www.grc.com/default.htm")
If you scroll down the page and click on the ShieldsUP! link.  This will scan all your ports and give you an idea whether there are any open ones.  Sorry to hear you're still having problems with this moron.

---

### Post by FreewareFan on 2008-03-21
I believe you've misundestood..  I said it stopped three days ago, and he's not been heard from since...

And thanks for the link, however, I ran that test when the scanning first started..  I was good, except for answering Icmp pings..  But when I turned that off, I became completely stealth!

FwF

---

### Post by NightwishFan on 2008-03-21
Yeah. With pings off they aren't even sure they are knocking at the right house. :)

---

### Post by Nocturne5577 on 2008-03-21
I had that once and I entered his IP in iptables and preffered action drop, never seen him since..

---

### Post by bhavi on 2008-03-22
> **FreewareFan said:**
> This jerk has been at if for well over 12 hours now, and I can't seem to find a way to block his port scans.  I've gone so far as to call my ISP (comcast--two thumbs down), and they tell me they can't do a thing about it.  Right.....  Last time I heard, port scanning was illegal. 

Anyway, is there a way from within Gutsy to get this guy to stop??  Is there anything I can send his way to make him stop?  Dirty tricks are accepted, at this point....

Thanks!

FwF

Port scanning only provides trivial Info about the the other system but nmap can reveal the network distance and open ports and services on a system and network complexity by no of HOPS... And nessus DoS vulnerability scan is dangerous if a system under scan is vulnerable to DoS.. Only thing is to use Iptables and sheildsup! or Firestarter... I think....

---

