---
title: "Now Sound on Virtualbox: Realtek &quot;alc889A&quot;"
date: 2010-05-06
forum: Virtualisation
---

### Post by lancerocke on 2010-05-06
was wondering if i could get some help getting my sound working on my guestos (windows 7) via virtualbox on my realtek alc889A.
Have been googling all day

---

### Post by lmarmisa on 2010-05-07
Do you see the speaker icon at your upper bar? Is the same icon than in my desktop?.

Best regards,

Luis

---

### Post by lancerocke on 2010-05-08
> **lmarmisa said:**
> Do you see the speaker icon at your upper bar? Is the same icon than in my desktop?.

Best regards,

Luisthe icon is not on either. thanks for the reply

---

### Post by lmarmisa on 2010-05-08
Could you tell me what information shows VirtualBox in its window about the Audio (Host driver and controller)?.

---

### Post by lancerocke on 2010-05-08
> **lmarmisa said:**
> Could you tell me what information shows VirtualBox in its window about the Audio (Host driver and controller)?.
sure, thanks.

Host Driver:

PulseAudio
Controller:

ICH AC97

---

### Post by lmarmisa on 2010-05-08
Is your Host Audio driver field blank? In my case this is Windows DirectSound. Your controller seems that is ICH AC97 too.

Have you installed the VirtualBox Guest Additions in your guest system?.

---

### Post by lancerocke on 2010-05-08
> **lmarmisa said:**
> Is your Host Audio driver field blank? In my case this is Windows DirectSound. Your controller seems that is ICH AC97 too.

Have you installed the VirtualBox Guest Additions in your guest system?.
yes i installed the virtualbox guest additions
[[IMG]http://thumbnails23.imagebam.com/7966/b2719779659527.gif[/IMG]](http://www.imagebam.com/image/b2719779659527)
[[IMG]http://thumbnails12.imagebam.com/7966/f28df379659535.gif[/IMG]](http://www.imagebam.com/image/f28df379659535)

---

### Post by lancerocke on 2010-05-08
i installed [this driver]("http://www.download3k.com/Install-Realtek-AC-97-Vista-Driver.html"), but i have very choppy sound in the guest os win7

---

