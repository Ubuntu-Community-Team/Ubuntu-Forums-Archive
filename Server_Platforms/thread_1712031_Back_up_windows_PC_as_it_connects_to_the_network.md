---
title: "Back up windows PC as it connects to the network"
date: 2011-03-22
forum: Server Platforms
---

### Post by teocomi on 2011-03-22
Hello I have a little home server with Ubuntu 10.10, actually it is already backing up my web hosting daily via a cron.daily script..
But I would like to do the same with my Windows laptop, which would it be the best way to do so?

I thought about this, please tell me if it's a good idea: 
since the Ubuntu pc is (almost) always turned on it would be no profit to have it mount the Win PC at startup, indeed I could have a cron.hourly script to check if the Laptop is connected to the network and to back it up once a day, thus by checking a small text file with written the date of the last backup (so that it does not back it up every hour!)

BTW how do I check if the Win PC is connected to the network? How do I mount it via samba? Do you suggest to backup stuff simply moving files, via tar (as I already do with my web host) or with rsync?

Thanks guyzz!

---

### Post by falko on 2011-03-22
Maybe BackupPC is for you: [http://backuppc.sourceforge.net/info.html](http://backuppc.sourceforge.net/info.html)

---

### Post by teocomi on 2011-03-24
Great, right what I could not find myself! ;) I took a while to configure but now it seems to be working great!

Thanks!

---

