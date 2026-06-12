---
title: "[Virtualbox] USB working but no USB 2 (though enabled in settings)"
date: 2008-12-09
forum: Virtualisation
---

### Post by hachel on 2008-12-09
hi,
I installed virtualbox today, for the main reason that there is no appropriate itunes substitute (thats another topic). Anyway, WinXP and itunes installed fine, but it wouldn't recognize my Ipod.
When I clicked Settings for my XP Virtual Machine it told me that it couldn't find USB (can't remember the exact wordings). So I edited my fstab according to a how-to I found on the virtualbox homepage.
I then plugged in my ipod and enabled usb and usb 2 (EHCI) in the settingsmenu and added a filter for my ipod.
After that itunes recognized my ipod when I "mounted" it under "devices".

So far so good, Itunes wiped my ipod cause it was set to another databse and started copying back the ~3000 songs, only that it was doing so with what has to be usb 1 speed (i know there is no such thing as usb1 and usb2 speed, but it was about 400kbs).
For what itunes under a native windows used to take a couple of minutes, virtual-itunes now took 1,5 hours.

I plugged in my usbstick (had to set a filter again, is that necessary? wouldn't recoginze otherwise) to see if it was maybe the ipods fault but it also took 12 mins for 700 mb.

Does anybody know what might be the problem and how to fix it?

thanks in advance,

hachel

---

### Post by sadohert on 2009-01-04
Exact same story here.  Would love to hear the answer.

Stu

---

### Post by mark_vinton on 2009-01-04
hey i had this problem too.  i've been using banshee and it's worked pretty OK but i just bought a 32g ipod touch and NEEDED itunes so i installed virtualbox.  i don't know why, but if you open the settings for your VM and click on the advanced tab under general, and then click the box next to "enable IO APIC" it seems to really speed it up.  hope this helps.


mark

---

