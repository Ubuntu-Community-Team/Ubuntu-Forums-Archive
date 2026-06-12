---
title: "Tracking intruders"
date: 2011-08-05
forum: Security
---

### Post by stefangr1 on 2011-08-05
Recently, I was the victim of some hackers (it has now become very clear to me that weak passwords are a bad idea). I was able to track the attack back to some ip blocks, and now I'm curious who's behind it.

Does anyone know whether there is a database with old whois records or modifications of whois records? I would like to find out who were the previous owners of the ip-blocks that are related to the hack.

---

### Post by haqking on 2011-08-05
> **stefangr1 said:**
> Recently, I was the victim of some hackers (it has now become very clear to me that weak passwords are a bad idea). I was able to track the attack back to some ip blocks, and now I'm curious who's behind it.

Does anyone know whether there is a database with old whois records or modifications of whois records? I would like to find out who were the previous owners of the ip-blocks that are related to the hack.

google earth the ip addresses ;-)

---

### Post by stefangr1 on 2011-08-05
> **haqking said:**
> google earth the ip addresses ;-)

But that probably gets the geolocation from the (current) whois record of the ASN the ip is on, right? I'm interested in old whois records...

---

### Post by haqking on 2011-08-05
> **stefangr1 said:**
> But that probably gets the geolocation from the (current) whois record of the ASN the ip is on, right? I'm interested in old whois records...

when you whois the ip address it will show you the dates.

you mean you have done so and the attack was pre registration ?

but you said it was recent ?

also a whois will only return the ISP related information for your attacks or at best the router from which they came so it might show something like comcast or whatever as the individual machines are probably using nat.

as for the geolocation it will show you where and you cna find out who is an address easily enough, a whois might hide the registration information or ven be located at somewhere different to where the IP actually is

alot of whois services provide an archive service though like [http://www.who.is/domain_archive-ws/whois.ws/](http://www.who.is/domain_archive-ws/whois.ws/) however this wont allow you to seach via ip address only domain name

---

### Post by bodhi.zazen on 2011-08-05
IP addresses can be spoofed and the ip that you tracked my be a compromised windows machine who's owner is wondering why it is running so slow.

Unfortunately there is not much you can really do about this except register a complaint with the IP provider, who may or may not care, or law enforcement, who may or may not follow though.

Often these activities cross jurisdictions and international boundaries and until there is a fundamental change in the way "the internet" works all you can do is ...

1. Use strong passwords.

2. Avoid server that send passwords in the clear 
http -> use https
ftp -> use scp, sftp
vnc -> tunnel over ssh, use freenx, use VNC

3. Harden any servers you do install.

4. Work thorough the security sticky. Use apparmor.

---

### Post by stefangr1 on 2011-08-05
> **haqking said:**
> when you whois the ip address it will show you the dates.

you mean you have done so and the attack was pre registration ?

but you said it was recent ?

also a whois will only return the ISP related information for your attacks or at best the router from which they came so it might show something like comcast or whatever as the individual machines are probably using nat.

as for the geolocation it will show you where and you cna find out who is an address easily enough, a whois might hide the registration information or ven be located at somewhere different to where the IP actually is

alot of whois services provide an archive service though like [http://www.who.is/domain_archive-ws/whois.ws/](http://www.who.is/domain_archive-ws/whois.ws/) however this wont allow you to seach via ip address only domain name

My impression is that they use some spam method to generate network traffic towards compromised servers (like mine). These servers contain a small php scrip that redirect to websites of their own. The weird thing is these guys seem to run several hunderds of malicious websites on their own ASN, with a few /24's on it. They basically run their own mini ISP.

I've been trying to find who's behind this ASN, but it seems that the whois records are forged. The previous owner of their IP blocks / ASN may know who it was sold to, in addition to this it is possible that they have leased it. So that is why I'm wondering whether a history of mutations is kept.

---

### Post by stefangr1 on 2011-08-05
> **bodhi.zazen said:**
> IP addresses can be spoofed and the ip that you tracked my be a compromised windows machine who's owner is wondering why it is running so slow.

Unfortunately there is not much you can really do about this except register a complaint with the IP provider, who may or may not care, or law enforcement, who may or may not follow though.

Often these activities cross jurisdictions and international boundaries and until there is a fundamental change in the way "the internet" works all you can do is ...

1. Use strong passwords.

2. Avoid server that send passwords in the clear 
http -> use https
ftp -> use scp, sftp
vnc -> tunnel over ssh, use freenx, use VNC

3. Harden any servers you do install.

4. Work thorough the security sticky. Use apparmor.

You're very right on 1 :oops: . I know that it's probably useless to go after them, but I never got anything hacked before and now that it happened to me I was quite curious about how it happened. After a lot of digging, I found out that they have in fact a dedicated ASN just for sending spam and that made me even more curious.

---

### Post by steve11911 on 2011-08-13
The external links at the bottom of this page are worth a look:

[https://secure.wikimedia.org/wikipedia/en/wiki/Autonomous_System_Number](https://secure.wikimedia.org/wikipedia/en/wiki/Autonomous_System_Number)

---

### Post by blackcobra on 2011-08-15
Advise, use different passwords for everything, perhaps use kwallet or lastpass (Lastpass is in debat weather to trust, I wouldn't trust them with online banking or anything i consider to be important, but for things like ubuntuforum.org, i personally don't care if some gets that information). Above all, never use your sudo password for anything on the web, or give anyone remote access to your computer. Suggestion, if you do not use remote access, uninstall it.

---

