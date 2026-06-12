---
title: "nfs share smaller than exported raid"
date: 2011-08-31
forum: Server Platforms
---

### Post by kingster80 on 2011-08-31
heres the deal.

yesterday I build myself a new personal nas/storagemachine.

I've used 5 2tb wd20earx drives (one of wich allready seems to be failing).

The drives are configured as software raid5 using webmin (headless server). Webmin tells me the array has 7.28TB of usable space. So far så good.

I then made an nfs export, mounted it on my laptop and desktop. When I open the folder on either of the two, nautilus tells me that there is only 26.1 GB available. 

What happened, where did I go wrong. please help....:confused:


**[COLOR="Red"]Sorry, it was a typo. accidentally wrote /etc/path.. instead of /mnt/path.. when mounting the raid.[/COLOR]**

---

