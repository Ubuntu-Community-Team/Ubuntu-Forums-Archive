---
title: "Windows Boot Annoyance..."
date: 2007-04-25
forum: Windows
---

### Post by GSF1200S on 2007-04-25
Hey guys..

I got a question for Windows here.. My buddy is running windows XP (he doesnt have linux), and hes having a very annoying problem.

Whenever he boots up, after the BIOS goes away, a screen pops up asking him to choose between running windows XP and XP setup. If he leaves it alone, it will automatically try to boot the setup. This part Ive managed to fix within msconfig and startup options.. it will now go to Windows, but its adding 10 or so seconds to his boot time.

How would I go about eliminating this selection prompt and making it go straight to Windows? He says thats what it used to do, and then it started doing this. Ive already been through msconfig and the BIOS (Dell desktop by the way) and I havent figured anything out.

Could it be something in Windows' MBR? Maybe I could use some kind of boot loader CD to fix this?

---

### Post by phiphedog on 2007-04-25
You could try editing the boot.ini in the C:\ drive and wiping out the one you don't want.

---

### Post by Imsati on 2007-04-27
But as for the root of that problem. It seems as if your friend started to run a reinstall or upgrade and stopped mid-way through. I recall during some of my reinstalls having that option. Either that or perhaps he has an upgrade CD in the drive? Not all of them boot up by default.

--Jay

---

