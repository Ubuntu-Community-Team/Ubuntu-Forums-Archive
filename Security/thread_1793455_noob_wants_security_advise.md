---
title: "noob wants security advise"
date: 2011-06-29
forum: Security
---

### Post by delamite on 2011-06-29
i am still very new to Ubuntu (10.04), trying to learn as quickly as possible. what steps or programs do we need for security? i do a little of everything from paying bills to P2P, not unlike most. you will have to dumb down advise or draw with a crayon for me, but once i get it, i get it. i have purchased an older Linux book to study, i wish it included terminal excersizes to help cement learning commands. anyway, looking forward to help and learning.

---

### Post by doperative on 2011-06-29
> **delamite said:**
> i have purchased an older Linux book to study, i wish it included terminal excersizes to help cement learning commands. anyway, looking forward to help and learning.

You don't need to learn any terminal commands to use Ubuntu Linux and it's secure by default ...

---

### Post by haqking on 2011-06-29
> **doperative said:**
> You don't need to learn any terminal commands to use Ubuntu Linux and it's secure by default ...


mmm not sure i would agree there but that is open to debate i guess......i would say learn  the use of Terminal/CLI/Bash, but yeah pretty secure by default

start here
[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)

[https://help.ubuntu.com/community/Security](https://help.ubuntu.com/community/Security)


these above 3 should cover most things you need to know

and here are plenty of tutorials for you for CLI [http://www.tuxfiles.org/linuxhelp/cli.html](http://www.tuxfiles.org/linuxhelp/cli.html) there is tons on the net if you look though

most of the support posts you will get in response to questions on here will include use of the terminal so i suggest learn as much as you can about it, it is where the power and configuration lies.

---

### Post by Dangertux on 2011-06-29
I really wish people would stop saying Ubuntu is secure by default. It gives people a very false sense of security.

Yes if you install Ubuntu on a box plug it in, and never ever do anything with it other than just let it run and update, it is pretty secure by itself. However, if you use it for things, especially when you don't quite understand how Linux works it's rather easy to make it not secure. 

General OS best practices still apply :

+ Use the firewall you have (UFW). Yes Ubuntu ships with no running services, however if you unintentionally, or unknowlingly activate a service while trying to learn, this will give you a failsafe. 

+ Download updates (particularly security updates). Use the built in update manager, it's there for a good reason.

+ Use appropriate browser plugins (eg : no script, etc). While many browser based exploits don't specifically target Linux based OS'es it's better to be safe than owned.

+ Use the official repos, don't run shell scripts you don't know what they do, be careful when poking around as root or when using the sudo command. 

+ Strong passwords ; forgot to mention this earlier, but MyD0gSk1p!! is not a strong password.

+ Use common sense : Use your brain. A very smart man once said "Did you go looking for a program to download? No? Then why are you downloading one right now?"

---

### Post by haqking on 2011-06-29
> **Dangertux said:**
> I really wish people would stop saying Ubuntu is secure by default. It gives people a very false sense of security.

Yes if you install Ubuntu on a box plug it in, and never ever do anything with it other than just let it run and update, it is pretty secure by itself. However, if you use it for things, especially when you don't quite understand how Linux works it's rather easy to make it not secure. 

General OS best practices still apply :

+ Use the firewall you have (UFW). Yes Ubuntu ships with no running services, however if you unintentionally, or unknowlingly activate a service while trying to learn, this will give you a failsafe. 

+ Download updates (particularly security updates). Use the built in update manager, it's there for a good reason.

+ Use appropriate browser plugins (eg : no script, etc). While many browser based exploits don't specifically target Linux based OS'es it's better to be safe than owned.

+ Use the official repos, don't run shell scripts you don't know what they do, be careful when poking around as root or when using the sudo command. 

+ Use common sense : Use your brain. A very smart man once said "Did you go looking for a program to download? No? Then why are you downloading one right now?"

I agree completely with you, however semantically speaking all of that is post-default ;-)

so yeah i should of said in my above post that yes it is secure if you dont change anything which can be done by just trying to do something useful. ;)

