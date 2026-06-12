---
title: "Ubuntu 12.04 Software Raid1"
date: 2012-07-11
forum: Server Platforms
---

### Post by go4unkwn on 2012-07-11
Hello Experts

I set up an Ubuntu 12.04 Server using the option of a software raid1.
Now I realised that the harddisk /dev/sda1 is always working under full load (the led of the harddisk is always illuminated.

Is this normal for an software raid1 or is there something wrong with the harddisk (or the software raid1).

I ask because the harddisk temperature goes up to 60°C. The working range of the Western Digital harddisk lies between 40°C and 60°C (WD Specifications).

S.M.A.R.T means the harddisk is ok.

Any hints are welcome!

Kind regards, go4unkwn.

---

### Post by rubylaser on 2012-07-11
I would take a look at iotop and iostat to see what is accessing your hard disk.  iotop's output looks like this.

```
Total DISK READ:       0.00 B/s | Total DISK WRITE:       0.00 B/s
  TID  PRIO  USER     DISK READ  DISK WRITE  SWAPIN     IO>    COMMAND                                       
  235 be/3 root          0.00 B     32.00 K  0.00 %  0.00 % [jbd2/sda1-8]
 8013 be/4 root          0.00 B      0.00 B  0.00 %  0.00 % [md0_raid6]
 8054 be/3 root          0.00 B      0.00 B  0.00 %  0.00 % [jbd2/md0-8]
```

---

### Post by go4unkwn on 2012-07-25
hello rubylaser

THANK's a lot for your help. I will follow your hint!

(sorry, i never said thank you for your help til now.
but a fine excuse is: i had a lot to do with a web server project. ;))

kind regards, go4unkwn

---

