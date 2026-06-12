---
title: "[SOLVED] Firewall adjustments?"
date: 2008-08-27
forum: Security
---

### Post by Camilia on 2008-08-27
Hi
I am new to unbuntu and still trying to understand it. I have tried applying  the info at ubuntu.com but never ever able to apply it. Hope this is the right place for this problem.

Just recently reinstalled ubuntu to format dual bootup. Then ad this forum found command to enabled firewall of ubuntu. Can't remember the command. Tried to save pictures from [http://art.cafepress.com/comics_funny_unique?page=3&topic=4419](http://art.cafepress.com/comics_funny_unique?page=3&topic=4419) Before lasted reinstallation of ubuntu I was able to save images from this link. Thus I am thinking it may be blocked.

How do I adjust the firewall of ubuntu to allow it?

---

### Post by cdenley on 2008-08-27
That depends on what iptables frontend you used to configure it. Assuming you used UFW
```

sudo ufw disable

```

Now what were you trying to accomplish with the firewall in the first place?

---

### Post by rogeriopvl on 2008-08-27
[gufw.tuxfamily.org]("http://gufw.tuxfamily.org")

take a look at this firewall front-end. It let's you configure the firewall in a more friendly and graphic way.

---

### Post by Camilia on 2008-08-27
I set up the firewall for advised to do so at ubuntu.com.  Was trying to copy pictures for avatar. 

This is what I have. What do I do with it?
Commands:
  enable			Enables the firewall
  disable			Disables the firewall
  default ARG			set default policy to ALLOW or DENY
  logging ARG			set logging to ON or OFF
  allow|deny RULE		allow or deny RULE
  delete allow|deny RULE	delete the allow/deny RULE
  status			show firewall status
  version			display version information

Tried 
$ allow|deny RULE
bash: allow: command not found
bash: deny: command not found
Tried $ sudo  allow|deny RULE
sudo: allow: command not found
bash: deny: command not found
All I could was disable it. 
Downloaded the updated version but still confused.

Disabled the firewall but still unable to save the picture. Must be missing some program. Thus I will enter question for saving the picture.

Please help understand how to tweak the firewall.

---

### Post by rogeriopvl on 2008-08-28
> **Camilia said:**
> 
Please help understand how to tweak the firewall.

I already told you the easiest way to do it...

Although I think that the fact that you can't save that picture has nothing to do with the firewall, normally firewall blocks connections, not files.

---

### Post by Camilia on 2008-08-28
> **rogeriopvl said:**
> I already told you the easiest way to do it...

Although I think that the fact that you can't save that picture has nothing to do with the firewall, normally firewall blocks connections, not files.

Tried
$ allow|deny RULE
bash: allow: command not found
bash: deny: command not found
Tried $ sudo allow|deny RULE
sudo: allow: command not found
bash: deny: command not found
All I could was disable it.

---

