---
title: "trying to install snort"
date: 2009-04-19
forum: Security
---

### Post by tronnix75 on 2009-04-19
I recently have been out of work because of the economy so i have some time on my hands.  I bought a $50 compaq pc witha 2ghz processor and 1gig of ram, 40gig hard drive.  I installed the version 8.04 of ubuntu on it that i have on a burned cd.  I installed using all of hard drive.  I wanted to take the time and get my skills up at this time so i wanted to deploy this box as an IDS using snort, i did find bodhi.zazen guide but ran into some issues already with downloading the rules set, is there another guide that is more up to date with its codes as i am not familiar with all commands as of yet.  I also probably have an old version of ubunutu as well how do i update that besides update manager as i have already used update manager and downloaded all of the updates it had checked off. :)

---

### Post by ibuclaw on 2009-04-19
Which one of bodhi's tutorials was that then? (There are so many, I loose count).

Have you looked at his blog?
 [http://blog.bodhizazen.net/linux/snort-ssh/](http://blog.bodhizazen.net/linux/snort-ssh/)

Or is that the one you are already reading...

Regards
Iain

---

### Post by tronnix75 on 2009-04-20
no i am not using that one since i do not have a central server, this is a home network.  I am using this one

[http://ubuntuforums.org/showthread.php?mode=hybrid&t=919472](http://ubuntuforums.org/showthread.php?mode=hybrid&t=919472)

---

### Post by Dr Small on 2009-04-20
> **tronnix75 said:**
> no i am not using that one since i do not have a central server, this is a home network.  I am using this one

[http://ubuntuforums.org/showthread.php?mode=hybrid&t=919472](http://ubuntuforums.org/showthread.php?mode=hybrid&t=919472)
You should be able to get your rules from here:
[http://www.snort.org/pub-bin/downloads.cgi](http://www.snort.org/pub-bin/downloads.cgi)

Under "Community Rules".

---

### Post by bodhi.zazen on 2009-04-20
If you used update manager, there is a box called "check". That will determine if there are additiona updates, if not your system is up to date.

You can use the command line as well

```
sudo apt-get update && sudo apt-get dist-upgrade
```

Snort rules are downloaded from the snort site, you need to register or user the (very old) community rules. See the link I already gave you in the snort thread.

---

