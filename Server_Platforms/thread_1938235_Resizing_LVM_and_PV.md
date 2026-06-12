---
title: "Resizing LVM and PV"
date: 2012-03-09
forum: Server Platforms
---

### Post by zbuddy99 on 2012-03-09
All,

This has been somewhat frustrating. I have tried a couple of time to do this. I went out and bought a nice Western Digital Black 2TB for my linux server. I used the newest Clonezilla, and copied over my 500gb HD. I told it to make it proportinate and use all of the space. When I look at GPARTED it appear to have worked (at first glance). Yet when you look over to the Used and UnUsed sections - it is not reading. The system still thinks it has 500gb. Any suggestions? See attached.

---

### Post by zbuddy99 on 2012-03-09
More information. I went in and ran pvdisplay and saw that it read 500gb. So I told it to do a resize of +5G. It then brought it online to 1.83TB. Then I ran lvresize and added 1000G. Now it shows it in the terminal at 1.43TB, but it appears it is not available to me still. It seems the usable space is 500g. I hope this is something stupid simple, that I will kick myself for later.

---

### Post by zbuddy99 on 2012-03-09
More info yet. Take a look at the attachment.

---

