---
title: "Cleaning pc from keyloggers"
date: 2009-06-24
forum: Security
---

### Post by Jorrittjarks on 2009-06-24
hello,

I have recently been the victim of a key-logger who took my account details for the game world of warcraft. This happed in the last 2 weeks when i used windows as well next to ubuntu 9.04. Since the keylogger incident i found the trojan on my windows partition but couldnt remove it.

So i deleted and formated my windows partition, now my question is could the virus have transferd to my other partitions aswell and if so would it be able to work while i;m running on ubuntu? And my final question is there a way to scan my pc for these viruses on ubuntu?

Greetings 

Jorrit

---

### Post by cdenley on 2009-06-24
Windows malware cannot run on Linux, unless you run it in wine. Even then, I doubt a keylogger would work. It is highly unlikely that windows malware would check for and modify a linux filesystem. Virus scanners would only check for Windows viruses since there are no known Linux viruses which can infect a recent release.

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by HavocXphere on 2009-06-24
> **Jorrittjarks said:**
> So i deleted and formated my windows partition, now my question is could the virus have transferd to my other partitionst
It could have jumped to NTFS or FAT32 partitions...but not the ubuntu one.

ps Make sure your flash sticks are clean too.

---

### Post by Jorrittjarks on 2009-06-24
thnx for the fast replays, helped a great deal.

kisses

---

