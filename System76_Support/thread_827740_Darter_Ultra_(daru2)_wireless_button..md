---
title: "Darter Ultra (daru2) wireless button."
date: 2008-06-13
forum: System76 Support
---

### Post by laserline on 2008-06-13
Hello,

To all you guys that own a 'daru2' - When you press the wireless button, how many states do you have?

I'll explain:
Do you have:
First Click  - Wifi + Bluetooth ON.
Second Click - Wifi + Blueooth OFF.

*OR*

First Click - Wifi On, Blutooth Off.
Second Click - Wifi + Bluetooth On.
Third Click - Wifi Off, Bluetooth On,
Fourth Click - Wifi + Bluetooth OFF.

You can test that from your laptop's boot screen, so you just test the laptop and don't have the effect of the OS.

Please post your version of Ubuntu and Bios version.

Thanks,
Idan

---

### Post by freduardo on 2008-06-13
I have the MSI PR200.

Using Ubuntu 7.10 and the latest Vista BIOS only gives me two options:
BT and Wifi on
BT and Wifi off

I remember that when it was still running Vista (came pre-installed) I'd have four options:
BT and Wifi on
BT and Wifi off
BT on and Wifi off
BT off and Wifi on
Plus there was an additional 'graphical utility' to manage which had to be on or off.

Nevertheless, I feel that the two possibilities I have now, are more than enough.

---

### Post by laserline on 2008-06-13
But aren't you wasting battery power with BT on ??

Thanks,

Idan.

---

### Post by freduardo on 2008-06-13
Yes, but I think (/me is no expert!) that the power consumption of the BT is rather minute.
It's not like on a mobile phone where you have very limited battery time.

I think I still get about 4 hours easily on a 9-cell battery with Ubuntu. Which is enough for me.
With some more tinkering, I could probably bump that up a notch or two. But I'm too lazy...

---

### Post by laserline on 2008-06-13
A friend of mine has the PR200 (it's like the daru2) and he runs Ubuntu with the 3.43 bios.

He has 4 states with his wireless.

I have only 2.

What are the diffrences between 3.43 and 1.43 from your (PR200) experience ?
If you enable AHCI on the 3.43 does it work exactly like 1.43 ?

Thanks,

Idan.

---

### Post by freduardo on 2008-06-13
Sorry m8,

Can't really help you there, as I've never used the 3.43 BIOS (Win XP). So I can't really compare.

I still keep the Vista recovery partition in case something goes horribly wrong (like when pigs fly etc.) so I honestly can't be bothered to switch to 3.43 just because of the BT switch.

---

### Post by laserline on 2008-06-13
Thanks,

I'll wait for somone with a daru2 to repond.

Idan.

---

### Post by walkeraj on 2008-06-13
It's a bios update thing.  It appears MSI decided that four states weren't necessary and disabled it in the latest bios.  It's not broken, but there's nothing you can really do about it, save downgrade your bios.

If you want to do that, I'd highly recommend getting a bios image from system76 rather than trying to get it from the OEM, because there are manufacturer and model number strings in the bios image that the system76 driver scripts tap into, and they won't work unless they match up.  Even then, I'm not sure if they can support that course of action.

Given that bluetooth consumes such a small amount of power, I wouldn't really worry about it.

---

### Post by laserline on 2008-06-13
I was just wondering :)

I'm not flashing yet...

> 
Given that bluetooth consumes such a small amount of power, I wouldn't really worry about it. 


The funny thing is that I thought BT uses a lot of power.

Let's say I'm using a BT mouse - wouldn't that "drain" the battery?

Idan.

---

### Post by walkeraj on 2008-06-13
> **laserline said:**
> I was just wondering :)

I'm not flashing yet...



The funny thing is that I thought BT uses a lot of power.

Let's say I'm using a BT mouse - wouldn't that "drain" the battery?

Idan.

Sure, but nowhere NEAR as much as wireless would, especially if it's idle.  802.11 uses way more power than bluetooth uses.  That being said, the use case where you might want to use a bluetooth mouse or accessory and not have the wireless on is now gone, which is disappointing.  It would be nice if MSI had made it a BIOS option to have a simple wireless button rather than removing the ability altogether.

I'll look into it and see if there are any options (perhaps an alternate image or something).  Worst comes to worst, I could probably patch an older  BIOS image so that the DMI strings matched up, but that is, of course, a totally unsupportable, warrantee-voidable thing to do. [-X  You could also edit the sys76 drivers script and hard-code it to bypass reading from DMI and then just assume you're a DarU2 (they're in Python, after all).

All of this is, of course, assuming that any update utility you might use would let you downgrade. ;)

---

### Post by laserline on 2008-06-13
What about not enabling wireless via Ubuntu's network applet ?
Will that conserve power the same way as disabling it by pressing the wireless button (assuming 4 states).

Is there a way to disable bluetooth by software in ubuntu ?

Thanks,

Idan.

---

### Post by walkeraj on 2008-06-13
If you uncheck the "enable wireless" box, all you're really doing is telling Gnome not to manage your wireless connection anymore.  Even if you were to issue 

```
/etc/init.d/networking stop
```

You would still only be disabling networking in linux, not killing power to your adapter.  Indeed it would, in theory, consume less energy if you weren't transmitting with it, but it would be negligible.  As long as those two lights are on, both the 802.11 card and the internal bluetooth card are drawing power.

---

### Post by laserline on 2008-06-13
Thanks :)

---

### Post by TheBuzzSaw on 2008-06-13
My daru2 only has two options: both on and both off.

---

### Post by thomasaaron on 2008-06-13
I've seen that before after upgrading the ms-1221 bios.
Doesn't really make sense. But I guess that's the way "they" decided it needed to be. ](*,)

---

### Post by laserline on 2008-06-13
And I thought it was a bug in my laptop...

** It's not a bug... It's Feature ** LoL

---

