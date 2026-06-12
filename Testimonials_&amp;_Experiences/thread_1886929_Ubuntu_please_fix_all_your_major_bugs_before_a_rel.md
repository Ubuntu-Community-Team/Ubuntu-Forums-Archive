---
title: "Ubuntu please fix all your major bugs before a release"
date: 2011-11-25
forum: Testimonials &amp; Experiences
---

### Post by Raul1800 on 2011-11-25
okay,

so here's my rant,(srry if i curse but i'm seriously pissed right now). so i wanted to migrate from windows 7 to ubuntu 11.10, i had once used ubuntu 9.04 to 10.10 and loved my experience. so i dualbooted ubuntu 11.10 and windows 7 on my acer aspire laptop and the set up was nice and easy. however, when i tried restarting my pc to boot ubuntu i was greeted with a black screen and spent literally 5-6 frustrating hours loking through the forums and google to fix this bug. when i finally fixed it i was very relived and started enjoying the world of ubuntu, until i closed the lid of a my laptop and another dang black screen greeted me. i hit every button on my laptop to get it working but nothing worked. so i decided to do a hard reboot. i then spent my next 4-5 hours trying to fix this problem digging through the ubuntu forums,youtube and google. i got tired and just said i'll fix it tomorrow. but wait, you know what happened next? the dam black screen, that i had thought was gone, greeted me every single time i chose what os to use, in the start of the grub. so i'm tired and currently removing ubuntu from my system. don't get me wrong i love Ubuntu but i wonder how these two major bugs got through the devs, thanks for all your work. so now i'm stuck with windows 7:(:(:(:(, which i sincerely dislike, but NO bugs AND its software compatability is enormous. so to end this plz ubuntu for you're next release fix you're major bugs. thanks to whoever read this ginormouse thread and i hope i didn't put it in the wrong place.

---

### Post by IWantFroyo on 2011-11-25
Bugs are extremely selective to hardware. If you put up your computer specs, it'll show up in Google for people with the same computer and problem, so I would recommend doing that. Just so you know, this bug could be unknown.

It sounds like your computer is having problems with the acpi power manager. Try this:
```
gksudo gedit /etc/default/grub
```
Change this line:
GRUB_CMDLINE_LINUX=""
To:
GRUB_CMDLINE_LINUX="acpi=off"

Then:
```
sudo update-grub
```

If you can boot up with acpi=off, then I would encourage you to try "pci=noacpi" as well. Remember to run update-grub whenever you change something.

---

### Post by Raul1800 on 2011-11-25
> **IWantFroyo said:**
> Bugs are extremely selective to hardware. If you put up your computer specs, it'll show up in Google for people with the same computer and problem, so I would recommend doing that. Just so you know, this bug could be unknown.

It sounds like your computer is having problems with the acpi power manager. Try this:
```
gksudo gedit /etc/default/grub
```
Change this line:
GRUB_CMDLINE_LINUX=""
To:
GRUB_CMDLINE_LINUX="acpi=off"

Then:
```
sudo update-grub
```

If you can boot up with acpi=off, then I would encourage you to try "pci=noacpi" as well. Remember to run update-grub whenever you change something.

thanks for replying, and i'll try to search it that way for a problem if i ever get back into ubuntu since i removed it and back on windows 7, no bugs :D

i actually did this exact workaround, which i found in another thread, and everything worked for like a day but after i found the close lid and black screen bug, which i was working on fixing it for a very long time. the next time i rebooted my pc the black screen came back at start up it must be my graphics card since i installed ubuntu 11.10 on my uncle's old dell laptop and no problem. it seems these bugs arise in newer hardware. thanks again

---

### Post by IWantFroyo on 2011-11-25
Very true. It took me several weeks to get Ubuntu 10.10 running on my new (at the time) Toshiba laptop. Same issue you had.

Sadly, the close-the-lid-test fails on many laptops. You're not alone. It makes it almost impossible if your acpi is off. I think there are other power managers in the repositories, so I would encourage you to try those. You may have more luck.

Usually you see something different when graphics go wrong. Are you sure it isn't the acpi elves causing trouble? You have to either keep editing the GRUB menu for acpi=off, or do the trick I posted above.

---

### Post by Raul1800 on 2011-11-25
dam that sux, cuz in a laptop closing the lid is really importat, to protect the screen or carry the laptop around. its a shame since ubuntu really would be the best os if it wasn't for the bugs and lack of software compatibility, itunes and others i tried different alternatives and even wine but it's just not as smooth. and probably what hurts the most is how hard it is to fix even a minor bug like mine. most ppl are lazy and don't have time to spend hours and hours tryin to fix a bug so just prefer to stick wit win or osx. anyway i hope by the next release these bugs will be gone, then i'll switch. i think what's funny about these bugs is the fact that (on my laptop) they didn't exist in previous builds, like 10.04 and 10.10. so insted of going forward we took a stepback, sad since 11.10 is soooooooo pretty lol

---

### Post by MAFoElffen on 2011-11-26
> **Raul1800 said:**
> dam that sux, cuz in a laptop closing the lid is really importat, to protect the screen or carry the laptop around. its a shame since ubuntu really would be the best os if it wasn't for the bugs and lack of software compatibility, itunes and others i tried different alternatives and even wine but it's just not as smooth. and probably what hurts the most is how hard it is to fix even a minor bug like mine. most ppl are lazy and don't have time to spend hours and hours tryin to fix a bug so just prefer to stick wit win or osx. anyway i hope by the next release these bugs will be gone, then i'll switch. i think what's funny about these bugs is the fact that (on my laptop) they didn't exist in previous builds, like 10.04 and 10.10. so insted of going forward we took a stepback, sad since 11.10 is soooooooo pretty lol
You misunderstood what he was saying- Closing a laptop lid should put a laptop Operating System into hibernation.  Laptops do actually have magnetic sensors in the case that sense the lid closing.

Oneiric has a few bugs with suspend and hibernation on some laptops, as other earlier versions sporadically did. New hardware and new code... It'll catch up.

Not to say that Win OS'es don't have bugs... They have their fair share also.

---

### Post by Raul1800 on 2011-11-26
> **MAFoElffen said:**
> You misunderstood what he was saying- Closing a laptop lid should put a laptop Operating System into hibernation.  Laptops do actually have magnetic sensors in the case that sense the lid closing.

Oneiric has a few bugs with suspend and hibernation on some laptops, as other earlier versions sporadically did. New hardware and new code... It'll catch up.

Not to say that Win OS'es don't have bugs... They have their fair share also.

sorry if i misunderstood him. but i changed the settings so that when i close the lid it sleep/suspend not hibernate. btw if it placed my laptop to hibernate it means it would shut down but when i open the lid i can see the background but only if i place a flash light directly on the screen so i know thats its on and running. i know that win has bugs but on this laptop it works flawlesly with no bugs yet. i really hope ubuntu can get these bugs resolved since i really like the ubuntu interface, its speed, reliability, and helpful community hope that on 12.04 release next year will be bug free for my laptop and many others.:guitar:

---

### Post by a271828 on 2011-12-18
> **Raul1800 said:**
> hope that on 12.04 release next year will be bug free for my laptop and many others.
I would like to hope also... Could this really happen???

I had issues with every upgrade with Desktop edition (started with 9.04). Most issues I had (and still have) with my laptop (used from 10.04). Those issues did not prevent me from using the system yet...  but I would prefer a MORE STABLE distribution. I could write a long list of issues starting with small (WHY THE UI APPEARANCE HAS CHANGED) ... till WHY THIS SOFT IS NOT WORKING ANYMORE???
Waisted hours of getting things to work again!!!

Worst of all is that users have this PAIN EVERY 6 MONTHS!!!

Taking in consideration all issues with EVERY RELEASE I am unable to understand the reasons for so frequent releases!!!

---

### Post by oldos2er on 2011-12-18
Moved to Ubuntu Testimonials & Experiences

---

### Post by Tamlynmac on 2011-12-18
> a271828
Worst of all is that users have this PAIN EVERY 6 MONTHS!!!

That is not a totally true statement. Users can choose to install the newest release every six months, but it's not mandatory. I've rarely used anything but LTS's, since first installing Ubuntu (7.04). New users may download the latest release, but that still doesn't mandate they must install every release.

As for 6 month release policy, that issue has been questioned many times (in this section of the forums and elsewhere) with no impact. I seriously doubt it will be altered anytime in the near future.

---

### Post by philinux on 2011-12-18
Thanks for all the contributions.

Thread closed.

---

