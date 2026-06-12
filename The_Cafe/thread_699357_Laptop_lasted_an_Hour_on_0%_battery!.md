---
title: "Laptop lasted an Hour on 0% battery!"
date: 2008-02-17
forum: The Cafe
---

### Post by mridkash on 2008-02-17
A rather interesting thing happened to me sometime back, I was worried about the declining battery life on my year and a half old laptop (compaq). It used to be about 3 hrs but now it went down to just 1 hr.
Ubuntu power analysis shows that the battery life is 45% (poor).

So I decided one day to clean off any memory effect on the battery by discharging it until it dies. As the battery went down to 5% Windows hibernated, then I started Ubuntu and after some time it hibernated too. Then I started ubuntu but the bios screen did not let me and it displayed a message that the battery is critically low and the system cannot boot. Then I plugged in the charger and booted ubuntu and after a moment plugged out again.

I thought it wouldn't boot, but it did and the battery status indicator showed 0% left. (see the screen shot).

Amazingly, the system kept running for about 1 hr on 0% battery, I was shocked to see that. And during that time I played cpu intensive games like chess and vdrift.

After that I have now turned off automatic hibernation on battery discharge and regularly see the indicator going to 0 and laptop still running. I think it is the charge indicating mechanism in the battery which is broken, not the battery itself.
Screen shots attached. you can see the uptime value at top.

---

### Post by tgalati4 on 2008-02-17
What version of Gnome are you running?  Gnome 2.20 has a smarter battery power monitor including continuously-updating power use integration.  This should result in predictions down to a few minutes.

---

### Post by Bachstelze on 2008-02-17
I don't think it's anything software-related, most likely the battery reporting wrong states.

---

### Post by oldb0y on 2008-02-17
> **mridkash said:**
> Amazingly, the system kept running for about 1 hr on 0% battery, I was shocked to see that. And during that time I played cpu intensive games like chess and vdrift.

Wow! Your laptop is super-efficient:lolflag:

---

### Post by Joeb454 on 2008-02-17
I want my battery thing to tell me all that info :(

---

### Post by mridkash on 2008-02-17
> **Joeb454 said:**
> I want my battery thing to tell me all that info :(

You can just click on the battery icon in the system notification area and select Laptop Battery from the menu.

to find more info, right click on the icon and select power history.

---

### Post by jpittack on 2008-02-17
My lasts about 30 minutes after 0%.  Battery says 55%.  Its still just a low 2 hours.  My new battery lasts 5 hours. 9 cell vs. 6 cell.

---

### Post by D-EJ915 on 2008-02-17
that's pretty funny, nice

---

### Post by macogw on 2008-02-18
One of my friends just said it's common for the charge reporting part of the battery to not really know what "0" means.  He said taking it back and forth between hot & cold environments (like leaving it in the car) speeds up that process.

---

