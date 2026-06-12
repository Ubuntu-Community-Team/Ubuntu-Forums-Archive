---
title: "Nvidia GTX 770 visual artifact issue"
date: 2014-12-22
forum: System76 Support
---

### Post by Q-collective on 2014-12-22
Hi all,

On my Leopard Extreme 4th generation I own a GTX 770 with 4GB memory. When using the proprietary Nvidia drivers, I have reoccuring visual artifacts which predominantly occur in the Unity UI and on websites (independent of browser). These artifacts are best described as a sort of 'stuttering'. 

- The issue does not occur when using the Nouveau drivers.
- The issue seems particularly present in Unity's UI, but also occurs in Cinnamon (on a clean install of Mint with a clean home directory).
- The issue occurs with multiple versions of the proprietary driver (currently having version 340.65 installed, released this month).

Is this simply a setting in the Nvidia drivers that should be switched on or off, or is there a deeper issue at play here?

Thank you!

---

### Post by Q-collective on 2015-02-23
So, since this issue just remained and remained I opted to just drop the Nvidia drivers and switch back to Nouveau.

Too bad it just kills most of my games :(

---

### Post by JeQhdMD on 2015-02-23
Did you try the nvidia console to adjust video config . . . or . . . the nvidia forums may provide more insight into fixes or adjustments.   

You could also run nouveau on Mint-Mate using Virtual Box for non-gaming, while the host OS is still Ubuntu Unity Utopic used mainly for gaming, etc.

(ps -  are the System76 drivers still running/active with crrent ppa?)

---

### Post by Q-collective on 2015-02-23
> **JeQhdMD said:**
> Did you try the nvidia console to adjust video config . . . or . . . the nvidia forums may provide more insight into fixes or adjustments.   
I could open a thread on the Nvidia forums about it. Thanks for the suggestion.

> You could also run nouveau on Mint-Mate using Virtual Box for non-gaming, while the host OS is still Ubuntu Unity Utopic used mainly for gaming, etc.
That seems like a very awkward workaround, but then again, it could work really well to split the usecases up like that. It could just prove to be awkward with backups and such as they'd need to copy the entire vbox file to the backup disk every time only a minute change happens. Hmm.

> (ps -  are the System76 drivers still running/active with crrent ppa?)
I've had bad experiences using them in the past, often resulting in a non-working X for me. So, whenever I use the Nvidia drivers, I manually install them from the Nvidia site.

---

### Post by JeQhdMD on 2015-03-01
You might also try Mint-Cinnamon DE using a live _USB-v3 with persistence_.   That way you could install the video drivers and test run the implementation on a different gtk3 desktop than Unity.

---

### Post by Mateusz Stachowski on 2015-03-22
Your issues are result of this bug:

[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/269904](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/269904)

It is fixed in 15.04 (development release) and 14.04 LTS but not in 14.10. When you post in a forum always state which version of Ubuntu you are running. I only learned that you use 14.10 because I saw your second post on NVIDIA forums.

You could comment in that bug report to remind Ubuntu developers that they still didn't release fix for Utopic.

---

