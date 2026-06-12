---
title: "Ubuntu studio 11.04 wireless help"
date: 2011-07-09
forum: Ubuntu Studio
---

### Post by MlDean on 2011-07-09
hi all , i need help getting the wireless Internet driver to work , on the other Linux installs i have did  it just worked right off the bat , kinda scratching my head on this one ? it detected my settings during  the install , 
but no shebang when it was done ?, i love this OS , its great looking , i still haven't figured out how to work all the instruments and plug ins , but i think Ubuntu studio has potential and might just become my primary OS,
i am trying to integrate this in to my home studio for some added versatility..

thanks Keith

---

### Post by jejeman on 2011-07-09
Please, don't tell us what wireless card, and what type of connection you are using.
:KS

---

### Post by MlDean on 2011-07-09
> **jejeman said:**
> Please, don't tell us what wireless card, and what type of connection you are using.
:KS
LOL, well i am using the same card and connection that works with my Ubuntu 11.04 64 bit , a net gear pci card and a gateway broadband router .

---

### Post by cchhrriiss121212 on 2011-07-09
Try this guide:
[https://help.ubuntu.com/community/UbuntuStudioNetworkSetup](https://help.ubuntu.com/community/UbuntuStudioNetworkSetup)

---

### Post by MlDean on 2011-07-11
Thanks ,i have got the wireless working ,
 
Now i have severe latency issues when recording  .. LOL

---

### Post by Supergoo on 2011-07-19
Currently, Ubuntu Studio is shipping the -generic kernel. We are working with the Ubuntu Kernel Team to get a -lowlatency kernel into the archives which will then ship, in addition to the -generic kernel, in Ubuntu Studio. An interim -lowlatency kernel is available in Allesio Bogani's PPA.


This is from the release notes on the Ubuntu Studio page, You might need to go to a older version of Studio if  latency is a problem. Hope this helps.

---

### Post by Bucky Ball on 2011-07-23
You need the -rt (real time) kernel. That should be what Ubuntu Studio is booting. Under 'Real Time support' [HERE]("https://help.ubuntu.com/community/UbuntuStudioPreparation#Real-Time%20Support") (down from the heading a bit) it shows you how to install  the rt kernel for 10.04 at least.

---

### Post by Pablo_F on 2011-07-23
> You need the -rt (real time) kernel. That should be what Ubuntu Studio is booting. 

No, US 11.04 does not offer a rt kernel (The last 2.6 rt patch was applicable to 2.6.33). See Supergoo's quote. 

In any case, when diagnosing "latency issues" there are other things to look into before the kernel.  

Make sure you (the user who runs jackd) have rtprio and memlock privileges and set up jackd with a low latency setting (but not too low as you have to avoid xruns).

---

