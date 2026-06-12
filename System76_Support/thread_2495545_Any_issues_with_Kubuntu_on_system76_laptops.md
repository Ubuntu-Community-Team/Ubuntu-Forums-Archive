---
title: "Any issues with Kubuntu on system76 laptops?"
date: 2024-02-22
forum: System76 Support
---

### Post by user1397 on 2024-02-22
Thinking about buying a system76 laptop but as soon as I'd get it, I'd wipe it and install the latest Kubuntu on it.  Has anyone tried this, and are there any issues?  Are there any specific system76 customizations/driver stuff that needs to be done after for you to have a similar experience to popOS/Ubuntu ?

---

### Post by him610 on 2024-02-23
My spouse has a system76 laptop with Xubuntu 23.04.3 installed - never had any issues. I would think you will get similar reliable performance with Kubuntu.

---

### Post by user1397 on 2024-02-23
> **him610 said:**
> My spouse has a system76 laptop with Xubuntu 23.04.3 installed - never had any issues. I would think you will get similar reliable performance with Kubuntu.

Appreciate the response!  Out of curiosity, what model does she have?  and is it intel or AMD?  

I read somewhere someone said that since system76 laptops used coreboot and popOS uses systemd-boot, that installing something like Kubuntu could be tricky as grub would have issues? that doesn't really make sense to me but just wondering.

---

### Post by &amp;KyT$0P# on 2024-02-24
I have previously tried Kubuntu on System76 laptop and did not encounter any issues specific to that combination.

> **user1397 said:**
> Are there any specific system76 customizations/driver stuff that needs to be done 

Just [installing the System76 Driver]("https://support.system76.com/articles/system76-driver").

> **user1397 said:**
> I read somewhere someone said that since system76 laptops used coreboot and popOS uses systemd-boot, that installing something like Kubuntu could be tricky as grub would have issues? that doesn't really make sense to me but just wondering.

This is not true.  The System76 laptop in my case was one of the coreboot ones and GRUB always worked fine on it.

Also by the way, the Pop!_OS live USB boots using GRUB even though an installed Pop!_OS system uses systemd-boot.

---

### Post by him610 on 2024-02-25
> Out of curiosity, what model does she have? and is it intel or AMD?
System76 Pangolin (pnp9) from 2013; it has Intel Core i5-3210M and intel graphics; this model was retired by System76 several years ago. Never experienced any issues with it - now running Xubuntu LTS 24.04.4.
I believe the current Pangolin laptops have AMD APUs

---

### Post by user1397 on 2024-02-27
> **halogen2 said:**
> I have previously tried Kubuntu on System76 laptop and did not encounter any issues specific to that combination.



Just [installing the System76 Driver]("https://support.system76.com/articles/system76-driver").



This is not true.  The System76 laptop in my case was one of the coreboot ones and GRUB always worked fine on it.

Also by the way, the Pop!_OS live USB boots using GRUB even though an installed Pop!_OS system uses systemd-boot.
awesome, thank you for the insight

---

### Post by user1397 on 2024-02-27
> **him610 said:**
> System76 Pangolin (pnp9) from 2013; it has Intel Core i5-3210M and intel graphics; this model was retired by System76 several years ago. Never experienced any issues with it - now running Xubuntu LTS 24.04.4.
I believe the current Pangolin laptops have AMD APUs

good to know, thanks!

---

