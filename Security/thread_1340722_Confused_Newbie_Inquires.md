---
title: "Confused Newbie Inquires?"
date: 2009-11-28
forum: Security
---

### Post by keesat_paul on 2009-11-28
I run a small server, and bought a debian iso disc on ebay to set it up. After initially installing the program everything was great for about 3 weeks, then one morning I tried to log-in (as it's on 24/7), when it changed the user and password on me!!
Locked-out!! I had a spare pc so installed the debian programme on that while trying to repair pc number one. I could not enter pc number one no matter what i done, and tried to boot both debian again, then windows xp, but the bios was fried! The damn thing cannot be fixed now. To add insult to injury, pc number two went the same way!! I changed the hard drives as told by in a local computer shop, but I think theres a trojan on the debian iso disc, as it is the only common denominator between them.
So, I bought a computer magazine with a copy of Ubuntu 9.04 on it and installed it on a new pc, number three!!
Guess what happened? I cannot get into it as it has locked me out just like the first two! I used to use ssh to access the files on the servers with winscp, but now the server is running ok, and i cannot enter it to change the config files???
I am at the end of my tether and finances, and really need someone to sort this mystery out for me, as no-one i know has any idea why the systems have locked me out??? What the hell is going on?? Please help me fix this!!!!!!

---

### Post by bodhi.zazen on 2009-11-29
I am sorry, but that post makes no sense at all.

First, if you wish to install Debian or Ubuntu, both are freely available. Download the Desktop, server, etc iso.

If your problem persists across multiple distros and replacement hardware my best guess would be you either mis-configured the server or you have a firewall somewhere.

---

### Post by samahad on 2009-11-29
**Yet Another Confused Newbie!**
I had loaded Ubuntu 9.04 on my EeePC at the store where I had purchased the hardware. It was my first Linux machine, so I did not pay much attention when store service staff loaded it. They did a good job and I played around with it for a few months. Now I have received Ubuntu 9.10. Was excited when I got it and went to load it and right away it asks for Admin password. Well I did not record it when the store service staff loaded my Ubuntu 9.04. How do I recover my Admin password from the last install of 9.04 so that I can proceed with the upgrade to 9.10?

---

### Post by bodhi.zazen on 2009-11-29
FYI , you are hijacking another's thread by asking an unrelated question of your own.

You should start your own thread.

Your admin password is the same as your log in password. Ubuntu uses sudo -

[RootSudo - Community Ubuntu Documentation]("https://help.ubuntu.com/community/RootSudo")

---

### Post by keesat_paul on 2009-11-29
Sorry bodhi.zazen that you think that my post makes no sense, but I need someone who knows what is wrong, or what I'm doing wrong, and proper solutions on how to fix them. Saying that it doesn't make sense tells me you don't know the solution, so maybe you should leave it at that buddy. Obviously this is in the right thread as I think that after my first 2 pc's were destroyed by this problem, that it must be a security issue as it sounds to me like someone is hacking my server and changing the user and passwords. What I need to know is, can someone hack my server, change the settings so I cant access my config files to change them, and if I have to start all over again and load ubuntu on a new pc from scratch, is there some security that a newbie like me can place on the server to illiminate the hacker as the reason for my frustration. 
Or, is it the case that the program is locking me out and changing the user and password by itself for some kind of self-protection?? Why is it doing this??
I don't wish to appear rude, but if anyone has had this happen to them, please explain what happened to you, and explain how to solved the problem, any helpful theorys will be appreciated, cheers.

---

### Post by wojox on 2009-11-29
How much did you pay for the free Debian disk?

---

### Post by keesat_paul on 2009-11-29
£3 on ebay buddy, including delivery. Couldn't burn a proper iso boot disc from downloads of debian. So thought I would get a copy from a trusted ebayer. Think that the disc had a trojan on it that screws your bios as that was the result for first 2 pc's with it. What I need to know now is why if I have a trusted copy from a linux magazine has the server magicly changed the user and password by itself? It must be a hacker??

---

### Post by cascade9 on 2009-11-29
> **keesat_paul said:**
> I run a small server, and bought a debian iso disc on ebay to set it up. After initially installing the program everything was great for about 3 weeks, then one morning I tried to log-in (as it's on 24/7), when it changed the user and password on me!!
Locked-out!! I had a spare pc so installed the debian programme on that while trying to repair pc number one. I could not enter pc number one no matter what i done, and tried to boot both debian again, then windows xp, but the bios was fried! The damn thing cannot be fixed now. To add insult to injury, pc number two went the same way!! I changed the hard drives as told by in a local computer shop, but I think theres a trojan on the debian iso disc, as it is the only common denominator between them.


I really, really, really doubt its a trojan. If you've been owned hard enough that someone can kill your BIOS, why would someone do that? Better to keep your machine as a zombie. Unless of course your x-girlfriend/x-boy friend/the dog you used to kick on the way to school is a major black hat hacker of course...

More likely you've got some major power issue. I havent heard of power spikes, etc, changing passwords, but it may well be possible. Its another common factor, and would explain why its now happened to your ubuntu install.

---

### Post by wojox on 2009-11-29
Well it's a little confusing. If you mean you can't log on through Windows with winscp, can't help. Stopped using Windows months ago. 

If you can't log on to your server with the monitior and keyboard attached, have a look at [resetting your password.]("http://www.psychocats.net/ubuntu/resetpassword"), okay budday?

---

### Post by keesat_paul on 2009-11-29
Cascade9 I doubt its a power serge, as I have it wired to an anti-surge adapter buddy.

---

### Post by cascade9 on 2009-11-29
Surge protectors don't protect against brownouts. Some of them will help with brownouts, for a little while anyway, but extended brownouts can, and do, happen.

---

### Post by cariboo on 2009-11-29
Just out of curiosity, when you install Debian, it asks you to set up a root password as well as a user password. Were you running as root or as a normal user when the problem occured?

Have you tried connecting a monitor and keybaord to the server and tried to log in as root or the user you set up?

I have to agree with bodhi.zazen, your post was confusing, as the only thing you really said was that you couldn't log in and that an operating system destroyed your bios.

---

### Post by rookcifer on 2009-11-29
This thread == FAIL

---

