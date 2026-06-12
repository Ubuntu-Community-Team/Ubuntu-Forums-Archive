---
title: "As a result of the WannaCry ransom ware worm spreading virus"
date: 2017-05-15
forum: Security
---

### Post by Neill_R on 2017-05-15
Hi
 Looking around, I find the BBC is a source of news about this **WINDOWS RANSOM WARE VIRUS. **I  am amazed but not surprised that there is no mention of an alternative  to WINDOWS. If anyone knows of any articles I have missed where the UK  government is pointing out the fact that Linux is a much more secure  operating system then please let me know.
 In Looking for articles about Linux I came upon the Dirty COW
 [CENTER][http://www.bbc.co.uk/news/technology-37728010](http://www.bbc.co.uk/news/technology-37728010)
[/CENTER] [CENTER][https://insights.ubuntu.com/2016/10/31/dirty-cow-was-livepatched-in-ubuntu-within-hours-of-publication/](https://insights.ubuntu.com/2016/10/31/dirty-cow-was-livepatched-in-ubuntu-within-hours-of-publication/)[/CENTER] So I have followed the instruction and also install the anti-virus software CLAMAV on the principle BETTER SAFE THAN SORRY.
 
[LIST=1]
[*]If needed then visit [https://login.ubuntu.com](https://login.ubuntu.com) create an account
[*]Visit [https://login.ubuntu.com/](https://login.ubuntu.com/) Login with your (new) account
[*]Visit [https://auth.livepatch.canonical.com/](https://auth.livepatch.canonical.com/) and select Ubuntu user and obtain the token
[*]In a terminal I ran (<ctrl><alt><T>)
[LIST]
[*]  sudo apt install unattended-upgrades
[*]  sudo dpkg-reconfigure unattended-upgrades
[*]  sudo snap install canonical-livepatch
[*]  sudo canonical-livepatch enable 55ac9908exxx442d82a6f39e7193e215
[*]  sudo apt-get update
[*]  sudo apt-get upgrade
[*]  sudo apt-get autoremove
[*]  sudo apt-get upgradesudo apt install clamav clamav-freshclam clamtk
[*]  sudo killall freshclam
[*]  sudo freshclam
[*]  sudo apt-get install gufw (and turned it on)
[/LIST]
[/LIST]
 So my question, to all, is how safe is my system now? Please tell me of  the things you do or check for to ensure your system's safety and  security.

From [ a post ]("https://ubuntuforums.org/showthread.php?t=2361144&p=13644789#post13644789") by [SeijiSensei]("https://ubuntuforums.org/member.php?u=698195")> Moreover, even if wine were infected somehow, you could just replace  your ~/.wine directory with yesterday's backup.  You do have yesterday's  backup of /home, right?  I keep an archive of clean VirtualBox images  for the same reason.  If one somehow got infected, I'd just blow it away  and revert to my clean image.
Neill

---

### Post by TheFu on 2017-05-15
Securing a system isn't a 1-time thing. Attacks change hourly.  We need to change our protective methods constantly as well.

I do not run any anti-virus on my Linux systems.  
I do not use my Windows systems for general use, never browse the internet with them and don't view files that I didn't create on them.

I have NOT patched my Win7 systems in over a year, due to the new EULA pushed by Microsoft back then with their "telemetry" updates for Win7, Win8, Win8.1 and Win10 systems.  For me, privacy is more important than being patched from Microsoft.  I am not concerned these systems are at risk.  

Thanks vasa1!

Ok - Linux is an alternative in many situates, but not all. Around 2004, I was asked by my management chain to find a way to replace Windows on some laptops at work, 22K of them.  These laptops were being infected with Windows viruses all the time since they were used to troubleshoot client's networks.  The laptops also ran about 15 highly specialized hardware diagnostic applications. Each of those applications costs many $$$millions to purchase from the software vendors.  These vendors only supported WinXP. No other OS.  I asked a few of them for a quick, ballpark guess, for costs to support any Linux they wanted.  Most came back with $100+M estimates. Some said that they were dependent on other SW venders underneath their code who only supported WindowsXP too.  We were not in healthcare, but I have friends who are and they run into similar issues.  

Health care systems WinXP is commonly mandated. Additionally, to get any support from the vendor, remote access into the systems is required by contract.  That remote access is through the internet ... so being disconnected from the network isn't a viable option.  [If I were in charge, I'd only connect those computers during agreed maintenance windows, which would be in the contract.]

Many Windows viruses spread using SMB/CIFS.  If you want to be more secure, don't use that protocol. That is a hard decision because the other, more secure, protocols aren't as convenient. A few of the other options are less secure than CIFS too (like webdav, IMHO).

Anyway, the point is that alternative OSes isn't always possible.  I'm a Linux zealot.  LUG organizer, F/LOSS pusher, but sometimes there isn't an option.

As for securing a Linux system, there are hundreds of other things which *may* be done.  There is a sticky thread at the top of the Security sub-forum here with fairly simple steps to improve security.  Nothing can replace an alert end-user.  If you'd like more after reviewing that thread, just post specific questions.

---

### Post by Neill_R on 2017-05-15
thanks for reply and views

---

### Post by sp40140 on 2017-05-15
> **TheFu said:**
>  Nothing can replace an alert end-user.  If you'd like more after reviewing that thread, just post specific questions.

Agreed here.
The one thing to note is that lots of issues arise from bad (lazy) development practices.
At a firm I consulted at, they bought a vendor application (multi MM $ contract). It was JAVA web application. Running on on-premise (Rad Hat) servers. But ran couple small pieces of functions on IE specifically. This is so utterly stupid that I couldn't believe it. Whats more, I worked with their dev a lot, and they used chrome to work on the app and de-bug most of the app. They said it was easier! It baffles me still.
Point is this app can on any os any browser if they just spend half day of dev and a week most of man-hour to avoid IE specifics. 

And practices like these today cause issues in future. (just like this WannaCry thing).

---

### Post by bashiergui on 2017-05-16
> **sp40140 said:**
> Agreed here.
The one thing to note is that lots of issues arise from bad (lazy) development practices.
At a firm I consulted at, they bought a vendor application (multi MM $ contract). It was JAVA web application. Running on on-premise (Rad Hat) servers. But ran couple small pieces of functions on IE specifically. This is so utterly stupid that I couldn't believe it. Whats more, I worked with their dev a lot, and they used chrome to work on the app and de-bug most of the app. They said it was easier! It baffles me still.
Point is this app can on any os any browser if they just spend half day of dev and a week most of man-hour to avoid IE specifics. 

And practices like these today cause issues in future. (just like this WannaCry thing).
It would be nice if we could only develop for the latest and greatest. But the sad reality is that businesses need to create software that works for their customers, which means it's developed for the lowest common denominator. The software you're referring to was probably developed that way because a major customer of theirs needs to use IE.

---

### Post by mastablasta on 2017-05-16
clamav is not that good at detecting threats. it is stil better than nothing.

i would go with Avast or at least Comodo (not sure if they are free on linux).
[https://www.avast.com/en-us/faq.php?article=AVKB131](https://www.avast.com/en-us/faq.php?article=AVKB131)

Avira and Bitdefender also had some linux verisons and free.
this and similar performance has beed there for some time now:
[http://www.networkworld.com/article/2989137/linux/av-test-lab-tests-16-linux-antivirus-products-against-windows-and-linux-malware.html](http://www.networkworld.com/article/2989137/linux/av-test-lab-tests-16-linux-antivirus-products-against-windows-and-linux-malware.html)

clam av has low detection. comodo has about 80 % and avast over 95%.

---

### Post by sp40140 on 2017-05-16
> **bashiergui said:**
> It would be nice if we could only develop for the latest and greatest. But the sad reality is that businesses need to create software that works for their customers, which means it's developed for the lowest common denominator. The software you're referring to was probably developed that way because a major customer of theirs needs to use IE.

I have been a developer. Believe me, I know the constraints. But it's 2016. Even MS recommends avoiding IE. And there are lots of alternative Browsers out there (better or not is not the point here). 
As to "Common denominator".. well, they could make the app standard and it would run on IE 9 as well as any other browser. So, clients can pick their own browser. I am not saying vendors avoid IE. In fact, we had to fight with vendor to make the next version of the app more standard (which we lost) as chrome was standard in our enterprise and the app only worked on IE9 (not even IE11).
Your point would have been absolutely accurate about 10 years ago not today.

---

