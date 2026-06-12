---
title: "Is Firefox safe for DD-WRT firmware updates?"
date: 2007-08-09
forum: The Cafe
---

### Post by Atreus12 on 2007-08-09
The DD-WRT website recommends NOT using Firefox to update the firmware, they recommend internet explorer instead.  However, I don't have Windows installed anymore, so thats not really an option. I just wondered what other people were doing.

-Andrew

Edit: I meant install, as in for the first time

---

### Post by jkeyes0 on 2007-08-09
I never knew they recommended IE. I installed and have updated DD-WRT using firefox, and didn't have a problem...

I suppose you could always install ies4linux and use it to install the DD-WRT update if you wanted to.

---

### Post by starcraft.man on 2007-08-09
I flashed DD-WRT on my old linksys router and I'm pretty sure I used Firefox. Not sure why it'd be a problem...

This is the guide I used. It is specifically aimed at the wrt54G router but I'm pretty sure you can use it as a general guide, has nice pictures too. I don't think it's specific to Windows, though I did it on XP for convenience (was in that at the time) so not sure. Good luck with flashing, and hopefully it doesn't brick.

Edit: Wuups, this is the link to the [guide.]("http://www.scorpiontek.org/portal/content/view/27/36/") Should be useful for new folks to DDWRT, I assume since your updating you probably know it all. Oh and I just looked, only thing that looks specific is the networking bit but I think you can do same thing in Ubuntu without trouble. Run through it first without modifying to be sure. Have fun, it's good firmware.

---

### Post by BlueStreak on 2007-08-09
I also used firefox to flash, no issues here

---

### Post by LookTJ on 2007-08-09
> **jkeyes0 said:**
> I never knew they recommended IE. I installed and have updated DD-WRT using firefox, and didn't have a problem...

I suppose you could always install ies4linux and use it to install the DD-WRT update if you wanted to.

Same here, I used firefox and tftp to install dd-wrt. Not sure about upgrading since I had the latest firmware for at least 5 months  (March).

---

### Post by Atreus12 on 2007-08-09
> **starcraft.man said:**
>  Should be useful for new folks to DDWRT, I assume since your updating you probably know it all. Oh and I just looked, only thing that looks specific is the networking bit but I think you can do same thing in Ubuntu without trouble. Run through it first without modifying to be sure. Have fun, it's good firmware.

Woops, I meant installing. I am going to be installing DD-WRT for the first time. Thanks for the link, I am installing on a WRT54GS

Just wondering, what is the advantage of using tftp?
-Andrew

---

### Post by starcraft.man on 2007-08-09
> **Atreus12 said:**
> Woops, I meant installing. I am going to be installing DD-WRT for the first time. Thanks for the link, I am installing on a WRT54GS

-Andrew

Ok then, that link should be helpful then. If you got any questions or problems (or something Windows specific not sure of) post back here and I or someone else should be able to help. I advise you to copy/save the pages to your desktop since you won't have access to the router/net during flash. 

Best of luck, good choice on firmware. :)

---

### Post by LookTJ on 2007-08-09
> **Atreus12 said:**
> Woops, I meant installing. I am going to be installing DD-WRT for the first time. Thanks for the link, I am installing on a WRT54GS

Just wondering, what is the advantage of using tftp?
-AndrewIf WRT54GS, use this link, [http://www.bitsum.com/openwiking/owbase/ow.asp?WRT54G5_CFE#h8](http://www.bitsum.com/openwiking/owbase/ow.asp?WRT54G5_CFE#h8) please note that this may be out of date.

---

### Post by Atreus12 on 2007-08-09
Ok, someone's going to have to explain this to me. Why do some guides recommend flashing the router with vxworks, and then tftp-ing the dd-wrt firmware?

Why not just flash it from the stock gui?

I have a WRT54GS version 1.0 if that makes a difference

---

### Post by LookTJ on 2007-08-09
> **Atreus12 said:**
> Ok, someone's going to have to explain this to me. Why do some guides recommend flashing the router with vxworks, and then tftp-ing the dd-wrt firmware?

Why not just flash it from the stock gui?

I have a WRT54GS version 1.0 if that makes a difference

You can't access the gui to flash the firmware. You'll have to TFTP or other suggestions.

---

### Post by Atreus12 on 2007-08-09
> **Taylor said:**
> You can't access the gui to flash the firmware. You'll have to TFTP or other suggestions.

Why use vxworks at all? Why not directly upload the dd-wrt firmware?

I think the vxworks is only applicable to versions after 5.0, I am at 1.0 (it's like 5 years old)

-Andrew

---

### Post by LookTJ on 2007-08-09
> **Atreus12 said:**
> Why use vxworks at all? Why not directly upload the dd-wrt firmware?

I think the vxworks is only applicable to versions after 5.0, I am at 1.0 (it's like 5 years old)

-Andrew

I have said other suggestions. But I have never tried vxworks so I can't tell you whether to use it or not. I have a wrt54gs v5 and used tftp...success

---

### Post by starcraft.man on 2007-08-09
> **Atreus12 said:**
> Why use vxworks at all? Why not directly upload the dd-wrt firmware?

I think the vxworks is only applicable to versions after 5.0, I am at 1.0 (it's like 5 years old)

-Andrew

You mean use the GUI built into the linksys router (i.e. one you access with 192.168.1.1 under administration) to directly upload the dd-wrt firmware? Ya, I'm pretty sure you can't do that as the GUI is limited to using only linksys firmware updates. They wouldn't tell you to do stuff unless you had to. I could be wrong, if I am someone correct away.

As for your version, 1, are you sure? Geez, I'm tempted to say go buy a cheap newer version 5 to flash. That seems pretty old, and I just can't help ya with that. Mine is a version 6.

Best of luck.

Edit:
> **Taylor said:**
> I have said other suggestions. But I have never tried vxworks so I can't tell you whether to use it or not. I have a wrt54gs v5 and used tftp...success
I checked your link and it's version 5 or 6 too. I don't think many people have older versions anymore. You may just be out of luck atreus. I certainly can't guarantee following those steps will work...

---

### Post by LookTJ on 2007-08-09
> **starcraft.man said:**
> As for your version, 1, are you sure? Geez, I'm tempted to say go buy a cheap newer version 5 to flash. That seems pretty old, and I just can't help ya with that. Mine is a version 6.

Best of luck.I wouldn't suggest that. wrt54gs v5 and up are more limited than the older versions and other older models. Someone correct me if I'm wrong.

---

