---
title: "Virtualbox Lubuntu boots to a black screen- please help"
date: 2020-09-14
forum: Virtualisation
---

### Post by adi50 on 2020-09-14
I was using my Lubuntu 20.04 virtualbox guest OS just this morning and it was running fine. I attempted to install an update, I remember it said there was some error with installing it but I can't recall exactly what it said. 


I then rebooted the OS, it opens to the password screen for LUKS, then I can see the Lubuntu logo loading for a few seconds, then it goes to a black screen and all I can see is the cursor on the screen. I tried rebooting the OS 20 times, rebooting my laptop, increasing the video memory of the guest, and even exported the OVA, importing again, but nothing seems to work.

What might the problem be and how can I go about fixing it?

---

### Post by ameinild on 2020-09-14
> **adi50 said:**
> I attempted to install an update, I remember it said there was some error with installing it but I can't recall exactly what it said.

What were you trying to update - kernel perhaps? For future troubleshooting, it would be extremely helpful if you had the error message, since people's ability to help you is drastically reduced when not knowing what the error was.

Can you enter the GRUB menu and choose a different kernel, or boot into recovery mode?

---

### Post by adi50 on 2020-09-14
OK I was able to get to the menu to boot into recovery mode or into an old kernel. I tried booting into an old kernel with no success, same black screen. Booting into recovery mode- I can get to the list of options- resume, clean, dpkg, etc. Upon pressing resume it just takes me to the black screen again. I don't know what I should do with the other options if that is where there solution lies, any further advice?

---

### Post by &amp;KyT$0P# on 2020-09-14
> **adi50 said:**
> OK I was able to get to the menu to boot 

Any useful information if you boot latest kernel **without** [FONT=Courier New]quiet splash[/FONT] parameters?

---