### Post by rogeriopvl on 2008-08-28
has I said previously, download the application in [http://gufw.tuxfamily.org](http://gufw.tuxfamily.org) .. this app let's you configure the firewall with buttons and windows and stuff... it will be easier for you...

---

### Post by Camilia on 2008-08-29
[QUOTE=rogeriopvl;5679983]has I said previously, download the application in [http://gufw.tuxfamily.org](http://gufw.tuxfamily.org) .. this app let's you configure the firewall with buttons and windows and stuff... it will be easier for you...

I clicked install.deb and got the latest firewall. I don't understand the configurations. Tried downloading picture with it off and it didn't work, thus possibly software problem. Thus I turned the firewall on. I only understand enable and disable.

---

### Post by hyper_ch on 2008-08-29
are you sure you even need to alter the default firewall settings?

---

### Post by Camilia on 2008-08-29
hyper_ch
I don't think it wise to say Ubuntu will never be hacked. If some effort is not put forth your the first to be attached.

---

### Post by hyper_ch on 2008-08-29
And how will a firewall help you to be hacked?

Firewalls: Limit incoming/outgoing connection options

This requires that you must run some kind of server that actually listens to outside requests coming in.

So, if you have no such server running, how can they get in? --> No firewall needed

But if you do want to run a server, lets say a webserver, then you also want people to be able to connect to it? --> So you don't want it to be limited, hence no firewall needed

Besides, you are very likely behind a router, right?

---

### Post by rogeriopvl on 2008-08-29
> **hyper_ch said:**
> And how will a firewall help you to be hacked?

Firewalls: Limit incoming/outgoing connection options

This requires that you must run some kind of server that actually listens to outside requests coming in.

So, if you have no such server running, how can they get in? --> No firewall needed

But if you do want to run a server, lets say a webserver, then you also want people to be able to connect to it? --> So you don't want it to be limited, hence no firewall needed

Besides, you are very likely behind a router, right?

Even without a server running, I think that at least every non tech savvy user should have a firewall running.

People accidently install software that listens on the network, and the firewall is an additional layer of security that avoids total exposure to possible attackers in those situations.

---

### Post by hyper_ch on 2008-08-29
> **rogeriopvl said:**
> Even without a server running, I think that at least every non tech savvy user should have a firewall running.
Why? If no services are running a firewall is useless...

> **rogeriopvl said:**
> People accidently install software that listens on the network, and the firewall is an additional layer of security that avoids total exposure to possible attackers in those situations.
Most people are behind a router through their modem. So only if they forward ports from the router to the machine it can be accessed. Hence "accidental" installation does not pose any security thread.
Furthermore you assume that all services are by default very unsecure. If the services are secure, no firewall is needed, only security updates.

I invite you to name a few those hazardous services that people acciedentally install :)

---

### Post by rogeriopvl on 2008-08-29
> **hyper_ch said:**
> Why? If no services are running a firewall is useless...


Most people are behind a router through their modem. So only if they forward ports from the router to the machine it can be accessed. Hence "accidental" installation does not pose any security thread.
Furthermore you assume that all services are by default very unsecure. If the services are secure, no firewall is needed, only security updates.

I invite you to name a few those hazardous services that people acciedentally install :)

You are assuming that everyone is behind a router. Allot of people use Ubuntu in a laptop, and "travel" with it from wifi network to wifi network, not every network has "trusted hosts" not every network offers you a gateway ip address. For example, you probably know the Eduroam wifi network? Which is present in almost every european university. when you connect to that network you get a public IP address.... wich is bad if you don't have a firewall...

I didn't said that the services I mentioned were hazardous. I can give you the example of Apache, many people use it only for local web-development... and of course I assume services to be insecure, nothing is perfect... and I could name you some versions of apache that were in some way exploitable through port 80.

---

### Post by hyper_ch on 2008-08-29
> **rogeriopvl said:**
> You are assuming that everyone is behind a router.
most != all

> **rogeriopvl said:**
> when you connect to that network you get a public IP address.... wich is bad if you don't have a firewall...
Not really....

> **rogeriopvl said:**
> I didn't said that the services I mentioned were hazardous. I can give you the example of Apache, many people use it only for local web-development... and of course I assume services to be insecure, nothing is perfect... and I could name you some versions of apache that were in some way exploitable through port 80.
If apache is exploitable, that's a problem of apache and not the firewall. Do you agree there? Besides, those people that install apache for web-development know that it's a server, so it's not an unintentional install either and as they know it's a server they know it serves things.

Still no reason for average john doe to alter default firewall rules.

Anway, have a read here:  [http://ubuntuforums.org/showthread.php?t=765421](http://ubuntuforums.org/showthread.php?t=765421)

---

### Post by rogeriopvl on 2008-08-29
> **hyper_ch said:**
> 
If apache is exploitable, that's a problem of apache and not the firewall. Do you agree there?

Yes, I agree, but the firewall could protect against such exploit... it doesn't hurt to have another layer of security.

> **hyper_ch said:**
> Besides, those people that install apache for web-development know that it's a server, so it's not an unintentional install either and as they know it's a server they know it serves things.

Still no reason for average john doe to alter default firewall rules.
And what about a reason to not "turn it on" by default?

---

### Post by hyper_ch on 2008-08-29
> **rogeriopvl said:**
> Yes, I agree, but the firewall could protect against such exploit...
Why? If you run apache for local developement only then you will ahve apache configured to listen to local requests only... otherwise you want it to be open and a firewall doesn't help.

> **rogeriopvl said:**
> it doesn't hurt to have another layer of security.
It can :) when things don't run as they should you can spend quite some time to find out why...

