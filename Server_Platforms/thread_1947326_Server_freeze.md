---
title: "Server freeze"
date: 2012-03-26
forum: Server Platforms
---

### Post by Empire-Phoenix on 2012-03-26
Hi, I currently try to determine, why my server randomly starts to full freeze after several days.

I currently have absolutly no Idea why this is happening, and hope someone with more knowledge could give me a few tips, what I can do to determine the freeze reason. (remotly, the server is unfortunalty in a computingcenter a few 100km away, butr I have root ssh)

Hardware: 
Intel i5-2500
Gigabyte GA-Z68MA-D2H-B3, Z68 (B3) Sockel 1155 Mainboard
2x120 GB OCZ Agility 3 SSD SATA 6Gb/s in software raid (115gb mirror and 10gb stripe swap)
DDR3RAM 4x 4GB DDR3-1600 (used memcheck for several hours after assembling it, with no errors)

Actually I don't really know where to start, since I never had problems with linux servers before.

What can i try to find out the reason for the freezes?

---

### Post by sffvba[e0rt on 2012-03-27
*Thread moved to **Server Platforms**.*


404

---

### Post by rmil on 2012-03-27
Start with
```
dmesg
```then
```
df -h
```and then
```
cat /var/log/syslog.log
```If server has been working for several years 24h/7/365 and it is not IBM, HP, Dell, etc... then change power supply

---

