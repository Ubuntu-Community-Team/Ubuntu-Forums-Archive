---
title: "Security"
date: 2012-07-31
forum: Security
---

### Post by gordie69 on 2012-07-31
Hey guys I got rid old Windows 7 tired of it and I'm setting up all my personal stuff last question do I need a firewall or is the kernel strong enough I was told that Linux is writin different like Windows I hope so I really like Ubuntu 12.04 getting use to the unity interface but sometimes you change is for the better.

Keep up the great work

---

### Post by Ms. Daisy on 2012-07-31
Yes, Ubuntu is different than Windows.  IMO you need a firewall.
 
You can see more recommendations for security in Ubuntu here:
[https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)

---

### Post by miegiel on 2012-07-31
I've run another linux than ubuntu (though ubuntu should be as safe) directly connected to the internet without a firewall without problems for about a year. Iptables still made my head spin back then, I had other stuff I wanted to do and love to taunt fate. :twisted: I've done the same with a fresh windows XP install and was hacked before I had the chance to install all the security updates. Within 30 to 60 minutes if memory serves me right.

Of course I'd never advice anyone to do that, but I didn't get hacked at all. At least not that I noticed. And I think I would have noticed, unless I was hacked really subtly. And my ISP is pretty alert on customers who are, unwittingly, acting as relays for spam and other mischief (they would have sent me a mail if my machine was misbehaving).

I did keep my machine updated all the time and didn't run any services (besides what is installed by default) that can be accessed from the internet other than skype and a bittorrent client.

One side note about firewalls: They are only as safe as their rules. If you don't configure them right they can give you a false sense of security. And you're always need to open your firewall enough to be able to access the internet and the openings you create can still be used by attackers.

---

### Post by gordie69 on 2012-08-02
What is the best firewall for Ubuntu the one that default and I remembered doing that and do you have too enable it everything you log in or not

---

### Post by Ms. Daisy on 2012-08-02
If I'm reading your run-on sentence the way you intended, then you want to set up a firewall in Ubuntu.

