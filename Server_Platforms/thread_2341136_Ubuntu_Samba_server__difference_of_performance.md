---
title: "Ubuntu Samba server : difference of performance"
date: 2016-10-25
forum: Server Platforms
---

### Post by cosimos on 2016-10-25
Hello,

I installed an ubuntu samba server (16.04 LTS, fully updated) in my small company to replace my old mac mini samba server. I got everything working, but I have performances issues. I have a diversified environment : 2 desktops using Mac OS, 4 desktops using Windows 10 and now 1 ubuntu samba server. Everything running on wired connection.

Transfer form Windows 10 desktop to Ubuntu Samba Server : ~ 9.5 mo/sec
Transfer from Windows 10 desktop to Old Mac Samba Server : ~ 10.5 mo / sec

An about 10% performance difference is huge. Can anyone gives me some ideas about where I should look into to investigate this problem ? As the hardware, dedicated ethernet card, etc., is more powerful and recent on the Ubuntu server, I expected it to be the opposite.

---

### Post by slickymaster on 2016-10-25
*Thread moved to **Server Platforms**.*

---

### Post by SeijiSensei on 2016-10-25
First thing I'd look at is the speed of the hard drives. Is one a 5400 rpm drive and the other a 7200? Does one have a hardware cache? What are the drives throughput rates?

One thing you can do to improve read performance is to buy a second drive and use RAID1. In this configuration both drives can be read simultaneously thus speeding up transfers.

---

### Post by cosimos on 2016-10-25
Thanks Seiji. But the Ubuntu server has a dedicated SSD hard disk for file sharing, while the old mac mini only had a 7200 RPM hard disk.

SSD of course has higher performance and is correctly configured. I believe this problem to be network-configuration (of samba ? of ubuntu ?) related, but I have no idea what to look at

---

### Post by SeijiSensei on 2016-10-26
Are both servers connected via Ethernet and not wifi?  

What network cards do they have?  Use "sudo lshw" to see their details.

Are the two machines running different versions of Samba?

---

### Post by cosimos on 2016-10-26
Both servers are connected via ethernet, same type of cable.

Mac mini is using a Broadcom BCM57765 Gigabit Ethernet card (built-in on late 2012 model).

Ubuntu server is using a TP-Link TG-3468 PCI Express Gigabit Ethernet.

Both are configured on 100Mb/s full duplex (100baseT/Full) auto-negotiated.

Of course the Mac Mini is running the Server version of Mac OS pushed in by Apple. While Ubuntu is running the latest Samba version in 16.04 LTS repositories (so as of today version 4.3.11  : 2:4.3.11+dfsg-0ubuntu0.16.04.1). The latest stable version of Samba is 4.5.1 but hasn't been pushed in 16.04.1 repo

---

### Post by kpatz on 2016-10-26
Why are they using 100baseT?  Do you not have a gigabit switch?

It would be interesting to compare the performance on a gigabit switch.

---

### Post by cosimos on 2016-10-28
The server <---> gigabit switch is 1G connection. However all desktops run on 100baseT because I could never get the link to work using 1G. If I configure their ethernet cards on 1G, it won't connect (unplugged cable !). But it's not the cable (cat 5e) because it's the same cable for the server.

Anyway I still couldn't find the reason of the 10% performance loss.

---