semantics and all that ;)

---

### Post by haqking on 2011-06-29
> **Dangertux said:**
> I really wish people would stop saying Ubuntu is secure by default. It gives people a very false sense of security.

Yes if you install Ubuntu on a box plug it in, and never ever do anything with it other than just let it run and update, it is pretty secure by itself. However, if you use it for things, especially when you don't quite understand how Linux works it's rather easy to make it not secure. 

General OS best practices still apply :

+ Use the firewall you have (UFW). Yes Ubuntu ships with no running services, however if you unintentionally, or unknowlingly activate a service while trying to learn, this will give you a failsafe. 

+ Download updates (particularly security updates). Use the built in update manager, it's there for a good reason.

+ Use appropriate browser plugins (eg : no script, etc). While many browser based exploits don't specifically target Linux based OS'es it's better to be safe than owned.

+ Use the official repos, don't run shell scripts you don't know what they do, be careful when poking around as root or when using the sudo command. 

+ Strong passwords ; forgot to mention this earlier, but MyD0gSk1p!! is not a strong password.

+ Use common sense : Use your brain. A very smart man once said "Did you go looking for a program to download? No? Then why are you downloading one right now?"

oh out of interest what is your take on the"no need to learn CLI" ?

---

### Post by nomko on 2011-06-29
> **doperative said:**
> You don't need to learn any terminal commands to use Ubuntu Linux and it's secure by default ...

Wrong! In most cases it is even better to use terminal commands since those commands are more powerful then the standard GUI commands (think of commands which aren't even available as GUI command like uname or chmod). 

Linux is much safer than Windows because of its different architecture (Unix-based) and much better rights management. 

But also Linux counts: the greatest threat comes not from the internet, the greatest threat to the security of any computer system is behind the keyboard of his/her system, namely the (home) user itself! Ignorance, ignorance, inexperience, factors that forms a significantly disadvantage for the system protection.

---

### Post by uRock on 2011-06-29
> **Dangertux said:**
> I really wish people would stop saying Ubuntu is secure by default.

But it is secure, until you download and install applications from a third party site/repo or install a server application without configuring the firewall to prevent those servers from being accessed by uninvited sources. Mostly every network facing application has an AppArmor profile in effect by default to protect other parts of the system from being affected should the user visit an insecure site.

You listed common sense in your post, but common knowledge is only common to those who are knowledgeable in the subject. If internet security practices were common knowledge, then Norton and McAfee would be bankrupt.

---

### Post by nomko on 2011-06-29
> **Dangertux said:**
> I really wish people would stop saying Ubuntu is secure by default. It gives people a very false sense of security.

Linux is not a secure operating system, it's a operating system which works more secure then Windows. But both operating systems are still as save as the user uses it.

---

### Post by CandidMan on 2011-06-29
So long as you don't install stuff from outside trusted sources and follow the advice int hose stickies you'll probably be alright
IMHO the bigger concerns have little to do with your box like MITM attacks, cookie stealers, phishing, and DNS poisoning. All of which would leave your system intact but you in deep trouble.
Apologies for the brevity but am typing this from a blackberry

---

### Post by cariboo on 2011-06-30
> **nomko said:**
> Wrong! In most cases it is even better to use terminal commands since those commands are more powerful then the standard GUI commands (think of commands which aren't even available as GUI command like uname or chmod). 

Linux is much safer than Windows because of its different architecture (Unix-based) and much better rights management. 

But also Linux counts: the greatest threat comes not from the internet, the greatest threat to the security of any computer system is behind the keyboard of his/her system, namely the (home) user itself! Ignorance, ignorance, inexperience, factors that forms a significantly disadvantage for the system protection.

The terminal is more powerful, but in most cases the Ubuntu target user has no need for it. the average person that uses Ubuntu for surfing the net, checking webmail and playing games does not need to learn any commands, everything can and should be done using the gui tools provided.

---