Here's a guide for using UFW, GUFW, or iptables.
[http://ubuntuforums.org/showthread.php?t=1876124](http://ubuntuforums.org/showthread.php?t=1876124)

---

### Post by Hungry Man on 2012-08-03
Not to blatantly disagree with Ms Daisy, who is awesome, but I think a Firewall is a bit of a waste of time.

Unless you take the time to set up separate UIDs for processes I can't see any benefit except to protect against automated malware, which doesn't even really exist for Linux home users. And even automated malware would probably take all of 10 extra lines of code to bypass an outbound firewall.

By default Ubuntu has no open ports except. A closed port is pretty secure regardless of a firewall. Actually there was an exploit for Windows that didn't attack the closed port, it attacked the firewall - the firewall had a counter and you could overflow it. More code = more attack surface = bad. So if that attack surface isn't really covering something critical it shouldn't be bothered with.

TL;DR - no, don't bother with one.

---

### Post by QIII on 2012-08-03
> **Hungry Man said:**
> Not to blatantly disagree with Ms Daisy, who is awesome, but I think a Firewall is a bit of a waste of time.

Unless you take the time to set up separate UIDs for processes I can't see any benefit except to protect against automated malware, which doesn't even really exist for Linux home users. And even automated malware would probably take all of 10 extra lines of code to bypass an outbound firewall.

By default Ubuntu has no open ports except. A closed port is pretty secure regardless of a firewall. Actually there was an exploit for Windows that didn't attack the closed port, it attacked the firewall - the firewall had a counter and you could overflow it. More code = more attack surface = bad. So if that attack surface isn't really covering something critical it shouldn't be bothered with.

TL;DR - no, don't bother with one.

Reading [this]("https://help.ubuntu.com/community/DoINeedAFirewall") might be enlightening.

Haqking may be along shortly.  Guy's a pro.  If he comes by, he'll get us up to snuff.

Additionally, if you are using the Oracle Java web browser plugin or the OpenJDK IcedTea plugin, you should make sure that you have updated to Version 7 Update 5.  A "fence-jumping" or "sandbox-jumping" or "escape" exploit has been discovered that will allow mailicious Java applets (and in some cases applications) to escape from the Java sandbox and execute in the user's context to deliver malicious payloads or cause other damage.  This was addressed by Update 5.  Previous versions are all vulnerable to this exploit -- on all platforms.  One specific example, that ***is **already ***in the wild, is even sophisticated enough to differentiate between OSes and deliver a tailored package specific to that OS.  Supposedly, it is a "drive by", which means the user need do nothing more than visit a website for the exploit to occur.

If you are running Java 6, you should get rid of it.  Java 6 has vulnerabilities to several known exploits and is due to reach EOL in November, 2012.

AppArmor profiles and proper attention to IP tables can go a long way towards mitigating a risk like this one.  But remember that there is ALWAYS risk from all angles.  This is just*** one ***example.

We've all known that javascript (which is not Java) has been dangerous for a long time.  There is another security risk.

Don't take security so lightly.  The myth of invulnerability is dangerous.  The myth that we are such a small segment that nobody is working to hack Linux is dangerous.  There is a significant motivation to seek vulnerabilities and exploit Linux servers.  Those exploits can be turned to your desktop.

I see people on the forum scoffing security by saying "I've been using Linux for years and have never had a problem."  They are missing one word at the end of that sentence:  "... yet."

---

### Post by ijumpship on 2012-08-03
I think we have to kinda tell him the heartache of using a firewall in linux.

I develop apps with firewalls you have to make sure the outbound rules match what you want.just an example if you want a streaming radio on a none standard port say (9175) you might not get it played with firewall

firewall in linux blocks both outgoing and incoming ports,you will have to set the rules when you use a firewall.the standard outgoing ports http(80),https(443) allows your traffic to browse the web. you want to do something else then a firewall may be necessary.

My recommendations to all newbie,test drive ubuntu,then soup it up the way you want like the rims etc.

---

### Post by Hungry Man on 2012-08-03
> Reading this might be enlightening.

Haqking may be along shortly. Guy's a pro. If he comes by, he'll get you up to snuff.
I've read this. Everything I've said still applies. 

Actually Dangertux, who contributed the majority of that wiki I believe, wrote a blogpost explaining the shortcomings and that this is purely for automated attacks.

Considering the trouble it can be to deal with an outbound Firewall I simply can't see it as being worth the trouble.

That said, if you take the time to split applications to a different User ID you can set up IPTables on a per UID basis, which is much more effective as it essentially acts as an application firewall.

edit:
[http://www.whenisfive.com/2011/10/03/a-firewall-is-not-a-catch-all/](http://www.whenisfive.com/2011/10/03/a-firewall-is-not-a-catch-all/)

His blogpost. P.S., if DangerTux sees this referrer he should PM me since he's awesome like Ms Daisy.

I think he gives more credit to the Firewall than I do. Much more.

Consider this situation. I have port X open outbound for Pidgin, port Y open outbound for xchat, port Z open outbound for DNS.

My DNS resolver is exploited. The attacker tries to open up port A. The attack fails.... until they try B, C, D, E, and finally get to X. Tada.

---

### Post by ijumpship on 2012-08-03
let me tell you my head curls when I think of all this hacking stuff.

All newbie do not put your life on your computer period.use it just to surf the internet period. you have a documents financials etc store them external with additional back up procedure.period

To all those fascinated by drop box and place your information in clouds.when these cloud burst it can only rain.

I buy the little flash media then the adapter as I notice the others  the electronics die and toast the usb drives.

for banking and other use secure browser and sites.
I still love paper and the post office and then I fret not much of the hackers as evil will always be there but it will never cripple me in fear

That's what the law is for find them and deal with them.

I think if you are skill to break a lock,help build  better locks not try destroy all locks.

---

### Post by QIII on 2012-08-03
A firewall is not a panacea.  I didn't say that, nor, do I think, did I imply it.  I mentioned apparmor.  I mentioned keeping Java up to date.

Each (and more) is one component of a constant process of security in depth.

I do not disagree at all with Dangertux.  A firewall is not a catch-all.

I am simply convinced that when it comes (and it will), the opening of the floodgates will be devastating because of (some of) our community's presently cavalier attitude about security.

---

### Post by Hungry Man on 2012-08-03
You added quite a bit to your original post.

Tangent - the Java exploit used the social engineering toolkit. OS detection also only takes like 15 lines or something like that and since Java is cross platform it's only a matter of getting users to open it in Java and the JVM handles the rest. I don't believe the one in the wild was a drive by, not that it couldn't easily become one.

Thankfully Apparmor completely prevents this as Java exploits will likely fail or become useless soon after exploitation.

A Firewall wouldn't really help. I spawn shell in Java, I find an open port, I win. Of course if Java already needs its own outbound port to work it's even easier.

It's more than not a panacea. ASLR isn't a panacea, Apparmor isn't a panacea, a Firewall... what does it do? It just prevents automated malware that stops executing when it can't get a connection to an outbound port - not a very likely behavior, it would probably just find another open port and keep looking until it does.

If the exploited program is running another UID you can restrict that UID to a port or remove its internet access entirely, which is much more helpful. Otherwise the shellcode can simply bruteforce its way to another open port.

The computer has internet access... we know it's probably using dhclient or some kind of DNS service... just check for those and you're basically guaranteed outbound access of some kind.

It's just not offering a hell of a lot and setting it up can be a real pain in the ***.

---

### Post by QIII on 2012-08-03
I added quite a bit because I was originally using thumbs on my cell and wasn't able to keep my thumbs up to speed.  Note that I also made a change in that I didn't mean to say anyone would get "you" in particular up to snuff.  A bit hard to write when there are several people in a thread to direct some things in one direction and others in another.

Wasn't trying to be argumentative, just trying to put brain to fingers in a hurry.

I guess we disagree... but for a reason we can probably agree on:  from either end we all see what "probably is" and what "probably isn't" (or something similar) as mirror images.

Tangent - the Java exploit with OS SomeSortOfCatFromApple in April (or was it May?) was apparently a drive-by.

---

### Post by gordie69 on 2012-08-03
Thanks guys so pretty much leave the firewalls out

---

### Post by samiux on 2012-08-03
Coin has two sides.

_Firewall is useless_ -

- Skilled hackers can bypass or evasion of firewalls and anti-virus.  Here is the [proof]("http://www.youtube.com/watch?v=GejYsldcIYk&feature=plcp"). 

- Malwares can also bypass or evasion of firewalls just depends on the skills of the developers.

- It is very difficult to configure and the outbound traffic seems cannot be blocked efficiently.

_Firewall is useful_ -

- It increases the difficulty of the attacks.

- It can block the not skilled hackers and script kiddies.

- It is not very hard to configure a firewall.  For Ubuntu, you can use ufw or gufw (if you are using desktop version).  It just need to enable the ufw or gufw, that's all.  All incoming traffic are blocked unless you allow a port.

I deployed [Unified Threat Management System]("http://en.wikipedia.org/wiki/Unified_threat_management") (UTM), such as [Untangle]("http://www.untangle.com/") which uses snort to filter the known attacks.  It includes anti-virus, firewall, intrusion prevention, spam filter, content filter and more.

There are many undiscovered or discovered but not yet announced vulnerabilities.  If any hacker take advantage of these, your boxes or networks will be very dangerous.

In conclusion, I suggest to implement firewall as well as UTM even you are using Linux.  However, these will not 100% protect your boxes and networks.  

System Administrators are therefore [required to know the skills of hacking in order to know your enemies]("http://www.youtube.com/watch?v=amY2GEKWlHU&feature=plcp").  In case your boxes or networks have been attacked, you can very easy to figure it out and prevent the future attacks efficiently and limited the loss.

Samiux

---

### Post by Ms. Daisy on 2012-08-04
> **Hungry Man said:**
> Unless you take the time to set up separate UIDs for processes I can't see any benefit except to protect against automated malware, which doesn't even really exist for Linux home users. And even automated malware would probably take all of 10 extra lines of code to bypass an outbound firewall.

IMO the typical desktop user is only ever going to encounter automated malware.  We love to talk about advanced attacks, but what's the likelihood that anyone in this thread will be targeted and attacked? (Well, except for Hungryman... ;) )  

A software firewall is simple and basic, but that doesn't make it useless.

---

### Post by Hungry Man on 2012-08-04
But even an automated attack could work around an outbound Firewall with very very little effort/ code involved. Instead of simply trying one port and then failing it would try one port and then the next and then the next etc until it finds an open one. 

You studied a bit of python =p you know how simple a loop/ if statement is. It's just running the same command they'd always run but you'd increment it.

As for automated malware, it's not like the web is swimming with Linux malware. Neither an automated attack nor a targeted attack are very likely haha.

---

### Post by samiux on 2012-08-04
> **Hungry Man said:**
> But even an automated attack could work around an outbound Firewall with very very little effort/ code involved. Instead of simply trying one port and then failing it would try one port and then the next and then the next etc until it finds an open one. 

You studied a bit of python =p you know how simple a loop/ if statement is. It's just running the same command they'd always run but you'd increment it.

As for automated malware, it's not like the web is swimming with Linux malware. Neither an automated attack nor a targeted attack are very likely haha.

If you know TCP/IP well, you may know that some ports are always opened.  The malware or torjan does not require to try and find the open port at your box.

However, firewall is required, in my opinion.

Samiux

---

### Post by Hungry Man on 2012-08-04
Some ports are always open such as for DNS or dhclient. But if they're in use the malware can't double up on it.

---

### Post by samiux on 2012-08-04
> **Hungry Man said:**
> Some ports are always open such as for DNS or dhclient. But if they're in use the malware can't double up on it.

Not exactly.  If the torjan or malware is at your box, it can very easy to connect to the attacker even the firewall is enabled.  There are some ports always opened but not only port 53.  Those opened ports have no service in use.

Samiux

---

### Post by Hungry Man on 2012-08-04
Right, so what's the point of a firewall?

---

### Post by samiux on 2012-08-04
> **Hungry Man said:**
> Right, so what's the point of a firewall?

As per I replied at #15 :

```
Coin has two sides.

_Firewall is useless_ -

- Skilled hackers can bypass or evasion of firewalls and anti-virus.  Here is the [proof]("http://www.youtube.com/watch?v=GejYsldcIYk&feature=plcp"). 

- Malwares can also bypass or evasion of firewalls just depends on the skills of the developers.

- It is very difficult to configure and the outbound traffic seems cannot be blocked efficiently.

_Firewall is useful_ -

- It increases the difficulty of the attacks.

- It can block the not skilled hackers and script kiddies.

- It is not very hard to configure a firewall.  For Ubuntu, you can use ufw or gufw (if you are using desktop version).  It just need to enable the ufw or gufw, that's all.  All incoming traffic are blocked unless you allow a port.

I deployed [Unified Threat Management System]("http://en.wikipedia.org/wiki/Unified_threat_management") (UTM), such as [Untangle]("http://www.untangle.com/") which uses snort to filter the known attacks.  It includes anti-virus, firewall, intrusion prevention, spam filter, content filter and more.

There are many undiscovered or discovered but not yet announced vulnerabilities.  If any hacker take advantage of these, your boxes or networks will be very dangerous.

In conclusion, I suggest to implement firewall as well as UTM even you are using Linux.  However, these will not 100% protect your boxes and networks.  

System Administrators are therefore [required to know the skills of hacking in order to know your enemies]("http://www.youtube.com/watch?v=amY2GEKWlHU&feature=plcp").  In case your boxes or networks have been attacked, you can very easy to figure it out and prevent the future attacks efficiently and limited the loss.

```

Firewall is working very well on layer 2 and 3 of OSI.  It can protect you from being attacked via layer 2 to 3 of OSI, such as ping to death.  

Meanwhile, firewall can increase the difficulty of the attack.  If a hacker is not very skilled, he may be in trouble when the box is firewalled.  For script kiddies, firewall is very powerful, in my own opinion.

You can sheath some of the ports of services when they are not required for remote access, such as port 3306 (MySQL) when the MySQL server does not serve remotely.

Not only firewall, you are also required to implement the Unified Threat Management System (UTM).  If it is impossible, you may required to implement Snort.  Since UTM and Snort can protect you from being attacked by known vulnerabilities or attacks.  

However, when your box or network is firewalled and UTMed, you are not 100% safe from attack.  You also need to keep an eye on your systems.

Once upon a time, when I was started to use Linux, every one told me that Linux is very secure and even firewall is not required.  However, I tell you that it is totally FALSE.  

Compares with Windows system, Linux is also very easy to compromise.  It is because attacker does not require to overcome the problem of anti-virus.  The attack vectors of Linux and Windows systems are same.

Please do NOT think that Linux is a bullet proof system.

Samiux

---

### Post by Ms. Daisy on 2012-08-04
> **Hungry Man said:**
> Right, so what's the point of a firewall?Asked and answered rather well by Dangertux IMO.
[http://ubuntuforums.org/showthread.php?t=1871177](http://ubuntuforums.org/showthread.php?t=1871177)

> The misconception in how a firewall can help you begins here. Some users  assume that since you are running no services, a connection can not be  made. So you do not need a firewall. If these were the only things you  needed to think about, this would be perfectly acceptable. However, this  is only part of the picture.  
 
 There are two additional factors that come into play there. One, if you  do not utilize a firewall on the basis that you have no open ports, you  are crippling your own security because if an application that you do  have is exploited and code execution occurs a new socket can be created  and bound to an arbitrary port. The other important factor here is that  if you are not utilizing a firewall you also have no outbound traffic  control whatsoever. In the wake of an exploited application, instead of a  new socket being created and a port being bound, another alternative an  attacker can utilize is to create a reverse connection back to a  malicious machine. Without any firewall rules in place this connection  will go through unhindered.

---

### Post by Hungry Man on 2012-08-04
>  One, if you do not utilize a firewall on the basis that you have no open ports, you are crippling your own security because if an application that you do have is exploited and code execution occurs a new socket can be created and bound to an arbitrary port.
This is somewhat viable. But that's for an inbound Firewall, not outbound.

And I don't see why an attacker can't just bind an already open inbound port.

But, yes, an inbound Firewall may be worth setting up for that reason.

> The other important factor here is that if you are not utilizing a firewall you also have no outbound traffic control whatsoever. In the wake of an exploited application, instead of a new socket being created and a port being bound, another alternative an attacker can utilize is to create a reverse connection back to a malicious machine. Without any firewall rules in place this connection will go through unhindered.
Dangertux's own blog shows how easily bypassable an outbound Firewall is on Linux. I linked to it earlier.

---

### Post by samiux on 2012-08-04
> **Ms. Daisy said:**
> In the wake of an exploited application, instead of a new socket being created and a port being bound, another alternative an attacker can utilize is to create a reverse connection back to a malicious machine. Without any firewall rules in place this connection will go through unhindered. 

Not exactly.  Even the box is firewalled (inbound and outbound), the reverse connection can be established to the attacker without any problem.

Samiux

---

### Post by samiux on 2012-08-04
> **Hungry Man said:**
> And I don't see why an attacker can't just bind an already open inbound port.

If the port is opened by a running service and the service has vulnerability, the port can be easily bind by attacker.

If the attacker opened a port at the victim box, the port can be bind by attacker.

If the port is opened with no running service in use, attacker can use this port to bind a shell after creating a listener at that port.

May be it is too difficult for you to understand.  However, I won't explain these in deep as it is my secret.  :)

Samiux

---

### Post by miegiel on 2012-08-05
> **Hungry Man said:**
> Right, so what's the point of a firewall?

Like a car is made to drive on land and not to drive on water, a firewall is made to allow and disallow IP packets by a set of rules and not to allow or disallow programs to communicate with each other.

Using a firewall to block malware, skype, bittorrent or whatever program to connect to other programs over a network is as stupid as driving your car on water. It's a thing IT professionals do (aka professional idiots).

To use skype as an examlpe. Skype uses ports 80, 433 and another random port to listen to other skype clients on the network (sometimes it even uses 8080 through a proxy). Of course you can block incoming connections on 80, 433 and go look for the random port and blok it too. But that won't block the skype client to connect to the p2p skype network unless you block every outward port including 80 and 433. In which case you might as well pull the plug on you network. You won't be able to browse the internet, you won't be able to resolve dns names, you won't even be able to get an IP address via DHCP.

If you don't want skype, bittorrent, malware, or whatever program to be used you don't install it (or allow people to install it on the network you administer).

One more thing :D Just like there are countries that call themselves a democracy, but are not a democracy. There is software that calls itself a firewall, but is not a firewall. It's just marketing, aka propaganda. Like that windows thing that calls itself a firewall in that youtube vid posted earlier. The only thing that vid proves is that windows has more holes than a swiss cheese, which is a well known fact. Exploiting a virtual windows with a virtual backtrack5 and thinking you proved firewalls don't protect against exploits, hilarious! That dude only proved he's an idiot. I'm looking forward to his next vid where he drives his car into a lake to prove you driving in the rain is dangerous.

However this doesn't mean firewalls can't be put to good use. They can! Just don't expect them to do stuff they're not made for.

---

### Post by samiux on 2012-08-05
> **miegiel said:**
> Like a car is made to drive on land and not to drive on water, a firewall is made to allow and disallow IP packets by a set of rules and not to allow or disallow programs to communicate with each other.

Using a firewall to block malware, skype, bittorrent or whatever program to connect to other programs over a network is as stupid as driving your car on water. It's a thing IT professionals do (aka professional idiots).

To use skype as an examlpe. Skype uses ports 80, 433 and another random port to listen to other skype clients on the network (sometimes it even uses 8080 through a proxy). Of course you can block incoming connections on 80, 433 and go look for the random port and blok it too. But that won't block the skype client to connect to the p2p skype network unless you block every outward port including 80 and 433. In which case you might as well pull the plug on you network. You won't be able to browse the internet, you won't be able to resolve dns names, you won't even be able to get an IP address via DHCP.

If you don't want skype, bittorrent, malware, or whatever program to be used you don't install it (or allow people to install it on the network you administer).

One more thing :D Just like there are countries that call themselves a democracy, but are not a democracy. There is software that calls itself a firewall, but is not a firewall. It's just marketing, aka propaganda. Like that windows thing that calls itself a firewall in that youtube vid posted earlier. The only thing that vid proves is that windows has more holes than a swiss cheese, which is a well known fact. Exploiting a virtual windows with a virtual backtrack5 and thinking you proved firewalls don't protect against exploits, hilarious! That dude only proved he's an idiot. I'm looking forward to his next vid where he drives his car into a lake to prove you driving in the rain is dangerous.

However this doesn't mean firewalls can't be put to good use. They can! Just don't expect them to do stuff they're not made for.

Interesting post but you are telling us you are an idiot in the field of penetration testing indeed.  :)

Samiux

---

### Post by miegiel on 2012-08-05
> **samiux said:**
> Interesting post but you are telling us you are an idiot in the field of penetration testing indeed.  :)

Samiux

Yes, in the sense that I've never pentested anything in my life. No, in the sense that I get poked by numbnuts almost every hour of every day in the year. Though, regrettably, it's getting less and less. How am I supposed to beef up my firewall if the numbnuts give up? I hope I don't have to become a pentest expert. There's so much more other fun stuff to do.

---

### Post by GreatDanton on 2012-08-05
> **miegiel said:**
>  I hope I don't have to become a pentest expert. There's so much more other fun stuff to do.

True, but pentesting is also fun thing to do. Once you start you can't stop ;)

---

