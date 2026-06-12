---
title: "Any XP users?"
date: 2010-12-21
forum: The Cafe
---

### Post by joelkat on 2010-12-21
I am dual booting using my desktop getting internet through my modem to my router that I used a cord to connect to my desktop but I do not know how to connect to the internet as I am not very good with XP???

---

### Post by Ekeluo on 2010-12-21
More info will be needed to offer valuable help, e.g. PC make/model(to know network interfaces), make/model of router, also whether XP is completely satisfied with your system (Device Manager will tell you this info and also about missing drivers). Right click on any 'my computer' icon, select 'properties'.

---

### Post by rev elation on 2010-12-21
So it's working with your linux on the same computer but not with XP?

my initial guess would be that you don't have drivers for your network.

---

### Post by joelkat on 2010-12-21
so what do I do?/?

---

### Post by joelkat on 2010-12-21
where do I get these drivers?

---

### Post by rev elation on 2010-12-21
Open the device manager, it can be found in the control panel or possibly if you right click "your computer" and go to properties to find out;
are there missing drivers?
what parts have missing drivers?
what brands/models are they?

then you go to the google machine and find drivers for those parts.

It's also highly possible that you got a CD with your motherboard, that CD would contain the drivers.
If you want to, post what parts you are using here and I can try to help you find the drivers.


What kind of computer is it? Are you using a laptop or a desktop? is it a brand-computer or home-made?

---

### Post by Verbeck on 2010-12-21
> **joelkat said:**
> where do I get these drivers?
whats the make/model of the ethernet controller? or the pc

---

### Post by uRock on 2010-12-21
> **Verbeck said:**
> whats the make/model of the ethernet controller? or the pc
+1. If we have this info, then we can help you find where to download the drivers from while using Linux or another computer, then you can put the exe on a thumb drive or whatever to install while in XP.

---

### Post by joelkat on 2010-12-21
the ethernet controller? my computers model compaq presario

---

### Post by rev elation on 2010-12-21
> **joelkat said:**
> my computers model compaq presario

well that narrows it down somewhat, but we still need the modelnumber.

---

### Post by NormanFLinux on 2010-12-21
Ylmf OS... run it alongside XP and you'll never know you're running Ubuntu! :D

---

### Post by Khakilang on 2010-12-21
Window XP like any OS need hardware drivers for it to work. Your computer should come with a motherboard drivers CD and so is your router, printer, USB dongle or any hardware you purchase. If you don't have the CD drivers. Open up the case and see what brand of motherboard and search the internet for the drivers.

---

### Post by uRock on 2010-12-22
> **NormanFLinux said:**
> Ylmf OS... run it alongside XP and you'll never know you're running Ubuntu! :D
He/she needs help with XP, not Ubuntu.

---

### Post by sdowney717 on 2010-12-22
you can use virtualbox to run XP inside of ubuntu and then you will have the internet working.
It sounds like your XP version needs drivers for the ethernet card.
In ubuntu simply list them from terminal like
lspci

or when running xp use device manager to find the card and then use ubuntu to find an xp driver if your lucky! There may not be one. I would have thought if your using the original on board ethernet hookup that XP would have automatically detected and installed a driver.
anyway, device manager in XP will tell you if it is there and working or not.

---

### Post by sdowney717 on 2010-12-22
[http://www.ylmf.org/en/](http://www.ylmf.org/en/)

interersting, but uses wine so its a cripple, you wont be able to run a lot of windows apps.

---

