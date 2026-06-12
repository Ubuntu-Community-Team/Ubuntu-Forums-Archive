---
title: "Macs Hit by Backdoor Attack is this possible with linux??"
date: 2010-04-18
forum: Security
---

### Post by denzykabzy on 2010-04-18
Hi there guys!
I'm a pretty new to ubuntu, so i know that there are some pretty obvious facts that I'm not  aware of. I wanted to ask some questions that I hope someone can help me with. 
1. How similar is linux similar to unix?
2. I just read an article in pc world that talked about hackers using a back door in that mac os programming to hack computers. Is this possible with linux? (thought that mac os was very safe)
[http://www.pcworld.com/article/194462/macs_hit_by_backdoor_attack.html](http://www.pcworld.com/article/194462/macs_hit_by_backdoor_attack.html)
3. With linux growing in popularity isn't it just a matter of time before hackers try to hack linux?
thanks :)

---

### Post by jrusso2 on 2010-04-18
That article is not very descriptive as to what the attack is and how it is introduced.

---

### Post by denzykabzy on 2010-04-18
here are other links
[http://www.pcworld.com/businesscenter/article/194409/new_malware_can_take_control_of_macs_intego_warns.html?tk=rel_news](http://www.pcworld.com/businesscenter/article/194409/new_malware_can_take_control_of_macs_intego_warns.html?tk=rel_news)
[http://www.intego.com/news/hellrts-backdoor-can-allow-malicious-remote-users-to-control-macs.asp](http://www.intego.com/news/hellrts-backdoor-can-allow-malicious-remote-users-to-control-macs.asp)

---

### Post by Armor Nick on 2010-04-19
The security of a computer always depends on the user. Don't use sudo regularly, don't install software you just found somewhere on a forum, and keep your firewall enabled. In a way, the big amount of users windows has is indeed the cause of all its hackers; the more users, the more noobs using it.

---

### Post by armandh on 2010-04-19
according to arstechnica it requires instillation through access to the computer or social engineering / user stupidity

yes bad things can happen to a secure OS
ware rm

---

### Post by BlueWolf_ on 2010-04-19
> **denzykabzy said:**
> 3. With linux growing in popularity isn't it just a matter of time before hackers try to hack linux?
thanks :)

If Linux would gain more people, then yes, more hackers would probably try to hack Linux. But due to it's nature it's far harder to hack Linux compared to Windows (where you actually need extra software to protect your system). And even when a hacker finds a exploit in Linux, a fix can easily be be send to all computers within a few days using the updater.

edit: I'm talking about a exploit here. I've no idea how new users will act (typing their password into some unsecure program and getting hacked that way)

---

### Post by Native Dialect on 2010-04-19
Linux is generally pretty safe. All unnecessarily open ports, are closed (ports that allow incoming, not outgoing). From there, any driver change, hardware configuration or program installation or removal, requires your password. So if you are typing up a graduate paper in Open Office, and suddenly the password prompt pops up, you know something is wrong, and that you should not input your password. 

Honestly, internet security is all about PEBKAC (Problem Exists Between Keyboard and Chair) a.k.a. the end-user. As long as you exercise safe habits (being careful about what you download from what repository, what commands you enter in the terminal etc), you will be fine. If you are really worried, you can download Firestarter and configure a firewall through a GUI based prompt. It is redundant, but it helps provide peace of mind. I myself have Firestarter, for just that reason.

---

### Post by DrMelon on 2010-04-19
There are people out there who are not careful and install anything, without checking if it is safe first - you can't force this kind of software on a Linux or Mac machine, the user has to make the mistake of running it with full system priveledges.

---

### Post by LeeDaugherty on 2010-04-20
The Hellraiser trojan (RAT) is deployed through typically "pirated" dmg files (this particular one hides in iphoto), these by default wouldn't work in Linux.  The code it uses is actually almost exclusively written for Mac's too, it should be noted this variant infect PowerPC's too!  This trojan isn't known to be deployed via drive-by, so it would require a download of sorts.

---

### Post by d3v1150m471c on 2010-04-20
Yes, it's possible. Though, it would have to be written for linux.

---

### Post by Grenage on 2010-04-20
It's been said a hundred times, but...

An OS is only as secure as the user; if the user installs random applications, there is no saving them.  Linux currently has such a small user base compared to Windows, there aren't many malicious apps.

Windows/Mac/Linux, they're all quite quite secure when used correctly.

---

### Post by P4man on 2010-04-20
Linux is certainly not immune to trojans. However, if you stick to the official repositories (or ones you trust) then the risk of getting a trojan is almost nihil. Using trusted repositories ("ubuntu software center") to install software from, rather than googling and downloading semi randomly is really what sets linux apart from windows in this aspect of security (and from OS-X, although iphone/ipad users could claim something similar with the appstore).

---

### Post by Ko$ on 2010-04-20
"backdoor" is the thing (as it sounds) is back door of shell. Almost every "script-kids"`s attack begins from web server, so they can run a script that will open "back door" on a port. Therefore if your services are run on defined ports, then with a firewall you can close all incoming connections to other ports (so if a "backdoor" opens on port 31338 (for example), an attacker can`t connect to it). It`s very hard to get the root account remotely (that can change the rules of a firewall), so there is no critical danger.

---

### Post by Native Dialect on 2010-04-20
> **Grenage said:**
> It's been said a hundred times, but...

An OS is only as secure as the user; if the user installs random applications, there is no saving them.  Linux currently has such a small user base compared to Windows, there aren't many malicious apps.

Windows/Mac/Linux, they're all quite quite secure when used correctly.

Exactly. most people who contract a virus, are people who are doing activities that put them in harm's way. It would be like walking through a neighborhood that is known for gang activity, after 8pm. You may be able to make it through, but you are putting yourself at risk by doing it. Computers are no different. If you visit a Warez site or download mp3s from Limewire, then expect that you may be attacked.

---

### Post by silkworm2.5 on 2010-04-20
> **Native Dialect said:**
> Linux is generally pretty safe. All unnecessarily open ports, are closed (ports that allow incoming, not outgoing). From there, any driver change, hardware configuration or program installation or removal, requires your password. So if you are typing up a graduate paper in Open Office, and suddenly the password prompt pops up, you know something is wrong, and that you should not input your password. 

Honestly, internet security is all about PEBKAC (Problem Exists Between Keyboard and Chair) a.k.a. the end-user. As long as you exercise safe habits (being careful about what you download from what repository, what commands you enter in the terminal etc), you will be fine. If you are really worried, you can download Firestarter and configure a firewall through a GUI based prompt. It is redundant, but it helps provide peace of mind. I myself have Firestarter, for just that reason.

Hm, Nice to know about the ports thing. But what should we do if the password request comes up? Don't allow obviously, but then what? post it here? Or is there a terminal code we can enter to gather info on the attack?

Btw, I like your sig : )

---

### Post by Native Dialect on 2010-04-20
If it were to occur on my system, I'd cancel the login prompt. Then, depending on what other activity seemed out of place, I would enter the terminal and run the command netstat -v

I'd check to see what (or who) is connected to my machine. I'd jot down any information I felt was useful, and see what I could find. The trouble though, is that if somebody is watching your system and you use netstat -v, you will have to put in your password anyway. So that would be risky. 

There is also the option of disconnecting your computer from the Internet (turn off your wi-fi, or unplug your ethernet). Configure the firewall (either manually adjusts your ports or you can get Firestarter, which is a GUI based configuration tool for Linux firewalls). If you are feeling safe about browsing, you could get an anti-virus. Alternatively, you could use another connected PC, to download an anti-virus program and then install that onto your Linux system. 

There are a lot of ways to go about it. Perhaps other users have some thoughts about what they would do if the password prompt came up, without any action on their part.

---

### Post by Dayofswords on 2010-04-20
from article comments:
> [QUOTE]Could this malware turn my iPad into some sort of robot thingie which could turn against me, and even murder me in my sleep?


One could only hope.[/QUOTE]

oh a good laugh

---

### Post by denzykabzy on 2010-04-21
> **Native Dialect said:**
> If it were to occur on my system, I'd cancel the login prompt. Then, depending on what other activity seemed out of place, I would enter the terminal and run the command netstat -v

I'd check to see what (or who) is connected to my machine. I'd jot down any information I felt was useful, and see what I could find. The trouble though, is that if somebody is watching your system and you use netstat -v, you will have to put in your password anyway. So that would be risky. 

There is also the option of disconnecting your computer from the Internet (turn off your wi-fi, or unplug your ethernet). Configure the firewall (either manually adjusts your ports or you can get Firestarter, which is a GUI based configuration tool for Linux firewalls). If you are feeling safe about browsing, you could get an anti-virus. Alternatively, you could use another connected PC, to download an anti-virus program and then install that onto your Linux system. 

There are a lot of ways to go about it. Perhaps other users have some thoughts about what they would do if the password prompt came up, without any action on their part.
  thanks for the advice Native Dialect. The problem is that for many people who have just started using linux most of the learning we do is gleaned from trial and error, visiting forums and asking friends. But i think that that is what makes Linux great. Believe it or not i understood windows better after using ubuntu. After a few mistakes here and there and a few re-installations of ubuntu things begin to make sense. Ubuntu makes it so easy to start from scratch that your confidence begins to grow. Windows does not encourage experimentation. With all those cryptic errors it is a wonder that anyone can get anything done.

---

### Post by a.walker on 2010-04-21
> **denzykabzy said:**
> thanks for the advice Native Dialect. The problem is that for many people who have just started using linux most of the learning we do is gleaned from trial and error, visiting forums and asking friends. But i think that that is what makes Linux great. Believe it or not i understood windows better after using ubuntu. After a few mistakes here and there and a few re-installations of ubuntu things begin to make sense. Ubuntu makes it so easy to start from scratch that your confidence begins to grow. Windows does not encourage experimentation. With all those cryptic errors it is a wonder that anyone can get anything done.

Firestarter is no longer maintained. You should probably use UFW or GUFW (but remember to remove firestarter before configuring UFW. They don't like each other).

---

### Post by P4man on 2010-04-21
I dont really see the point of adding a "firewall" to ubuntu. Unless you are running services that you only want to be accessible from certain networks, it just gives a false sense of security and complicates things. 

If there is no software listening on those ports, closing them with a firewall is pointless. If you do have software running that listens on certain ports (say a bittorrent client or ssh server) then you want those ports open or it wont work (again, except if you want to restrict access to certain networks, like local network). For the vast majority of ubuntu users, a firewall is about as useful as a 5 year old antivirus is on windows.

---

### Post by shebaw on 2010-04-22
First of all, no system is 100% percent secure and like all of the guys here said, the user has a major role in making his system being secure. Having said that, Macs were hacked first for 3 years in a row in PWN-2-HACK contest, I really believe that Macs won't be secure if they had more market share. But, security is by design, not by the number of the users using it. Linux dominates the server market but it's still secure. Windows is not secure because it is flawed by design and has the major market share. Almost 95% percent of the "viruses" you see out there are made by script kiddies because of this.

---

