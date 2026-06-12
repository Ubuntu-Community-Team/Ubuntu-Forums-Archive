---
title: "How to Monitor cpu, disk usage and more with Open NMS???"
date: 2013-04-23
forum: Server Platforms
---

### Post by Digitallysick on 2013-04-23
So i have open NMS installed, i have ubuntu running in another VM, I want to be able to monitor the cpu, disk usage/space, temp and more 

Open NMS isn't picking up this data automatic,  what do i need to do in baby steps to make this work as simple as possible?

---

### Post by beboylips on 2013-04-23
Quick and dirty would be to run cron jobs with the respectful commands that monitor the data you need and output the raw data on some accessible location.

*ps aux *for cpu/memory
*sensors* for temp
*fdisk -l* for disk usage (I think)

```

!#/bin/bash
ps aux > /var/www/cpumem.txt
fdisk -l > /var/www/disk.txt
sensors > /var/www/temp.txt

```

and run this script every minute or something. 

Beboy

---

