---
title: "X-Windows probs with CE 2.0 and ichthux"
date: 2006-12-01
forum: Ubuntu Christian Edition
---

### Post by beta.tester on 2006-12-01
Hi

Replicteable problem here. Install CE 2.0 just fine. It allows me to access other terminals via Alt-F1 etc.

Install Ichthux also and big problems. ie No access to other terminals, screen blanks and reset of hware needed. Also I cannot "logout" session and go in another session ie switching between sessions gnome <=> kde without same problem of blank screen and hware reset needed..

On install I have tried both options of which to use ie gdm and kdm - results are the same - switch and try to open another terminal and zilch.

I remember this happening on earlier ubuntu versions and *may* be related. You had to always choose the windows manager you initially installed or it got confused :)

Hardware: AMD 3200 (64), 2 Gig DDR400, NVidia 5900 ULtra, MSI Platnum mobo, twin 250 gig seagate ide hdd's (not raid).

Any help really appreciated.

Pax et bonum (Peace and all good)   john

---

### Post by mhancoc7 on 2006-12-01
> **beta.tester said:**
> Hi

Replicteable problem here. Install CE 2.0 just fine. It allows me to access other terminals via Alt-F1 etc.

Install Ichthux also and big problems. ie No access to other terminals, screen blanks and reset of hware needed. Also I cannot "logout" session and go in another session ie switching between sessions gnome <=> kde without same problem of blank screen and hware reset needed..

On install I have tried both options of which to use ie gdm and kdm - results are the same - switch and try to open another terminal and zilch.

I remember this happening on earlier ubuntu versions and *may* be related. You had to always choose the windows manager you initially installed or it got confused :)

Hardware: AMD 3200 (64), 2 Gig DDR400, NVidia 5900 ULtra, MSI Platnum mobo, twin 250 gig seagate ide hdd's (not raid).

Any help really appreciated.

Pax et bonum (Peace and all good)   john

Thanks for reporting this. I will definitely be looking into it.

The one thing that I did notice is that you are using and amd64. Currently Ubuntu CE is only being developed for PC (Intel x86). I am not sure if this could be the issue, but it definitely stood out to me.

Thanks, Jereme

---

### Post by Darrious on 2006-12-01
Sorry to intrude here but how do you check your chipset.

---

### Post by beta.tester on 2006-12-02
Hi Jereme


> **mhancoc7 said:**
> Thanks for reporting this. I will definitely be looking into it.

The one thing that I did notice is that you are using and amd64. Currently Ubuntu CE is only being developed for PC (Intel x86). I am not sure if this could be the issue, but it definitely stood out to me.

Thanks, Jereme

Many thanks! I should have also mentioned I have an 18.1" NEC MultiSync LCD 1810 screen. I hear what you say but would point out using "native" ubuntu (from 6.xx onwards) x64 or i386 this problem doesnt appear to happen.

If I can help in anyway resolve please just ask :)

Pax et bonum (Peace and all good)  john

---

### Post by mhancoc7 on 2006-12-02
> **beta.tester said:**
> Hi Jereme




Many thanks! I should have also mentioned I have an 18.1" NEC MultiSync LCD 1810 screen. I hear what you say but would point out using "native" ubuntu (from 6.xx onwards) x64 or i386 this problem doesnt appear to happen.

If I can help in anyway resolve please just ask :)

Pax et bonum (Peace and all good)  john

Thanks John,
Let us know if you figure anything out with it. I do not currently have a amd64 system to test with so your help will be much appreciated.
Thanks, Jereme

---

### Post by beta.tester on 2006-12-09
Hi Jereme

Apologies for delay in getting back to you, I think you have jit it in one. Appears to be related to the different calls in AMD64 - no idea how to fix sorry.

Pax et bonum (Peace and all good)  john

---