> **rogeriopvl said:**
> And what about a reason to not "turn it on" by default?
What about it? By default iptables lets everything pass and that's good. Have you read the Ubuntu Security sticky?

---

### Post by Camilia on 2008-08-30
From what all have read I am beginning to think a firewall is unnecessary. I am going to keep in on though, for I do at times make mistakes. Seems it good for protecting me from me.

Thanks everyone!!

---

### Post by nbayiha on 2008-08-30
Yeah dude , the firewall in Ubuntu is useless, you don't and won't need it.

---

### Post by Free Me on 2008-12-07
Yeah I second that nbayina and I'll admit I've been a naughty boy when surfing and still haven't managed to become infected. Even those really helpful people (not) who jump in through open Windows (Firefox) might manage to run their nasty little programs on an open screen but upon restarting Ubuntu I have never been able to find any trace of their trojan/virus.

---

### Post by kevdog on 2008-12-07
If you are going to be running listening processes then a firewall may provide one layer of security.  There are other methods available also (host allow,deny file, individual /etc files of the listening process).  If you are not going to be running listening processes, then a firewall provides no additional protection

---

### Post by Kinstonian on 2008-12-07
Here is why I think people should use a firewall.

[QUOTE=Kinstonian]
I think the people who say Ubuntu doesn't need a firewall because it doesn't have ports open make a few erroneous assumptions...

1.  **Firewalls are only useful for filtering inbound connections**:  If you only look at a firewall as filtering inbound connections, you only see half of it's potential.  What about filtering *outbound* connections with suspicious protocols, or to known bad IPs like the [Russian Business Network](http://en.wikipedia.org/wiki/Russian_Business_Network)?

2.  **All protocols use ports**:  There are protocols like ICMP which don't use ports.  It's not only commonly used for information gathering in attacks, but it's not unreasonable to think history could repeat itself and there could be a vulnerability in the way it's handled by the OS.

3.  **Firewalls are only for preventing attacks**:  While they are no doubt preventative controls, by analyzing the logs they generate they can detect both failed and successful attacks.  If you look at firewall logs from inbound traffic you can detect attacks and take actions.  If you look at firewall logs from outbound traffic like outbound IRC or SMTP traffic to China was blocked, you could have detected a successful attack.

4.  **At no point will there ever be an open port**:  There is a chance that at some point someone could open a port.  Whether it was from the administrator making a mistake in installing/configuring software, or it could be an attacker purposefully using your computer as a server to store and distribute contraband, or perhaps using your computer to host a phishing site.[/QUOTE]

---

### Post by kevdog on 2008-12-07
> If you look at firewall logs from outbound traffic like outbound IRC or SMTP traffic to China was blocked, you could have detected a successful attack


How does this constitute an attack??  

A lot of theoretical arguments on your list.  I guess it would depend if you are running a router or server.  If not running any type of server, then it really doesnt matter.

And ICMP packets being accepted or rejected -- so what?  You can't prevent a flood with firewalls.

---

### Post by Kinstonian on 2008-12-07
> **kevdog said:**
> How does this constitute an attack??  

A lot of theoretical arguments on your list.  I guess it would depend if you are running a router or server.  If not running any type of server, then it really doesnt matter.

And ICMP packets being accepted or rejected -- so what?  You can't prevent a flood with firewalls.


There is often suspicious and flat out malicious outbound traffic relating to intrusions.  If you are looking at your firewall logs and you notice your firewall has blocked outbound IRC traffic, your computer is doing a port scan or port sweep, or is sending spam, trying to SSH to another country, etc. and you can't account for that traffic-- you are probably compromised.  There is an entire software market for dealing with and analyzing logs, including firewall logs.  Logs and network security monitoring isn't "theoretically" useful, it is useful.

