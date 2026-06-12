---
title: "2am download every night?"
date: 2018-11-07
forum: Server Platforms
---

### Post by b3nst3r on 2018-11-07
Hi I'm running  Ubuntu 18.04.1 LTS server, with various things such as TS3, Rtorrent,Plex, and quake 3.  I have VNstat php installed so I can look a the bandwith usage daily, and compare to my provider to make sure I don't exceed a 1TB cap (this has happened once already).  When viewing the hourly logs of VNstat, I noticed that every single night there is a dowload between 200 and 500 Megs.  It's a relatively small amount, but there is no explanation on why I would be receiving data exactly at this time every night.  Outgoing is virtually zero most days, even with rtorrent.  

How would I determine who/what is downloading this data?  Does Ubuntu go out and check for updates once a day?

---

### Post by Frogs Hair on 2018-11-07
Moved to *Server Platforms*.

---

### Post by #&amp;thj^% on 2018-11-07
If this "unattended-upgrades" is installed then yes.
More info found here: [https://libre-software.net/ubuntu-automatic-updates/](https://libre-software.net/ubuntu-automatic-updates/)
I think the program Nethogs perfectly suits your requirements for seeing what and who is downloading.
Also more here: [https://askubuntu.com/questions/706928/how-to-tell-which-processes-are-uploading-and-downloading-data-and-how-much](https://askubuntu.com/questions/706928/how-to-tell-which-processes-are-uploading-and-downloading-data-and-how-much)

Others here may have other suggestions.

---

### Post by b3nst3r on 2018-11-07
I looked at /etc/apt/apt.conf.d/20auto-upgrades and saw this below:

```
APT::Periodic::Update-Package-Lists "1";APT::Periodic::Unattended-Upgrade "1";
```

So then that would explain the small amount of incoming data I see every night.  I've been playing with nethogs while doing some streaming.  definitely helps, but there's no way I'd be at the computer at 2am to see who is downloading at that moment.  :)  Still, good info.  

Thanks for the help.

---

### Post by TheFu on 2018-11-08
You can setup a cron job to capture the data at 2am. Automation is a wonderful thing on computers.  It is a key reason that I  prefer Unix systems over other alternatives.  I have computers doing things all the time for my convenience later.

---

