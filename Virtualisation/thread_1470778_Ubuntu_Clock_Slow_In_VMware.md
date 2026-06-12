---
title: "Ubuntu Clock Slow In VMware"
date: 2010-05-03
forum: Virtualisation
---

### Post by robinhood2008 on 2010-05-03
When I first installed Ubuntu Lucid Lynx 10.04 on a new virtual machine using VMware Player 3.0.1, I noticed that Ubuntu's guest clock was two hours slow compared to my Windows host's clock. I corrected this problem manually, but when I installed and ran VMware Tools and selected "Time synchronization between the virtual machine and the host operating system", VMware Tools insisted on setting Ubuntu's guest clock two hours backwards again! Having to correct Ubuntu's guest clock over and over again is getting to be a real nuisance for me. Is there any way to force Ubuntu's guest clock to behave properly, or is there at least a way in Lucid Lynx to make Ubuntu's guest clock to synchronize with an Internet time server? (I was able to do that with a previous version of Ubuntu, and I just wondered what happened to that feature either in Lucid Lynx or a previous incarnation of Ubuntu.)

I thank you for any help you can give me in this matter.

Brandon Taylor

---

### Post by dcstar on 2010-05-05
> **robinhood2008 said:**
> When I first installed Ubuntu Lucid Lynx 10.04 on a new virtual machine using VMware Player 3.0.1, I noticed that Ubuntu's guest clock was two hours slow compared to my Windows host's clock. I corrected this problem manually, but when I installed and ran VMware Tools and selected "Time synchronization between the virtual machine and the host operating system", VMware Tools insisted on setting Ubuntu's guest clock two hours backwards again! Having to correct Ubuntu's guest clock over and over again is getting to be a real nuisance for me. Is there any way to force Ubuntu's guest clock to behave properly, or is there at least a way in Lucid Lynx to make Ubuntu's guest clock to synchronize with an Internet time server? (I was able to do that with a previous version of Ubuntu, and I just wondered what happened to that feature either in Lucid Lynx or a previous incarnation of Ubuntu.)

I thank you for any help you can give me in this matter.

Brandon Taylor

If you set the Timezones correctly on the VM and the host there should not be a problem.

---

