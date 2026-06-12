---
title: "Regnum cannot support my video card"
date: 2009-04-11
forum: Ubuntu Gamers Arena
---

### Post by Cammytea on 2009-04-11
when logging into regnum online a message pops up not letting me access the game the message says:

Unsupported video card!

There are three possible causes for this error:
1. Your video card is too old
2. You haven't installed the latest available drivers
3. You haven't installed the latest DirectX version

I am unsure if I need a new video card or simply to install some stuff,
I do not know what directX is either.

I would be very grateful if anyone could help, 
thank you,
Cameron :)

---

### Post by tomplast on 2009-04-14
> **Cammytea said:**
> when logging into regnum online a message pops up not letting me access the game the message says:

Unsupported video card!

There are three possible causes for this error:
1. Your video card is too old
2. You haven't installed the latest available drivers
3. You haven't installed the latest DirectX version

I am unsure if I need a new video card or simply to install some stuff,
I do not know what directX is either.

I would be very grateful if anyone could help, 
thank you,
Cameron :)

If you want help then you have to tell us a little more about your system and hardware. Which Linux distro are you running? What is the name of the video card? Run **lspci | grep VGA** in a terminal if you don't know what video card you have. And finally, have you installed 3d drivers for your card?

---

### Post by Cammytea on 2009-04-15
I did that and it says: 00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)

I am running ubuntu 8.10 but have not installed any 3d drivers, I do not know which ones to install

My computer is a dell inspiron 6000 with intel centrino proccsor

---

### Post by b6of12 on 2009-05-06
you wont nvidia drivers  17x.xx I think you can install tham by left hand corner of screen system/administration/hardware drivers it onley shows drivers that are compatable with your system

---

### Post by CharmyBee on 2009-05-07
> **b6of12 said:**
> you wont nvidia drivers  17x.xx 
This is Intel hardware. nvidia drivers won't turn it into an nvidia card.

DirectX requirement sounds like a WINE compatibility issue.

---

### Post by Perfect Storm on 2009-05-08
> **CharmyBee said:**
> This is Intel hardware. nvidia drivers won't turn it into an nvidia card.

DirectX requirement sounds like a WINE compatibility issue.

Now, that would be ground breaking! :P:P

---

