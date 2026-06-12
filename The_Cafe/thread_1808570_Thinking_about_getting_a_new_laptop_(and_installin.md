---
title: "Thinking about getting a new laptop (and installing Ubuntu on it)"
date: 2011-07-20
forum: The Cafe
---

### Post by Kimm on 2011-07-20
Does anyone have any comments on this comp? 

[google translated link]("http://translate.google.com/translate?js=n&prev=_t&hl=en&ie=UTF-8&layout=2&eotf=1&sl=auto&tl=en&u=http%3A%2F%2Fwww.elgiganten.se%2Fproduct%2Fdatorer-tillbehor%2Fbarbar-dator%2FSAMNPRV511S06%2Fsamsung-np-rv511-s06se-15-6-barbar-dator&act=url")

Sorry about google-translated link, couldn't find anything better. Do you think this laptop would work well with Ubuntu? I'm concidering dual-boot with Windows 7 that comes pre-installed.

any comments appretiated ^^ I would use the laptop for writing, statistics, surfing and perhaps playing WoW now and then :)

---

### Post by jrozo17 on 2011-07-20
> **Kimm said:**
> Does anyone have any comments on this comp? 
 
[google translated link]("http://translate.google.com/translate?js=n&prev=_t&hl=en&ie=UTF-8&layout=2&eotf=1&sl=auto&tl=en&u=http%3A%2F%2Fwww.elgiganten.se%2Fproduct%2Fdatorer-tillbehor%2Fbarbar-dator%2FSAMNPRV511S06%2Fsamsung-np-rv511-s06se-15-6-barbar-dator&act=url")
 
Sorry about google-translated link, couldn't find anything better. Do you think this laptop would work well with Ubuntu? I'm concidering dual-boot with Windows 7 that comes pre-installed.
 
any comments appretiated ^^ I would use the laptop for writing, statistics, surfing and perhaps playing WoW now and then :)
 
Yes, that should be fine. My laptop has the SAME exact specs(except for being a Dell) and Ubuntu 11.04 runs fast on it.
 
Not to sure about earlier releases though... 10.04 didn't detect any wifi :(

---

### Post by Simian Man on 2011-07-20
The tricky thing will be that the graphics card has Optimus which is not supported on Linux currently.  If the BIOS lets you disable it you will be alright otherwise you'll likely be in trouble.

---

### Post by Kimm on 2011-07-20
> **Simian Man said:**
> The tricky thing will be that the graphics card has Optimus which is not supported on Linux currently.  If the BIOS lets you disable it you will be alright otherwise you'll likely be in trouble.

Would it still work but with reduced functionality? I imagine it would be hard to find a decent laptop with an nvidia GPU that doesnt have Optimus.

Otherwise, I might consider having just Windows 7 on it until Bumblebee is usable

---

### Post by forrestcupp on 2011-07-20
I would think that it would work. The nvidia binary drivers support the GeForce 315m, so I would think it would work without that functionality.

I would make sure to create your system restore DVDs before you install Ubuntu, just in case you screw something up and need to reinstall your system.

---

### Post by beew on 2011-07-20
> **Kimm said:**
> Would it still work but with reduced functionality? I imagine it would be hard to find a decent laptop with an nvidia GPU that doesnt have Optimus.



No, the Nvidia card will not work at all if the laptop has Optimus but it would still generate heat and eat your battery. The card  has Linux support is irrelevant. The linux drivers supplied by Nvidia doesn't work with Optimus (nouveau doesn't work either)

The intel card on the other hand works with diminished functionality so that it is worse than it would working alone (fore example it may not  support Unity though even a very old Intel card on a beaten up crappy laptop would out of the box)

So you should definitely do more research. I think not all SamSung laptops with Nvidia come with Optimus, it seems to depend on the series.
> 

