---
title: "Ubuntu 14.04 + webmin   -- diskspace usage ???"
date: 2015-06-18
forum: Server Platforms
---

### Post by rhandy2 on 2015-06-18
HELLO

IN WEBMIN I HAVE : 145.61 GB total / 134.24 GB free / 11.37 GB used


BUT IS STRANGE IF I USE  DF -h 

> 
/dev/sda1       146G  4,0G  135G   3% /


Used 4Gb, not 11.37Gb.

---

### Post by rhandy2 on 2015-06-18
Drive have 160Gb

Dev/sda1 Have 146Gb

Used 4,0Gb

Free only 135Gb???? I don´t understand diference? should have free 142Gb

---

### Post by darkod on 2015-06-18
This might be a result of ext4 reserving around 5% when formatting. But I don't remember now if they are included in the Used space or not.
If they are not, your 4G used plus those 5% is about right for 135G free.

---

