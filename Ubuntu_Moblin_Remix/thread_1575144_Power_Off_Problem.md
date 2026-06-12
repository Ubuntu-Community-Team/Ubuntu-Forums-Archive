---
title: "Power Off Problem"
date: 2010-09-15
forum: Ubuntu Moblin Remix
---

### Post by mcuk2010 on 2010-09-15
Hi Folks
 
I have installed the latest Netbook version on my old Toshiba Portege 7020CT Laptop and it is running really well.
 
The only problem I have is that when I'm shutting down the system it does not auto shut down. I have to use the power button to shut it down.
 
Does anyone know why this might be happening.
 
Cheers
mc

---

### Post by tangchengguang on 2010-09-21
You can try to execute the following instructions in the terminal when you shutdown the computer:
[COLOR="Red"]**$sudo init 0**[/COLOR]
That means you change the run level from 3/5 to zero, then the computer will shutdown automatically.

---

