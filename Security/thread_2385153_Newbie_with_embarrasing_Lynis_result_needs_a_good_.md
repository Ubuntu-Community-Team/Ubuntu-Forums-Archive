---
title: "Newbie with embarrasing Lynis result needs a good Samaritan please"
date: 2018-02-16
forum: Security
---

### Post by jimijives on 2018-02-16
Hi, I just tried to make a thread but it said something like a technical error when I posted, I didn't understand it at all.   I did use the pastebin link because it's a Lynis report I need help with please.

I'm a complete newbie and I only use the computer for chat and YouTube plus the odd newspaper, basically the idea of running a server freaks me out because it suggests remote login and I just got hacked so badly I had to throw my laptop out and the new laptop is so bad it can't even run Windows 10.
However I do like Ubuntu but I'm desperate to learn the very basics of how to block remote login and generally keep it as secure as possible because I'm paranoid the hackers might come back.

This is a link to a Lynis Audit and some stuff frightens me like not having a boot password because I made two passwords, one for disk encryption and one for the home folder.

I understand if I don't receive advice because it is a long file but I would be so grateful if someone could have a brief look and give me basic advice so I can browse the net in peace.

Thank you.

[https://paste.ubuntu.com/p/qBRwzNpdfM/](https://paste.ubuntu.com/p/qBRwzNpdfM/)

---

### Post by mikewhatever on 2018-02-16
You seem to be slamming in an open door. Remote login is not enabled by default in Ubuntu, so why are you desperate? It is also quite secure as is. 
It's pretty clear that the only thing that needs fixing is the attitude. Try to relax, there is no need to be paranoid.

---

### Post by jimijives on 2018-02-17
Hi mikewhatever, thanks for replying. I do realise I'm a little paranoid but it was the nature of the hack.  It was a group of people ranging in skill from script kiddies to Mr Robot.  I thought if I removed the hard drive and just used Ubuntu Live CD I would be ok but whatever they did was running programs sharing a symmetrical amount of RAM as I was.  I don't know how they managed that but it just feels as if they could hack any basic computer user if they wished to. So I want to Fort Knox my computer haha. Hopefully you're right and everything will be cool. I denied ports 22 and 23 in ufw, you think that would have any effect on ssh and ftp logins?  Also installed noscript so I hope that's enough.

---

### Post by mikewhatever on 2018-02-17
No, I don't think so. There is no ssh, telnet or ftp server installed/enabled by default. 
I am not sure what exactly we can help you with. Can you ask a more specific question.

---

### Post by jimijives on 2018-02-17
Well there is something bugging me.  I use Private Internet Access with Ubuntu 16 and sometimes it will be fine for hours and today for example it won't make any connections at all.  I have tried every port in the router and restarted all network devices.  Just seems strange it'll work one day and then not the next.  There isn't Ubuntu software or terminal commands I could try to fix it is there?

---

### Post by xalu on 2018-03-01
Hey,

I've also experienced a similar type of hack. I ended up with a bunch of infected devices due to lack of caution..heres a few pointers.

A grub password is for when the pc is booting. Someone could log into grub shell to make changes to the boot config. I'm not sure if this a remote-attack issue, or only in person, but there are guides for adding password protection.Lynis tool gives directions with links at the bottom. Follow those and it should help. Make sure to install sparkwire, debescan, needrestart ..etc.

 You don't have to follow all the suggestions and some you won't be able to when not running a server (ie nameservers)  so just take it one at a time. With a fresh install I believe the score is 65. I've managed to get mine to 75. 

Be careful some changes can cause errors so one at a time and restart may be a good idea. 

 If you have issues with pia try changing the settings in advanced settings. You may have accidently blocked a port range that it uses . You can see ports needed here:
https://helpdesk.privateinternetaccess.com/hc/en-us/articles/220934827-What-ports-are-used-by-your-VPN-service-

If you need a gui firewall try Gufw. It's a good way to start out and it shows what ports are trying to connect. 

EtherApe is useful for monitoring your network. When using pia make sure you pick the tunnel under interfaces. That's how pia connects. Nmap and netstat are command line tools you can use. 

Install clamtk for gui virus scanner but be sure to look up results. False positives are common. Bitdefender has an antivirus for Linux with free license.  

Logs are your only way to really be sure what's going on. So find a good log viewer or use watch /var/log/syslog type command to keep an eye out. 

I'd also recommend watching the /tmp directory as it's a common area for file creation and could be used by malware. Lynis recommends a few options to mitigate. 

Generally everyone is correct in saying by default these systems are secure. However, after a serious malware event it's best to be cautious until you're sure it's eliminated. If I had been, I'd have saved a ton of time. 

Best,
James

---

