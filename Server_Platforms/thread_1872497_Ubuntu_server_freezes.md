---
title: "Ubuntu server freezes"
date: 2011-10-30
forum: Server Platforms
---

### Post by imsan on 2011-10-30
Hi guys,

I have an 5 year old ubuntu server thats been running fine till last fortnight. One day it suddenly start freezing after couple of hours. I found the issue and installed a new Graphics card.

It started working fine until i removed the connected monitor for one day and it froze again. I connect same monitor to it and it crashed after 4 days. There are no logs , i don;t know what to do . 

please help 

distro :

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=6.06
DISTRIB_CODENAME=dapper
DISTRIB_DESCRIPTION="Ubuntu 6.06.2 LTS"

---

### Post by knight187 on 2011-10-31
Clone the server to new / temp hardware (even a virtual if its available) then start testing and replacing the hardware. If I had to guess it will be faulty memory. The Ubuntu disks come with a MEMTEST application you can launch from the boot menu.

Good luck, keep us posted with your progress.

Cheers,

---

### Post by imsan on 2011-10-31
> **knight187 said:**
> Clone the server to new / temp hardware (even a virtual if its available) then start testing and replacing the hardware. If I had to guess it will be faulty memory. The Ubuntu disks come with a MEMTEST application you can launch from the boot menu.

Good luck, keep us posted with your progress.

Cheers,


I was thinking to clone the server but its in a production environment... any good software that can do the job without bringing server down?

Thanks for your feedback

---

