---
title: "Server 12.04.1 - Would HDD SMART status report in the event of a failure?"
date: 2013-01-19
forum: Server Platforms
---

### Post by Roasted on 2013-01-19
I have a 12.04.1 box running with Ubuntu Server. It's running an array of various services. It also may be running a RAID array in the somewhat near future if I can get some money together to make happen. I'm curious... when I SSH in I see quite a bit of statistical info listed there on the main screen. If you have a hard drive that is failing or has already failed, would anything be reported there? Or should I invest time into some sort of hard drive watcher application that'll notify me (somehow) that a drive replacement is necessary?

I've had Ubuntu desktop edition notify me of failing hard drives before, which makes me wonder if the server variant would do the same.

Thanks!

---

### Post by tgalati4 on 2013-01-19
```
sudo apt-get install smartmontools
```

Configure with your user account to receive emails when errors are found.  I believe root account may be default email receiver, but you can check in /etc/smartmontools.  Set up a schedule to run long tests on your drives once or twice a year.  Modern drives will store the test resuls in firmware/eeprom so you can review error counts vs power-on hours.

I've got one server drive that has been running a while:

 9 Power_On_Hours          0x0032   248   248   000    Old_age   Always       -       118529

That's 13.5 years!  24/7 Dapper Drake server, I'm afraid to shut it off.

---

