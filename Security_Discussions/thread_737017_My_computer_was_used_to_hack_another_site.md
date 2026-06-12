---
title: "My computer was used to hack another site"
date: 2008-03-27
forum: Security Discussions
---

### Post by p0k3r808 on 2008-03-27
Yesterday when I tried to log on the internet I had a message from my internet service provider to call them and use a ticket number.  When I called they informed me that the FBI had contacted them and told them to shut down my internet because my computer was used in an online attack of microcyb.com  They said my open ports were 8080 and 81 the port 8080 is used on my ubuntu system and they said it was the ubuntu system that was used.  I realize I have to do a complete reinstall of the system, but after trying to restart so it would kill all the running processes my computer froze I manually powered it off and now it wont post.  Either the "hacker" did something to my system that would cause a no post issue or I am just having the worst luck ever.  
Now for the questions:
Any known fixes besides replacing my mobo?

Also any ways to prevent this in the future?

I run torrentflux on my computer and it utilizes the 8080 port, is there a way to secure this port more thoroughly  so that I can prevent this in the future and continue using my torrentflux program?

---

### Post by TenPlus1 on 2008-03-27
All I can think of is using a firewall like Firestarter from the repo's... The setup is really easy with a wizard and will let you enable/disble a lot of security features that may help...

---

### Post by jw5801 on 2008-03-27
Use a torrent client that doesn't use Port 8080 for a start :P 8080 is an alternative http port, so it's rather common to be open! Secondly I'd consider utilising a firewall, either at OS level or at your router (preferably both). You can then set up your router to forward all packets of a certain port number (NOT 8080) to your local IP and tell the firewall on your OS to only allow that program to access that port.

I'd also be curious to know what makes the FBI so certain it came from you? It's probably more likely they spoofed an IP than actually used your computer.

---

### Post by p0k3r808 on 2008-03-27
The FBI saw it was my IP/ISP and I wouldn't doubt it but they said it was using the 8080 and my ssh remotely I am just going off of the sites hacklog which had like 500 different ip adresses and such...  you can view the hacklog here:

[http://microcyb.com/HackLog.txt](http://microcyb.com/HackLog.txt)

---

### Post by opscure on 2008-03-27
More than likely the host (microcyb.com) has a trojan that opened port 80 and allowed someone (malicious) to do bad things with a spoofed IP/host.  They even have what looks to be a fix for spyware by disabling the micro$oft messaging service instead of removing the malware. You can see this from their unsecured indexable directory:
[http://www.microcyb.com/data/windows/msgr_spam_01.jpg](http://www.microcyb.com/data/windows/msgr_spam_01.jpg)
and 
[http://www.microcyb.com/data/windows/msgr_spam_02.jpg](http://www.microcyb.com/data/windows/msgr_spam_02.jpg)

In addition, one of the main dns entries that shows up in this "hack log" is eclub.lv

This domain is registered with the following information:
% Information from TLD .lv whois service.
% Please visit [http://www.nic.lv/DNS/](http://www.nic.lv/DNS/) for more information.

domain:      eclub.lv
admin-c:      2576-LUMII
tech-c:       2576-LUMII
nserver:      kabir.ot.lv
nserver:      ns2.deac.lv
nserver:      ns.ot.lv
changed:      [email]dns-reg@nic.lv[/email] 20051130
source:       LUMII

person:      
address:      none
phone:        +371-7204196
phone:        +371-29550568
e-mail:       [email]miha@ot.lv[/email], [email]mihail@sok.lv[/email], [email]zarra@zarra.net[/email]
nic-hdl:      2576-LUMII
source:       LUMII


According to the LATVIA DNS FAQ page the individual must include their personal information to register a domain.  see:
[http://www.nic.lv/DNS/En/faq.php](http://www.nic.lv/DNS/En/faq.php)

You should write your ISP and tell them to contact this registrar to obtain that information or perhaps direct the FBI to investigate the possible creators of the domains listed with the "Hacking Script URL".  

All and all, this seems to me that some low level webmaster compiled a list and sent it to the FBI.  The FBI's response was to do the easiest thing possible and just believe the information they were handed rather than investigating all possible origins of any such attack.  More than likely, the server this page is hosted on is infected with some form of malware and in turn is opening a door for someone to screw with them.  

Hope you don't loose you connection to the great series of "tubes"  :wink:

---

