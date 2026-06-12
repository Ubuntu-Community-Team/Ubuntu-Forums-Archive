---
title: "Ubuntu Server on PowerEdge T440 - Dell PERC H330"
date: 2018-12-11
forum: Server Platforms
---

### Post by flaviove on 2018-12-11
Hi All.

We´ve got a new Dell PowerEdge T440 with a PERC H330 Raid card and 4x900Mb disks on it. I am trying to install Ubuntu Server Version 18.04 on it and I had some problems.
I coundn´t get the full space of 4x900=3.6T. On the screen I´ve got only 1.8T. 
How we can see on the attetched picture the PERC H330 was recognized.
Any help will be great.
Thanx in advance.

Flávio Veras

---

### Post by darkod on 2018-12-11
Did you confirm the drive in the PERC is actually 3.6TB?

In fact, if you are using raid10 then the useful space is exactly 1.8TB from 4x 900GB disks.

First check in the PERC what sort of raid array you have and the virtual disk size. Only then you can know if the OS is seeing it differently or not.

---

### Post by SeijiSensei on 2018-12-11
If you configure them as [RAID5]("https://en.wikipedia.org/wiki/Standard_RAID_levels#RAID_5") you'll have 3 X 900G, or 2.7 T.  The fourth drive is used for "parity."  

In my experience the PERC driver is quite reliable.

---

### Post by flaviove on 2018-12-12
Thank you so much darkod and SeijiSensei. You are right.
In reality I didn´t have check it out on my PERC config. Now its ok. I´ve got the right space, about 2.6T.

---

