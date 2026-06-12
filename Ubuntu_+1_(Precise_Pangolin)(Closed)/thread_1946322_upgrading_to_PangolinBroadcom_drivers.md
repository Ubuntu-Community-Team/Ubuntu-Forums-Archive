---
title: "upgrading to Pangolin/Broadcom drivers"
date: 2012-03-24
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Inisfad on 2012-03-24
I am currently on Lucid Lynx, and initially had a difficult time setting up my Broadcom card with it, when I first got my wifi connection.  I currently have the STA and B43 drivers installed, and my wifi is now working great.  When I upgrade, I will not have an alternative internet connection. Will the upgrade keep the STA and B43 drivers that are currently installed in Lucid, or will I have to download them previously and manually install them? If I do have to manually install them, can anyone advise how I can get them on to a USB stick or similar?  Thanks!

---

### Post by PhantomTurtle on 2012-03-24
I think you can install them through the Additional Drivers utility(that's what I did on my laptop). If the the drivers were made specifically for 10.04 then it might not work after the upgrade. Additionally there's no guarantee that there will work anyway because 12.04 is still in beta.

---

### Post by ksa618 on 2012-03-24
You could try a 12.04 live session and see if your wireless works before upgrading?

---

### Post by wildmanne39 on 2012-03-24
Hi, it uses the b43 you will need to already have them because you will need to reinstall them.

What does this tell us:
```
lspci -nnk | grep -iA2 net
```
thanks

---

### Post by nothingspecial on 2012-03-24
*Thread moved to **Ubuntu +1 (Precise Pangolin)**.*

---

