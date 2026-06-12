---
title: "ATI Radeon Ll7004D driver"
date: 2008-11-13
forum: Windows
---

### Post by diwas on 2008-11-13
Well i have a chinese laptop and it has windows XP built in. And the graphics card is ATI Radeon Ll7004D. I didnt find any driver of this model in their website. 
I dont know the card's capacity either. It just shows N/A, which directly means that the driver is not installed. Is there anyway i can get this driver for WINDOWS XP?? 

If its my faulty reading of the driver's serial number, iam sorry. And i would like to know how to read the model number of the card.

Thank you.

PS: The BIOS and all other system stuffs are in chinese...(or it looks like so...). And i dont know the language. Thus cannot read anything.

---

### Post by prshah on 2008-11-13
> **diwas said:**
> Well i have a chinese laptop and
 the graphics card is ATI Radeon Ll7004D. I didnt find any driver of this model in their website. 
And i would like to know how to read the model number of the card.

PS: The BIOS and all other system stuffs are in chinese.. Thus cannot read anything.

Get hold of an Ubuntu live CD, boot off it (Choose English for the language!), then open a terminal (Applications-Accessories-Terminal) and post the results of the following commands```
lspci | grep -i -E graphics\|vga
sudo lshw -C display
```

This will give us details on what graphics card is in use, and then someone can advise you on what to download from where.

---

