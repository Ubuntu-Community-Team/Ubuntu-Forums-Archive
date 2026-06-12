---
title: "Samba PDC problems"
date: 2007-02-13
forum: Server Platforms
---

### Post by mihaisofti on 2007-02-13
I am running ubuntu 606 as a PDC with an XPpro box as client.  I was able to log in to the PDC as 'root' and 'michael' when I first set this up, but not as 'administrator'.  I added user 'administrator' to the pdc and then used smbpasswd to make it a samba user from the xpbox.  I had already done the same with 'root' and 'michael'.  
My problems are twofold:  I can no longer log in as 'root' or 'michael' to the PDC, but I can login with 'administrator' and despite the fact that 'administrator' has full rights on the xpbox, I cannot change the network settings on the xpbox whilst logged in to the PDC as 'administrator'
Can anyone suggest what might be wrong?

mihaisofti

---

### Post by mihaisofti on 2007-02-16
I have now solved the first of these problems.  It was to do with a file called smbusers which contained the line
'administrator=root'
I deleted the file and can now log on as any of the defined users.

However, I am still unable to change the network settings whilst logged on to the PDC, despite the fact that each user has admin equivalence.  

Is this normal, and how can I override the locked network settings?

I would be very glad of any help or pointers anyone can give me.

tia

bungaymike

---