Otherwise, I might consider having just Windows 7 on it until Bumblebee is usableIf the laptop has Optimus you can install Ubuntu in an external drive and boot from it try using bumblebee and help the project along by filing bugs or reporting success. I would if I have an Optimus laptop.

There is now a bumblebee ppa for Ubuntu

[https://github.com/MrMEEE/bumblebee](https://github.com/MrMEEE/bumblebee)
(see the Readme)

---

### Post by beew on 2011-07-20
> **forrestcupp said:**
> I would think that it would work. The nvidia binary drivers support the GeForce 315m, so I would think it would work without that functionality.
.

No it won't. The Nvidia driver supports the card working by itself, it becomes a hybrid with Optimus and the Nvidia driver wouldn't work at all.

---

### Post by forrestcupp on 2011-07-20
> **beew said:**
> No it won't. The Nvidia driver supports the card working by itself, it becomes a hybrid with Optimus and the Nvidia driver wouldn't work at all.

I see. So with Optimus, you're using Intel graphics until you need 3D, then it turns on the nvidia GPU? I would hope that the BIOS would let you choose to not use that option, like Simian Man suggested. Hopefully nvidia gets on that pretty quickly for the Linux binaries.

---

### Post by Simian Man on 2011-07-20
> **forrestcupp said:**
> I see. So with Optimus, you're using Intel graphics until you need 3D, then it turns on the nvidia GPU? I would hope that the BIOS would let you choose to not use that option, like Simian Man suggested. Hopefully nvidia gets on that pretty quickly for the Linux binaries.

Some BIOS will let you disable it apparently, but the one I tried it with didn't.  And Nvidia has said they have no plans to provide Linux support for it, so it's kind of a mess at the moment.  The laptop I tried it on would not allow any compositing, allow me to change the brightness or allow me to use the external VGA port, so it was basically useless.

If you're set on that laptop, the best option would probably be to keep Windows and run Linux in a VM honestly - again unless the BIOS lets you disable it, which is info that manufacturers think to unimportant to disclose.

---

### Post by 3Miro on 2011-07-20
1. Unless you intend to dual-boot, get a laptop with Linux pre-installed. Even if it is not Ubuntu, you will know that things are compatible.

2. Do not waste your money on incompatible or semi-compatible hardware. People are commenting about Optimus and I have no experience with that, however, I have experience with Broadcom WiFi. While it works, it is always a hassle, if I had to do it all over again, I would have bought a different card.

---

### Post by Kimm on 2011-07-21
Lots of comments here, I am still considering getting that laptop and dual boot Ubuntu and Windows for testing Bumblebee and reporting bugs. However, where do you see that it has Optimus? I cant find it on that site, but when I googled on the model I found another laptop that looked exactly the same and had a similar name (NP-RV520-S01SE compared to NP-RV511-S06SE) but another graphics chipset (Geforce 520M) that did mention Optimus. I just want to be sure no one just googled it and happened to come across this model instead! :)

In any case, this will require more consideration than I had hoped, my only previous laptop was an Asus eeePC that works flawlessly with Ubuntu, I was hoping the same would go for most laptops. As for buying one with Linux preinstalled, there are no vendors that sell linux laptops in Sweden that I know of and I don't feel like buying from a vendor outside the country (due to extra shipping costs and delays if something breaks)

Edit: might not be so bad to keep a Windows computer around anyway, since I do some programming and don't want to dual-boot my desktop. I could still use my favorite applications anyway :)

---

### Post by Simian Man on 2011-07-21
> **Kimm said:**
> However, where do you see that it has Optimus? I cant find it on that site

When I saw it had an Nvidia GPU, Optimus was my first concern so I googled "NVIDIA GeForce 315m" and saw [this page]("http://www.nvidia.com/object/product-geforce-315m-us.html") on the Nvidia site which says this GPU does have Optimus.

BTW I love how the translation page says "Plenty of power tasty wrapped in a single laptop" :).

Good luck whatever you decide on.

---

