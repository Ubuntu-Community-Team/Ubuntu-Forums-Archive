---
title: "Dell Poweredge 1850"
date: 2011-12-08
forum: Server Platforms
---

### Post by TomMcloughlin on 2011-12-08
Hello,

I have a problem with my Poweredge,
when i boot it up it boots up fine but i am not receiving any signal from the vga. :(
Please could someone help me as i need this server for my company.

Thanks,
Tom Mcloughlin.

---

### Post by TomMcloughlin on 2011-12-08
*bump*

---

### Post by trundlenut on 2011-12-08
Does the machine only have one vga connection or are there ones front and rear?

---

### Post by TomMcloughlin on 2011-12-09
> **trundlenut said:**
> Does the machine only have one vga connection or are there ones front and rear?
It only has vga and i have one on the front and back and tried both

---

### Post by RobFromLafayette on 2011-12-09
> **TomMcloughlin said:**
> It only has vga and i have one on the front and back and tried both

I had a similar problem with my install (Server 11.10 on a dual-xeon PowerEdge 1750) using an LCD monitor.  
In my case, the VGA timings were sending a 75hz refresh rate, and my LCD only goes to 70 (and prefers 60hz)

I found and attached an old CRT, and it works just dandy.

I *think* that you can pass a kernel argument from Grub2 that will force a VGA mode, but I'm still reading up on that.


FWIW, I had the same issue on a Poweredge 2500 box earlier, before I got the 1750.

---

### Post by RobFromLafayette on 2011-12-09
> **RobFromLafayette said:**
> I had a similar problem with my install (Server 11.10 on a dual-xeon PowerEdge 1750) using an LCD monitor.  
In my case, the VGA timings were sending a 75hz refresh rate, and my LCD only goes to 70 (and prefers 60hz)

I found and attached an old CRT, and it works just dandy.

I *think* that you can pass a kernel argument from Grub2 that will force a VGA mode, but I'm still reading up on that.


FWIW, I had the same issue on a Poweredge 2500 box earlier, before I got the 1750.


Followup:  I followed the instructions from here:  [http://askubuntu.com/questions/45071/how-do-i-set-the-refresh-rate-used-by-kms-on-the-foss-ati-driver](http://askubuntu.com/questions/45071/how-do-i-set-the-refresh-rate-used-by-kms-on-the-foss-ati-driver)  
and now I'm all set, displaying an old-LCD-friendly 60Hz console.

---

### Post by TomMcloughlin on 2011-12-10
> **RobFromLafayette said:**
> Followup:  I followed the instructions from here:  [http://askubuntu.com/questions/45071/how-do-i-set-the-refresh-rate-used-by-kms-on-the-foss-ati-driver](http://askubuntu.com/questions/45071/how-do-i-set-the-refresh-rate-used-by-kms-on-the-foss-ati-driver)  
and now I'm all set, displaying an old-LCD-friendly 60Hz console.

Thanks :)
I will let you know if it works.

---

