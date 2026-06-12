---
title: "AV for Ubuntu File Server"
date: 2009-03-25
forum: Server Platforms
---

### Post by damo12 on 2009-03-25
I run an Ubuntu 8.04 file server for a company who's computers run on both Windows XP home and Mac OS X.

Although each machine runs it's own AV program (AVG Network Edition) the owner of the business has asked for the file server to runa suitable AV program.

I access the server through Webmin and am not overly confident with the command line.  I would be grateful if anyone can give me advice on this problem.

Thanks in advance

---

### Post by BkkBonanza on 2009-03-25
AV for Linux? I think I've heard of that but most people chuckle when it's mentioned.:)
But seriously, do a search here for anti-virus and you'll find that many people say there's none to worry about. I wouldn't guarantee that to be true but if even close to true then just what is the AV scanning for... if none are known to exist?

---

### Post by smeerbartje on 2009-03-25
Did you check the non-resident scanner [clamAV]("https://help.ubuntu.com/community/ClamAV")?

---

### Post by MrWES on 2009-03-25
I have the same setup; Linux and Windows machines accessing my file server, so I installed ClamAV and run a freshclam and clamscan once a week via cron.

Bill

---

### Post by smeerbartje on 2009-03-25
How did you add the weekly update in the cron? Can you give me the rule?

---

### Post by MrWES on 2009-03-25
> **smeerbartje said:**
> How did you add the weekly update in the cron? Can you give me the rule?

First, if you want to change your default editor from vi to nano, follow the instructions I posted in this thread, post #3

[http://ubuntuforums.org/showthread.php?p=6949251#post6949251]("http://ubuntuforums.org/showthread.php?p=6949251#post6949251")

Now edit the root cron with:

```
sudo crontab -e
```

I run my update and scan weekly on Sunday mornings at 12:30am and 12:35am respectively.

```
30 0 * * 0 freshclam
35 0 * * 0 clamscan -r /media/samba

```

UPDATE 3/27: Actually there is no reason to run freshclam in your cron; freshclam runs as a daemon and checks for updates every hour.

Change the path of the clamscan to match your needs. You should get an email when the cron job is completed. Make sure you have /etc/aliases set to root:YOURUSERNAMEHERE

Bill

---

### Post by smeerbartje on 2009-03-25
Thank you very much! I managed to follow your guides...

---

### Post by MrWES on 2009-03-25
> **smeerbartje said:**
> Thank you very much! I managed to follow your guides...

Your welcome.

Good Luck,
Bill

---

### Post by mrsteveman1 on 2009-03-26
A Linux machine can still host and distribute viruses for Windows, and a piece of malware can spread through a network like that quite easily, so its a good idea to keep the server from hosting malware and allowing clients to become infected.

There is malware written for Linux too, but it doesn't have an easy time spreading itself around like it does on Windows.

---

### Post by damo12 on 2009-03-26
Thanks for all of the advice, I'll give Clam a try.

---

### Post by windependence on 2009-03-26
Ummm.....AVG has several versions for Linux including a free one. The network edition also works on Linux.

[http://www.avg.com/business-security-comparison](http://www.avg.com/business-security-comparison)

-Tim

AVG Partner

---

