---
title: "&quot;No wireless networks foud&quot;"
date: 2014-01-30
forum: Virtualisation
---

### Post by abdallah3 on 2014-01-30
Hello

I am using backtrack 5 on virtualbox, I am using a D-LINK network adapter, I am trying to connect to the internet, it says "no wireless networks found'.


Thanks.

---

### Post by tfrue on 2014-01-31
I've never had wireless to work in virtual box, but you can try this webiste

[https://forums.virtualbox.org/viewtopic.php?f=8&t=19305](https://forums.virtualbox.org/viewtopic.php?f=8&t=19305)

go to the fourth post down

Good luck,
Chris

---

### Post by Bucky Ball on 2014-01-31
*Thread moved to **Virtualisation**.*

Benefit of the doubt here as I'm presuming you're using Ubuntu as the host. Backtrack is not officially supported in the main support areas of the forum and any support requests directly related to it should be posted in ***Other OS Support***. Cheers.

---

### Post by TheFu on 2014-02-02
> **abdallah3 said:**
> Hello

I am using backtrack 5 on virtualbox, I am using a D-LINK network adapter, I am trying to connect to the internet, it says "no wireless networks found'.


Thanks.

Inside virtual machines, the actual, physical, devices in the real computer don't matter unless you setup some sort of passthru. Passthru doesn't work consistently and if the device being "passed thru" to the clientOS is a PCI, PCIx, PCIe adapter, it is much, much harder to make this experimental feature work. The vbox manual has a section on what the hostOS and physical hardware requirements are to accomplish this.

If the network adapter is USB, there is much more hope that passthru can be made to work.

I hope this makes sense.

---

