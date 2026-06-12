---
title: "Windows 10 and VHD native boot Ubuntu"
date: 2017-02-08
forum: Virtualisation
---

### Post by eino-makitalo on 2017-02-08
I asked already on Windows forums question 

Microsoft Community: Windows 10 and native VHD boot of Ubuntu 16.04 LTS [https://answers.microsoft.com/thread/5a8f0f71-e1f7-405c-9c3e-c45bb89e93b7](https://answers.microsoft.com/thread/5a8f0f71-e1f7-405c-9c3e-c45bb89e93b7)

If anybody has succeeded to install Ubuntu so that you can also native boot from VHD disk, please share your knowledge.
This is a feature of Windows  that you can boot another system native mode from VHD disk normally used with Hyper-V (or Virtual Box).

-Eino

---

### Post by wildmanne39 on 2017-02-08
Virtualbox does not support Hyper-V technology.

---

### Post by ian78 on 2017-02-10
I tried something similar on my work laptop a few years ago when VHD boot was first released and i had no luck either. I was just trying to dual boot a Windows desktop and a Windows Server at the time so no Linux OS in the mix and everything was on the Microsoft stack. The server was in a VHD and the windows desktop was installed as normal on the disk. The thing that was causing me trouble was my employers use of PGP Desktop whole disk encryption software which seemed to be getting very much in the way and causing the VHD boot process to fail very early in the cycle. I never did get to the root cause but i believe it was likely that the hypervisor was unable to read the VHD because it was on an encrypted partition.

I notice your post on the Microsoft forum mentions bit locker so that could be the problem in your case too.

---

