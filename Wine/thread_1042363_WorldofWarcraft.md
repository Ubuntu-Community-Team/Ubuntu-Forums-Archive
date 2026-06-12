---
title: "WorldofWarcraft"
date: 2009-01-17
forum: Wine
---

### Post by ozzyprv on 2009-01-17
I (unfortunately) installed WoW in my windowS partition. Now I regret my decision. 
Is there are way that I could access to that installed version of WoW via Wine or some other system from Ubuntu.

Thanks.

---

### Post by panaut0lordv on 2009-01-17
Applications -> Add/Remove -> Disk Manager :)
Setup & go.

EDIT: Copying or reinstalling shouldn't be hard.

---

### Post by ozzyprv on 2009-03-08
> **panaut0lordv said:**
> Applications -> Add/Remove -> Disk Manager :)
Setup & go.

EDIT: Copying or reinstalling shouldn't be hard.


I had to re-install the whole thing via Wine. So far so good!.

---

### Post by hikaricore on 2009-03-09
Since WoW does not use the windows registry (or not for anything important) it can be easily copied from one drive to another without having to reinstall.

---

### Post by ozzyprv on 2009-03-09
It did not worked for me. Program went frozen when I tried "wine Wow.exe".

Thanks.

Up and running now....with low FPS thou...

---

### Post by TheHolm on 2009-03-10
> **ozzyprv said:**
> It did not worked for me. Program went frozen when I tried "wine Wow.exe".

Thanks.

Up and running now....with low FPS thou...

Configure WoW to use OpenGL. And instal closed code driver for your video card.

---

### Post by ozzyprv on 2009-03-10
> **TheHolm said:**
> Configure WoW to use OpenGL. And instal closed code driver for your video card.

This is another interesting point.
I started modifying the wow config file to use OpenGL.
Then I notice a bumpy mouse pointer and decided to give it a try without the OpenGL mod. 
Mouse pointer seems to be better using default (DirectX I guess) grpahic mode.


What is "closed code driver"? I am at nvidia 180.11.

Thanks.

---

### Post by Spr0k3t on 2009-03-10
> **ozzyprv said:**
> What is "closed code driver"? I am at nvidia 180.11.

That's the "closed code driver"... aka, "binary release driver"... aka, "closed source driver"... aka... I'll stop there, the rest aren't for kids.

---

### Post by ozzyprv on 2009-03-11
> **ozzyprv said:**
> This is another interesting point.
I started modifying the wow config file to use OpenGL.
Then I notice a bumpy mouse pointer and decided to give it a try without the OpenGL mod. 
Mouse pointer seems to be better using default (DirectX I guess) grpahic mode.
Thanks.

Correction,mouse move more smoothly but FPS dropped a lot. I
 went back to OpenGL and the bumpy mouse (but a decent FPS).

Still working on improving the sound.

---

