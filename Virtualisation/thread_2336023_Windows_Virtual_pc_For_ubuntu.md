---
title: "Windows Virtual pc For ubuntu"
date: 2016-09-03
forum: Virtualisation
---

### Post by jarvis3 on 2016-09-03
Ive been on ubuntu for a month now. Ive been looking for a virtual pc that runs windows but runs ON UBUNTU. Ive tried virtual box and vmware both of them! but for virtual box i got kernal errors and for vmware well... guess.. MORE ERRORS. Thanks!

---

### Post by howefield on 2016-09-03
Thread moved to the "*Virtualisation*" forum for a better fit.

---

### Post by &amp;KyT$0P# on 2016-09-03
> **jarvis3 said:**
>  for virtual box i got kernal errors 
VirtualBox runs fine here.  This problem should be fixable.

What version of Ubuntu?
What errors specifically you get?
What version of VirtualBox and how did you install it?

Are you running on a EFI system with Secure boot enabled?  If so, disable secure boot in the EFI and try again.

---

### Post by jarvis3 on 2016-09-04
Alright, i reinstalled VirtualBox on my windows 10 and found the problem! I think it was because i did not select an Iso image. But now it does the first ever startup of ubuntu then asks me to select install ubuntu or try ubuntu. I selected both at different times but now i get a new kernal error: This kernal requires an x86-64 CPU, but only detected an i686 CPU. Unable to boot please use a kernal appropriate for your CPU. It shows this error every startup. I know why though. When i created the virtual pc i selected Ubuntu 32 bit although i have a 64bit CPU and i installed a 64bit ubuntu iso image. In virtual box i could not find the 64 bit ubuntu in the list of operating systems.

---

### Post by &amp;KyT$0P# on 2016-09-04
Thank you for posting the solution, good to hear you got it all sorted :KS

---

### Post by SeijiSensei on 2016-09-05
> **jarvis3 said:**
> In virtual box i could not find the 64 bit ubuntu in the list of operating systems.
Funny, if I start typing "Ubuntu" in the top box of the new machine dialog, VirtualBox offers 64-bit Ubuntu as the operating system version by default.

Reboot into your system's BIOS and make sure you have all the virtualization features enabled, especially VT-X.

---

