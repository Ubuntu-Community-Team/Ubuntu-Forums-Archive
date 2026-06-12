---
title: "NTP not working"
date: 2013-06-22
forum: Server Platforms
---

### Post by nerdtron on 2013-06-22
Does anyone here running NTP on their local network?
I would like to do this scenario:

A: 3-computers on a private LAN, one of them would be the master clock and the 2 would sync their time from server 1.

B: 3-computers on a private LAN, one would connect to the internet to sync time, the other 2 would sync their time from server 1.

It would be better if it were scenario A.
I tried experimenting for both situations and I can't seem to sync the time of the 3 computers. They are out of sync on every reboot with different varying time like 1.832 secs or 0.758 secs etc. And i don't think they are trying to sync on the background because the "skew time" between doesn't change for about and hour or so.
I need to have their times in sync to approx. <.05 secs because I use them for ceph nodes.

Do you have any ntp.conf files on your servers and clients? Can you suggest to me what should be done to correct this issue?

Thanks in advance.

---

### Post by 2F4U on 2013-06-23
You can easily verify whether the machines have contact to a ntp server by issuing the command

```
ntpq -p
```

in a terminal. It should show you the ntp server along with some other information such as the offset. However, if the local time difference between the client and the ntp server is too big, it won't sync. Then it could be a good idea to go into the BIOS of each machine and manually set the time to the correct value.

---

### Post by newbie-user on 2013-06-23
Check your broadcast address and allowed subnets in your ntp.conf.

---

### Post by nerdtron on 2013-06-23
> **2F4U said:**
> You can easily verify whether the machines have contact to a ntp server by issuing the command

```
ntpq -p
```

in a terminal. It should show you the ntp server along with some other information such as the offset. However, if the local time difference between the client and the ntp server is too big, it won't sync. Then it could be a good idea to go into the BIOS of each machine and manually set the time to the correct value.

Yes, ntpq -p shows that the clients (10.1.0.12 and 10.1.0.13) peering with the server (10.1.0.11) but they can't seem to get a correct value. If normally like between node2 or node 3 is advance by about 1 secs to .5 secs. It really bugs me, ntp doesn't update much and sync is not as accurate as I thought it would be.

---

### Post by SeijiSensei on 2013-06-23
First, make sure your clients sync their hardware clocks at reboot.  I believe Ubuntu does this by default nowadays, but you might also want to add a cron job that runs periodically with the command

```
hwclock --systohc
```

If you don't sync the master to an Internet time server, you are at the mercy of that computer's local hardware clock, which on most PCs is rather suspect. The NTP daemon supports the use of [alternative local clocks]("http://doc.ntp.org/4.1.1/extern.htm") as well like a GPS device.  High-quality clocks [cost money]("http://www.timetools.co.uk/index.htm").

I'm pretty sure you can get quite accurate syncs with NTP.  You probably need to read the [documentation]("http://www.ntp.org/documentation.html") more closely.  Here's a [discussion of accuracy]("http://www.ntp.org/ntpfaq/NTP-s-sw-clocks-quality.htm").

---

### Post by Leonardo_Chacon on 2014-01-28
This may help you.
[http://ubuntuforums.org/showthread.php?t=862620](http://ubuntuforums.org/showthread.php?t=862620)
[http://ubuntuforums.org/showthread.php?t=579418](http://ubuntuforums.org/showthread.php?t=579418)

---

