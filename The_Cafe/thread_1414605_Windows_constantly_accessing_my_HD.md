---
title: "Windows constantly accessing my HD"
date: 2010-02-23
forum: The Cafe
---

### Post by blueshiftoverwatch on 2010-02-23
I've noticed that Windows XP is constantly accessing my HD. It doesn't matter whether I'm duel booted into it or it's running on a VM. About once every second I'll either see the HD light on my case flashing or in the case of a VM, the HD access indicator on Virtualbox flashing. Which accesses my real hard drive once every several virtual accesses.

I can fall asleep booted up under Windows and when I get up in the morning it's still accessing my HD for a split second about once every second. If left alone it would probably continue to do this until the sun expanded and engulfed the Earth. Assuming my computer didn't die before then.

I know it's not malware because it does it even after a fresh install when the first thing I'll do is install Zonealarm (firewall) and AVG (anti-virus).

Ubuntu will occasionally access my HD for no apparent reason. But it's much less frequent.

---

### Post by thatguruguy on 2010-02-23
Maybe it's this:

[http://www.pcguide.com/ts/x/comp/hdd/winAccess-c.html](http://www.pcguide.com/ts/x/comp/hdd/winAccess-c.html)

---

### Post by Kai69 on 2010-02-23
Look under processes in XP loads are running just to keep the os ticking over Then look at ubuntus most are sleeping..that is why the HDD light flashes so much in XP.

---

### Post by litemirrors on 2010-02-23
Very interesting, isn't this more of a hardware category or something? I can only extend condolences since it really could be anything :(

---

### Post by oldsoundguy on 2010-02-23
first off, AVG and Zone Alarm alone will not protect your computer completely .. you need an anti-malware/anti-spyware program such as Spyware Blaster or Spybot Search & Destroy with the "immunize" ACTIVATED.

Also, programs within Windows such as Media Player phone home at regular intervals.  AND anything you have installed such as a web cam also will check for updates.

---

### Post by dmizer on 2010-02-23
> **oldsoundguy said:**
> first off, AVG and Zone Alarm alone will not protect your computer completely .. you need an anti-malware/anti-spyware program such as Spyware Blaster or Spybot Search & Destroy with the "immunize" ACTIVATED.

Not necessarily: [http://www.psychocats.net/ubuntucat/windowssecurity/](http://www.psychocats.net/ubuntucat/windowssecurity/)

---

### Post by Sporkman on 2010-02-23
That's one thing I always notice when using Windows vs. Linux - the HD is constantly grinding away in Windows.

---

### Post by doas777 on 2010-02-23
try using process explorer from sysinternals. add a collum for process IO, for both read and write bytes, and see which process keeps moving upward. may be an AV system.

---

### Post by NightwishFan on 2010-02-23
Windows Xp likes to use virtual memory a lot, Linux prefers to use RAM. Linux used to wake up the disk constantly. Doing that was bad for power management. However, I do not think it does that any more.

---

### Post by orethrius on 2010-02-23
My three best guesses, in order of probability based on your system specs (if your sig is accurate):

1.  Content indexing service.  This is relatively straightforward to pause via right-clicking the "magnifying glass" tray icon, or to disable via services.msc.  Ask around before attempting the latter, as a good deal of critical system processes are started from that snap-in.
2.  Overzealous antivirus / antimalware suite.  Follow the article posted up by dmizer, then drop the scan interval to once or twice a week.
3.  Low physical memory resulting in swapfile usage.  Add more memory and/or manually adjust the swapfile size from the "Advanced" > "Performance" tab in System Properties (Control Panel or right-click "My Computer").

If none of these seems to be the issue, please post back.

---

### Post by NightwishFan on 2010-02-23
Also, on the SWAP issue: You should set your page file on Windows to be a specific size, such as 1800min and 1800max, so it is not dynamically allocated.

---

### Post by blueshiftoverwatch on 2010-02-23
Thanks for all the suggestions so far everyone.
> **orethrius said:**
> 1. Content indexing service.  This is relatively straightforward to pause via right-clicking the "magnifying glass" tray icon, or to disable via services.msc.  Ask around before attempting the latter, as a good deal of critical system processes are started from that snap-in.
I don't think that'll work. Because when I do that I loaded up Process Explorer and theirs still a process called "searchprotocolhost.exe" running and it'll come back from the dead even after I kill it.
> **orethrius said:**
> 2.  Overzealous antivirus / antimalware suite.  Follow the article posted up by dmizer, then drop the scan interval to once or twice a week.
It was already several hours past what the scan time was. But out of curiosity I tried to uninstall AVG. It wouldn't let me uninstall it because the process kept freezing up during the uninstall phase. But it did disable it from running while trying to uninstall it. And it's still accessing the HD as much as ever before with it not running.
> **orethrius said:**
> 3.  Low physical memory resulting in swapfile usage.  Add more memory and/or manually adjust the swapfile size from the "Advanced" > "Performance" tab in System Properties (Control Panel or right-click "My Computer").
That might be the case on my VM, even though I assiged it 1GB of dedicated RAM. But the same thing happens on my 32 bit duel boot install as well.
> **doas777 said:**
> try using process explorer from sysinternals. add a collum for process IO, for both read and write bytes, and see which process keeps moving upward. may be an AV system.
It looks like an app called "searchprotocol.exe" is what's doing this. I'll have to look more into it later. But for right now I think I'm off to bed.
> **NightwishFan said:**
> Also, on the SWAP issue: You should set your page file on Windows to be a specific size, such as 1800min and 1800max, so it is not dynamically allocated.
That's already one of the first things I do when installing Windows.

---

### Post by brons2 on 2010-02-23
Use Nlite to build a custom windows XP install, and disable the swap file altogether.  You have 8GB of RAM, you don't need a swap file.

Alternately, set up a RAMdrive and put your swapfile there.

---

### Post by blueshiftoverwatch on 2010-02-24
> **brons2 said:**
> Use Nlite to build a custom windows XP install, and disable the swap file altogether.  You have 8GB of RAM, you don't need a swap file.
Being a 32 bit OS, XP only recognizes 4GB of RAM. So I have a 4GB pagefile setup. I might go ahead and install 64 bit XP over it though because I found the driver page for my networking card.

---

### Post by juancarlospaco on 2010-02-24
*Seems normal, just the common Virus scanning HD for your passwords...*

---

### Post by doas777 on 2010-02-24
searchprotocol.exe is the indexer process for Windows Desktop Search, a particularly pernicious piece of crap that i have to fight at work, because some admin with a workhorse box says it doesn't adversely impact users. i will state unequivicaly that it does.

just uninstall the desktop search (most user do not install it intentionally), and all shoudl be well. it may be required for search in outlook 07 on xp though, so if that is a feature you require, then you may have to live with it.

gl and hf

---

### Post by blueshiftoverwatch on 2010-02-24
I uninstalled the search app, but it seems that now Zonealarm is what's constantly writing to my HD. So I guess I'll just have to live with it. It's not a big deal and probably won't impact the life of my HD's that much. I was just curious as to why it was happening.

---

### Post by jdong on 2010-02-24
In addition to misbehaving applications causing repetitive disk access, Windows has a background automatic defragmentation/optimization service that adapts the disk layout to the user's file access patterns.

In Window Vista and Windows 7, the SuperFetch feature was also introduced which uses an artificially intelligent machine learning algorithm to pre-fetch disk contents into unused RAM proactively.

These two features can generate disk traffic in the background. It's generally true of any modern operating system that there may be random disk access even when "not using" the computer, so my best suggestion is to either move the computer somewhere where it wouldn't bother you during the night, invest in quieter hard drives, or put the computer to standby or shutdown when not using it.

---

### Post by blueshiftoverwatch on 2010-02-24
> **jdong said:**
> In addition to misbehaving applications causing repetitive disk access, Windows has a background automatic defragmentation/optimization service that adapts the disk layout to the user's file access patterns.

In Window Vista and Windows 7, the SuperFetch feature was also introduced which uses an artificially intelligent machine learning algorithm to pre-fetch disk contents into unused RAM proactively.
I can understand pre-fetching information. But I can't understand why it would continue to pre-fetch information for 10 or more hours after I haven't even touched the computer. Theirs only so much you can pre-fetch.

I don't know if Vista or 7 do this or not, I think it might though. I have 7 installed, but only because I was able to obtain a free legal copy. It just sits there unused 99.9% of the time. I'm just talking about XP.

Also, I thought that only Unix-like OS's defragged hard drives. Which is the reason why the overwhelming majority of Linux users don't' even have defragging software installed. In fact, I'm not even sure if ext3 or ext4 even have defragging software.

---

