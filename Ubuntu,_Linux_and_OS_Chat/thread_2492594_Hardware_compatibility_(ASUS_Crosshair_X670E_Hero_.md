---
title: "Hardware compatibility (ASUS Crosshair X670E Hero + RTX 4090)"
date: 2023-11-16
forum: Ubuntu, Linux and OS Chat
---

### Post by twist960 on 2023-11-16
Hi,

New user - relatively familiar with Ubuntu, hopeless with hardware - **looking for a little advice on hardware compatibility**. I have had a look in the compatibility thread but can't find anything about the specific components I'm looking to use.

I have an old computer I'm using **to run machine learning Python scripts** on but unfortunately it has failed so I'm looking to spec a new computer for this but on trying to research Ubuntu compatibility with hardware components, I'm really struggling.

The old computer's drive has a partition with Ubuntu 20 which I'm hoping to migrate over and run but I'm happy to update it to 22 if that's less likely to run into issues.

I was hoping maybe someone familiar with gaming-spec hardware might be able to comment on compatibility? **To be honest, it's mainly the motherboard and GPU I'm concerned about** but I'll list the other specs anyway.

The spec I've configured are as follows:

&#8226; CPU: AMD Ryzen 9 7950X3D 16 Core CPU (4.2GHz-5.7GHz/144MB w/3D V-CACHE/AM5)
&#8226; **Motherboard: ASUS® ROG CROSSHAIR X670E HERO (WIFI 6E, DDR5, PCIe 5.0) **
&#8226; RAM: 64GB Corsair VENGEANCE RGB DDR5 5600MHz (2 x 32GB) AMD
**&#8226; GPU: 24GB NVIDIA GEFORCE RTX 4090 (edited this - erroneously included the 16GB version)**

Additional components that I'm hoping will work OK and shouldn't require specific OS compatibility:
&#8226; CORSAIR iCUE H100i ELITE LCD XT RGB CPU Cooler (250W TDP)
&#8226; CORSAIR 1000W RMx SERIESTM - MODULAR 80 PLUS GOLD
&#8226; Intel I350-T4 V2 Gigabit PCI-E CARD (4 x RJ45)

Really hoping someone here has experience with the above motherboard and GPU combination (with positive results!) but I'm **also happy to be advised of similar hardware that might be better suited**.

I know the recommendation is to avoid Nvidia cards but we ideally want to use one for CUDA (the scripts are built to utilise that platform).

Thanks,

Twist

---

### Post by tea for one on 2023-11-17
This site has a wealth of info [https://linux-hardware.org/](https://linux-hardware.org/)
Worth investigating?

---

### Post by twist960 on 2023-11-20
> **tea for one said:**
> This site has a wealth of info [https://linux-hardware.org/](https://linux-hardware.org/)
Worth investigating?

Thanks, yes I will give this a look!

---

### Post by grahammechanical on 2023-11-20
If the hardware was put on the market after April 2020 then Ubuntu 2020 may not have the hardware drivers. Does Ubuntu 20.04 have them? Does Ubuntu 22.04 have them? If you are thinking about taking the hard drive out of the old machine and putting it into the new machine then disable the proprietary video driver in Software and Updates>Additional drivers tab before you swap it out. Otherwise, you may find that you do not get a video display because the OS is using the wrong proprietary video driver.

Regards

---

### Post by twist960 on 2023-11-21
> **grahammechanical said:**
> If the hardware was put on the market after April 2020 then Ubuntu 2020 may not have the hardware drivers. Does Ubuntu 20.04 have them? Does Ubuntu 22.04 have them? If you are thinking about taking the hard drive out of the old machine and putting it into the new machine then disable the proprietary video driver in Software and Updates>Additional drivers tab before you swap it out. Otherwise, you may find that you do not get a video display because the OS is using the wrong proprietary video driver.

Regards

Good points, thanks. According to the user who provided a link to that useful hardware compatibility website: the RTX 4090 card is functional on Ubuntu, it’s just not 100% clear whether that requires fiddling about with drivers direct from Nvidia.

In anticipation of a worst-case scenario, I will do as you suggest and disable the old Nvidia driver before moving over and once the basics are working, I’ll update to 22 and then install the driver.

I assume this then defaults to some sort of basic cross-compatible driver that attempts to at least get some sort of video out of the card?

---

### Post by monkeybrain20122 on 2023-12-04
> **twist960 said:**
> Good points, thanks. According to the user who provided a link to that useful hardware compatibility website: the RTX 4090 card is functional on Ubuntu, it’s just not 100% clear whether that requires fiddling about with drivers direct from Nvidia.



The most expensive system76 laptop comes with RTX4090 so I suppose it works or can be made to work.

---

