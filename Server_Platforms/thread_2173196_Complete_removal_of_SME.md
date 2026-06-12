---
title: "Complete removal of SME"
date: 2013-09-08
forum: Server Platforms
---

### Post by ChrisRChamberlain on 2013-09-08
Hi all

Followed instructions in this article,[http://www.liberiangeek.net/2011/12/automatically-mount-map-microsoft-skydrive-in-ubuntu-11-10-with-sme-storagepat-ii]("http://www.liberiangeek.net/2011/12/automatically-mount-map-microsoft-skydrive-in-ubuntu-11-10-with-sme-storagepat-ii"), but decided to remove SME which was done using 'purge' etc.

Key commands in article are:-

```
sudo modprobe fuse
```
```
sudo usermod -a -G fuse chris
```
```
sudo gedit /etc/fuse.conf
```

Having since reset /etc/fuse.conf to default, removed SME from Startup Application and rebooted, what now occurs is an error message via email every minute, title being:-

> Cron <chris@econel> DISPLAY=:0; export DISPLAY; LANG=en_GB.UTF-8; export LANG; /usr/bin/smesynccenter --hidden --syncall
Content being:-
> /bin/sh: 1: /usr/bin/smesynccenter: not found

Would appreciate suggestions as to to how to resolve this issue

TIA

---

### Post by ChrisRChamberlain on 2013-09-08
The clue is the word 'cron'

There had been a new line appended to the the current crontab by SME

Removed the line, problem sorted :p

---

