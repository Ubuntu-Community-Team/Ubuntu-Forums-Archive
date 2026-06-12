---
title: "Ubuntu 8.10 on Acer 5515 laptop"
date: 2009-05-13
forum: The Cafe
---

### Post by richg on 2009-05-13
I have a chance to pick up a new Acer 5515 laptop for $400 which is 64 bit. I have never dealt with 64 bit Ubuntu software and I do not know if there might be hidden issues. Any idea if 8.10 will run on this machine? I have run 8.04 on a desktop. My stepson bought an Acer 5515 and told me it runs very well. He is a former programmer so has no problems with it. Problem is it is Vista but I know Ubuntu can take care of that. I do not have any need for Vista. Thanks.

Rich

I might have found some issues/answers in a search. I will try to go to my stepson's and try a live CD. It seems the wireless might be an issue though.

---

### Post by gymophett on 2009-05-13
But 9.04 on it. It will recognize everything on the Acer. You can always put 32bit Ubuntu on a 64bit computer, because some software isn't compatible with 64bit. Ubuntu runs excellent on an Acer usually. My sister's and mine worked out of the box.

---

### Post by drawkcab on 2009-05-14
Seems like a decent deal.

Yeah, I'd install 9.04 which is going to have better hardware recognition.

---

### Post by MARAUDER2003 on 2009-07-08
Hi, I tried to run 9.04 in the acer 5515 but the live cd does not run, it gets stuck when you try to run it or install it. So, the rick to run it or do the install is to modify the boot parameters and add xdriver=vesa. I don't know what driver it loads during live cd but vesa allowed me to install it and live run it. You won't have 3d acceleration with this driver. The new xserver included with 9.04 keeps locking up with ati drivers. Some have successfully downgraded the xserver while using 9.04.

---

