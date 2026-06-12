---
title: "Virtualbox 2.1.0 with Windows XP laggy slow"
date: 2009-02-02
forum: Virtualisation
---

### Post by tuncay on 2009-02-02
Hello,

iam new here:KS

I have a big problem. My virtualbox is really slow... I have read a ton of forums articles on the internet but i cant solve the problem.

What could be the reason that my virtualbox with Windows XP ( without Service Pack ) is so slow?

My System:

AMD x2 Dualcore 2x 2ghz
3 GB Ram DDR II
GeForce 8600 GT 256 MB RAM
250 GB S-ATA 

I have installed the guest additions

Could the NTFS Format the reason ? Or something with my partitions which slows down the system ?! 

I would be very happy if anybody can help me...

Please post anything that can help me....

thank you very much

---

### Post by Therion on 2009-02-02
How much RAM did you allot the VM when you created it?

---

### Post by tuncay on 2009-02-02
i think 512 MB

then i tried it with 1 GB Ram but i dont see any changes

and if i go to system at the windows xp then it shows me the processor AMD X2 4000+ but with only 999 MHZ oder 1 GHZ

---

### Post by tighem on 2009-02-02
Upgrade to 2.1.2 and if you can, turn on nested paging support under the advanced settings.

---

### Post by tuncay on 2009-02-03
soooo

now i know where the problem comes from...

if i start a pogramm which connects to the PostgreSQL Server ( the server is installed on ubuntu )

the guest (Windows XP running on virtualbox) is starting to lag...

thats the problem!

should i install the postgreSQL server on windows at the virtualbox ? Could this solve the problem?

---

### Post by THE-DUKE on 2009-02-03
I'm having the same problem with Virtualbox 2.1.2installed on Ubuntu 8.10. I had problems right from the installation of windows xp home, and I had given it 512MB of RAM. I'm kinda stuck as a result. The XP installation reports that I do not have sufficient memory allocated to graphics, so I assume the VIrtualBox Guest Additions is not working as it should? What do you reckon?

---

### Post by tuncay on 2009-02-05
help pls :(

---

