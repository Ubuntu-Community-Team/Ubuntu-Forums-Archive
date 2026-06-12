---
title: "Apt-Mirror with several versions of Ubuntu"
date: 2012-03-06
forum: Server Platforms
---

### Post by jesushero on 2012-03-06
I have been hosting an apt-mirror on a LAN with no internet access for a while now. I now want to discontinue support for 8.04 updates, but I would like to keep the files there for the few stubborn people in the LAN who choose to still use 8.04, in case they want to apt-get some 8.04 software. I still have plenty of disk space to do that.

Apt-Mirror was getting its sources from a laptop that would physically travel to an internet access point a few times every month. As disk space on the laptop is limited (compared to the server), I can no longer keep files or sources for 8.04 on it.

The laptop has apt-mirror on it as well, and mirrors from the internet. Then it serves its mirror through Apache to the LAN mirror. Then it goes offline and the LAN mirror serves the entire LAN.

So I want the LAN mirror server to keep all the existing files for 8.04, but to not try to seek new updates from the laptop. So I want to remove 8.04 sources from the mirror.list files, both on the LAN server and on the laptop. On the laptop, I have already removed the 8.04 mirror entirely, and I'm only hosting 10.04. 

I want the LAN server to receive updates for 10.04 every time apt-mirror is run, with the laptop connected to the LAN. I want the LAN server to never ask for 8.04 updates again, but I want it to keep on serving its existing 8.04 mirror.

How do I do that?

Do I just remove the 8.04 entries, as well as the clean entries, from the LAN server's mirror.list? Or will the next time I run clean.sh remove all the 8.04 files from the mirror?

Thanks in advance!

---