As for ICMP, I'm not talking about a ping flood.  As I said, historically ICMP has been used for recon, and it hasn't been uncommon for there to be vulnerabilities found in ICMP.  A quick search of the [Common Vulnerabilities and Exposures](http://cve.mitre.org/cgi-bin/cvekey.cgi?keyword=icmp) for ICMP turns up quite a few results.  Not all of those ICMP problems are for *nix, but you get the point.  These aren't theoretical vulnerabilities either.

---

### Post by kevdog on 2008-12-07
Show me a log file from one linux system where rogue outbound traffic has been detected, when there has been no previous servers ever running on the machine!!

As far as ICMP, I read through the list you from the post you provided.  Where does anyone of this bugs, actually lead to a compromised system?  A bug or crash is a separate issue, as well as a DNS attack.

---

### Post by Kinstonian on 2008-12-07
Well, there are two general types of software vulnerabilities.  **Server side** which focus on exploiting vulnerabilities in services, and **client side** which focus on exploiting vulnerabilities in client software.  This is why it's commonly recommended to use NoScript when browsing the web, and keep your web browser patched.  So just because you don't have any services available, doesn't mean you're impervious to attack.

As for your other point on ICMP...  For one, I remember just last year there was a vulnerability in ICMPv6 that could result in root privileges on OpenBSD of all things.  Secondly, why do you think DoS attacks aren't worth preventing?  Third, like I said it has also been used in recon.  Fourth, other attacks not related to DoS or recon have existed such as ICMP router redirects or covert channels.  I'm sure you understand how important defense in depth and the principle of least privilege are on the host level, so you should also understand why they're important on the network level.

---

### Post by kevdog on 2008-12-07
Use of a firewall can not stop DoS attacks.  Its not that I don't think they are pointless, its just that IPtables can not prevent them. 

Your discussion regarding NoScript and client side vulnerabilities is a little off topic.  Firewalls can not block by application.  I suppose you could examine and find unknowing packets being passed by examining the firewall iptable log, however you could do the same if you were running Wireshark and examining outgoing packets as well.  I don't think this ability to detect rogue outgoing packets is unique to iptables. If you do find rogue outgoing packets by either method, I would recommend a complete reinstall, since blocking only the destination IP address via iptables does not guarantee complete protection.  You have no idea if different IP addresses will be contacted in the future.  

I dont know anything regaring ICMPv6 -- do not use it, can't speak intelligently on the topic.

---

### Post by Kinstonian on 2008-12-07
> **kevdog said:**
> Use of a firewall can not stop DoS attacks.  Its not that I don't think they are pointless, its just that IPtables can not prevent them.

There are bandwidth consumption DoS attacks that are difficult for firewalls to prevent, but there are also software vulnerability DoS attacks that I was referring to, and which a firewall can prevent easily by blocking the traffic.

> **kevdog said:**
> 
Your discussion regarding NoScript and client side vulnerabilities is a little off topic.  Firewalls can not block by application.  I suppose you could examine and find unknowing packets being passed by examining the firewall iptable log, however you could do the same if you were running Wireshark and examining outgoing packets as well.  I don't think this ability to detect rogue outgoing packets is unique to iptables. If you do find rogue outgoing packets by either method, I would recommend a complete reinstall, since blocking only the destination IP address via iptables does not guarantee complete protection.  You have no idea if different IP addresses will be contacted in the future.

When I was talking about detecting suspicious outbound traffic generated from programs run by attackers after they compromise your computer, you said:

*"Show me a log file from one linux system where rogue outbound traffic has been detected, when there has been no previous servers ever running on the machine!!"*

So, yeah you may not see suspicious outbound traffic after getting compromised by a server side vulnerability since there are no listening services running, but you could get compromised by a client side vulnerability and then detect the following suspicious traffic.

And yes, you're right... you could get similar visibility as to what is happening on your network by using Wireshark.  In a perfect world people would use both iptables and Wireshark...

---

### Post by q.dinar on 2008-12-31
> **Camilia said:**
> Tried
$ allow|deny RULE
bash: allow: command not found

i think that should be written 

gufw allow

or

ufw allow

---

