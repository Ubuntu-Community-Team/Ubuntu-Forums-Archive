---
title: "trouble running world of warcraft under virtualbox"
date: 2009-03-03
forum: Virtualisation
---

### Post by Arminius on 2009-03-03
hi, I'm running ubuntu as my main operating system, and using virtualbox I'm running windows xp home as a guest operating system, within that I have installed world of warcraft, but it keeps saying "failed to find a suitable display device"

under display property's under the settings tab it says default moniter is the display
so it doesn't actually list my Eizo moniter, and I don't know how to make it.
I tried to install my video cards drivers on the guest OS but it wouldn't let me, so what do I do now?

---

### Post by NikoC on 2009-03-04
Hmmz I'm not really that much of a gamer, but I think VirtualBox does not support 3D... yet!

---

### Post by Dedoimedo on 2009-03-04
3D support in virtual machines is slightly limited yet.

However:

Did you install guest additions?
Did you enable 3D support?

Did you try this:
[http://www.dedoimedo.com/computers/virtualbox-guest-addons.html](http://www.dedoimedo.com/computers/virtualbox-guest-addons.html)
[http://www.dedoimedo.com/computers/virtualization-3d-support-virtualbox.html](http://www.dedoimedo.com/computers/virtualization-3d-support-virtualbox.html)

Dedoimedo

---

### Post by Arminius on 2009-03-04
nah at the time guest additions were not installed
but I have since installed them and the exact same error message remains
also increased video memory

display tab now reads "default moniter on virtualbox graphics adaptor"
if that helps

so does anyone play world of warcraft on virtualbox?

---

### Post by Arminius on 2009-03-04
well the tech over on the world of warcraft forum pretty much told me to get stuffed "we don't troubleshoot linux boxes"
OUTRAGEOUS!!!

so this forum is my only hope, anyone?

---

### Post by lot3k on 2009-03-05
> **Arminius said:**
> well the tech over on the world of warcraft forum pretty much told me to get stuffed "we don't troubleshoot linux boxes"
OUTRAGEOUS!!!

so this forum is my only hope, anyone?

If you honestly want to play WoW in linux, I would recommend using wine before virtual box.  I'm not even sure what it would take to get it to run stable inside VB, however under wine it will run really well and quite stable.

Now if you just abosultely have to play it under a VM session, you may be out of luck till advanced 3d accel is implemented.

---

### Post by Allwynd on 2009-08-26
[SIZE=2]i have tried running WoW on Ubuntu via Wine, it was back then when i had my old machine and ubuntu wouldnt detect my hardware (this time ubuntu fails cuz when i reach the install wizard the screen turns in lines and sometimes fades to black and i cant see a thing and install ubuntu 8.04 on my fujitsu siemens amilo li 3710) [/SIZE][SIZE=3][SIZE=2]without drivers i was also able to run it last summer, it was choppy, but it ran[/SIZE]
[/SIZE]

---

