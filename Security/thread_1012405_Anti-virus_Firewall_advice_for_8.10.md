---
title: "Anti-virus/ Firewall advice for 8.10?"
date: 2008-12-15
forum: Security
---

### Post by frankwakeman on 2008-12-15
I use Avast with Windows Vista and I see it is available for Linux.  I've read some people don't use a/v software at all with Linux, but I'd have thought - I imagine it's now a cliche - that Linux will get more an more risky as it gets more popular, and I had my old XP laptop cabbaged by viruses.  I've had Ubuntu 8.10 for three days, via Wubi dual-boot.

I don't want to be learning too much technical stuff.  What security should I be adding?  I'd like to stick with Avast if the Linux version is as reputable - would that be okay on its own without a firewall program, and if not, which is the simplest and most reputable?

Thanks.

---

### Post by ArcticWalrus on 2008-12-15
this is going to go up in flames.........

---

### Post by tuxxy on 2008-12-15
You only need an AV if you are currently or plan to regularly access or share files with another windows drive/user.

ClamAV and Avast are both good choices :)

---

### Post by cariboo on 2008-12-15
> I don't want to be learning too much technical stuff. What security should I be adding? I'd like to stick with Avast if the Linux version is as reputable - would that be okay on its own without a firewall program, and if not, which is the simplest and most reputable?


If you plan on using Ubuntu to it's fullest, you are going to have to learn some of that technical stuff. 

If you are behind a router you shouldn't need a firewall. If you do need a firewall, because you are running services that are listening and open to the internet, I would suggest you install GUFW which is a gui interface for the firewall that is installed by default when you install Ubuntu.

Gufw is available in the repositories.

Jim

---

### Post by bodhi.zazen on 2008-12-16
> **frankwakeman said:**
> I use Avast with Windows Vista and I see it is available for Linux.  I've read some people don't use a/v software at all with Linux, but I'd have thought - I imagine it's now a cliche - that Linux will get more an more risky as it gets more popular, and I had my old XP laptop cabbaged by viruses.  I've had Ubuntu 8.10 for three days, via Wubi dual-boot.

I don't want to be learning too much technical stuff.  What security should I be adding?  I'd like to stick with Avast if the Linux version is as reputable - would that be okay on its own without a firewall program, and if not, which is the simplest and most reputable?

Thanks.

Well, first thing, Linux is not windows.

So while there is malware for Linux, it is not the same as Windows malware.

See this link : [http://www.theregister.co.uk/2003/10/06/linux_vs_windows_viruses/](http://www.theregister.co.uk/2003/10/06/linux_vs_windows_viruses/)

So at this time , viruses on Linux are a non issue. You can install all the antivirus you wish and you will not significantly increase your security as you an not vulnerable to that kind of attack either before or after you install antivirus.

Linux is a new OS and, as with other aspects, you will need to learn some new security strategies.

I suggest you start with the stickies on this forum. Spend as much or as little time as you wish.

I suggest you learn what a root kit is. How to secure any server you run. How to configure your firewall, and why or why not to use it. Learn how to use root kit scanners and tiger.

Then look at apparmor.

OSSEC is easy to use also.

Only you can decide how much or little you wish to learn, how much time you want to spend on it. Either way I would not rely on your Windows background or antivirus too much.

---

