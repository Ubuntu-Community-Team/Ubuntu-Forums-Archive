---
title: "Brand-New Leopard Extreme No Longer Boots"
date: 2012-08-03
forum: System76 Support
---

### Post by Dan Wiebe on 2012-08-03
After a very positive experience with a System76 Bonobo laptop, I purchased a Leopard Extreme desktop, which arrived yesterday. I hooked it up and everything worked great.
 
Then I ran all the pending updates, installed the NVidia hardware-specific video driver, performed the recommended restart, and everything went to pieces.
 
When I boot the machine from the installed hard drive, after the BIOS sequence, I get a screen that looks like Exhibit A, attached. (Occasionally, that screen serves as background for a grub menu; I haven't been able to predictably affect when the grub menu shows up and when it doesn't.) After maybe fifteen seconds of that, I get a solid-magenta background (I don't mean the nicely-graduated standard Ubuntu desktop, I mean solid #FF00FF from corner to corner) with nothing but a movable mouse cursor on it, like Exhibit B, attached. Once this magenta screen comes up, the keyboard is dead: there are no lights lit on it, and the lights don't respond to the various LOCK keys. This screen stays like that seemingly forever, but at least for twenty minutes. In case it matters, when this happens, the motherboard POST display shows 6C.
 
That's the closest to an actual boot I can get.
 
I've also tried booting it with a Precise installation USB stick, with a Precise installation CD-R, and with an Oneiric installation CD-R. With all of those, I can get to the initial Try Ubuntu/Install Ubuntu/Check disc/Check memory/etc menu, but if I do anything but Check memory (which works just fine and finds no issues), the system eventually freezes.
 
Booting with the Precise installation media eventually wedges the system with the screen black and a flashing text-mode cursor in the upper left. (I didn't photograph that, because it's not interesting.) Anything I do with the keyboard or mouse is ignored.
 
Booting with the Oneiric installation CD freezes at the point in the boot process where the screen looks like Exhibit C. If I type at this point, what I type appears on the screen, but the system otherwise ignores it. The motherboard POST display shows Fb.
 
Note the corrupted characters: that's a pretty common feature. When I get the grub menu, it's corrupted in the same general sort of way; when I start recovery mode, the menu there is corrupted; when I drop to a root command prompt, the prompt, my commands, and the system's responses are corrupted like that too.
 
A further moderately interesting feature is that even the BIOS Setup menu looks a little moth-eaten; see Exhibit D. I'm pretty sure this couldn't possibly have anything to do with the installation of the NVidia video driver; but I haven't seen anything like it before.
 
Can anyone help?
 
Thanks,
Dan Wiebe

---

### Post by isantop on 2012-08-03
> **Dan Wiebe said:**
> After a very positive experience with a System76 Bonobo laptop, I purchased a Leopard Extreme desktop, which arrived yesterday. I hooked it up and everything worked great.
 
Then I ran all the pending updates, installed the NVidia hardware-specific video driver, performed the recommended restart, and everything went to pieces.
 
When I boot the machine from the installed hard drive, after the BIOS sequence, I get a screen that looks like Exhibit A, attached. (Occasionally, that screen serves as background for a grub menu; I haven't been able to predictably affect when the grub menu shows up and when it doesn't.) After maybe fifteen seconds of that, I get a solid-magenta background (I don't mean the nicely-graduated standard Ubuntu desktop, I mean solid #FF00FF from corner to corner) with nothing but a movable mouse cursor on it, like Exhibit B, attached. Once this magenta screen comes up, the keyboard is dead: there are no lights lit on it, and the lights don't respond to the various LOCK keys. This screen stays like that seemingly forever, but at least for twenty minutes. In case it matters, when this happens, the motherboard POST display shows 6C.
 
That's the closest to an actual boot I can get.
 
I've also tried booting it with a Precise installation USB stick, with a Precise installation CD-R, and with an Oneiric installation CD-R. With all of those, I can get to the initial Try Ubuntu/Install Ubuntu/Check disc/Check memory/etc menu, but if I do anything but Check memory (which works just fine and finds no issues), the system eventually freezes.
 
Booting with the Precise installation media eventually wedges the system with the screen black and a flashing text-mode cursor in the upper left. (I didn't photograph that, because it's not interesting.) Anything I do with the keyboard or mouse is ignored.
 
Booting with the Oneiric installation CD freezes at the point in the boot process where the screen looks like Exhibit C. If I type at this point, what I type appears on the screen, but the system otherwise ignores it. The motherboard POST display shows Fb.
 
Note the corrupted characters: that's a pretty common feature. When I get the grub menu, it's corrupted in the same general sort of way; when I start recovery mode, the menu there is corrupted; when I drop to a root command prompt, the prompt, my commands, and the system's responses are corrupted like that too.
 
A further moderately interesting feature is that even the BIOS Setup menu looks a little moth-eaten; see Exhibit D. I'm pretty sure this couldn't possibly have anything to do with the installation of the NVidia video driver; but I haven't seen anything like it before.
 
Can anyone help?
 
Thanks,
Dan Wiebe

Ensure that you have a good, solid connection between the monitor and the graphics card. Also try replacing the cable you're using, as a bad cable would cause that too. You might also pop the side off of the system and make sure that the graphics card is well seated in its slot, as it may have been jostled loose during shipping.

---

### Post by Dan Wiebe on 2012-08-03
Cable's fine, or at least it was with the Dell the Leopard replaced.  The DVI connector on the card might be a little dodgy, I suppose, but that's not going to cause the sort of character corruption I saw. I hadn't thought about reseating the card, though--that's a great idea.  I'll try that.
 
But even a certifiably insane video card doesn't seem as though it ought to be able to produce the sort of boot failures I'm seeing.  How does a bad video card make a boot from an installation disc hang in the middle, but in such a way that the screen still shows you what you type?
 
Thanks for your response.

---

### Post by isantop on 2012-08-03
> **Dan Wiebe said:**
> installed the NVidia hardware-specific video driver

This concerns me a bit. When you installed the driver, do you mean to say you downloaded one from Nvidia.com? The latest Ubuntu-provided driver should have been pre-installed on your system. 
 
> **Dan Wiebe said:**
> I've also tried booting it with a Precise installation USB stick, with a Precise installation CD-R, and with an Oneiric installation CD-R. With all of those, I can get to the initial Try Ubuntu/Install Ubuntu/Check disc/Check memory/etc menu, but if I do anything but Check memory (which works just fine and finds no issues), the system eventually freezes.
 
Booting with the Precise installation media eventually wedges the system with the screen black and a flashing text-mode cursor in the upper left. (I didn't photograph that, because it's not interesting.) Anything I do with the keyboard or mouse is ignored.

This is actually caused by the fact that your graphics card is too new and too powerful. From the installation CD, you'll need to disable mode-setting by hitting a key at the initial purple screen, then choosing a language, then hitting F6 and ticking "nomodeset", then booting the CD. This will get it up and running. If you want to do a reinstallation, then the instrucitons for that are available [Here.](http://knowledge76.com/index.php/Restoring_Your_System)

As for the connection, you mentioned that the DVI connector on your cable may be a bit dodgy. That could definitely cause the sort of graphics corruption you're seeing (particularly that in the first and fourth pictures). I would try it with a different cable, if at all possible.

---

### Post by Dan Wiebe on 2012-08-04
> **isantop said:**
> This concerns me a bit. When you installed the driver, do you mean to say you downloaded one from Nvidia.com? The latest Ubuntu-provided driver should have been pre-installed on your system. 
I brought up the Additional Drivers part of System Settings, and it said the NVidia driver was inactive.  I activated it, and got a couple of progress bars that looked like network access; that's why I said "downloaded."
 
> This is actually caused by the fact that your graphics card is too new and too powerful. From the installation CD, you'll need to disable mode-setting by hitting a key at the initial purple screen, then choosing a language, then hitting F6 and ticking "nomodeset", then booting the CD. This will get it up and running.
Worked very nicely--mostly--thanks.  I'm still having the occasional glitchy temporary freeze (that is, the monitor will develop a sudden case of magenta chickenpox and the computer will become completely unresponsive for twenty seconds to a minute, then the chickenpox disappear and the machine responds again), but the frequency of it seems to be declining.

> As for the connection, you mentioned that the DVI connector on your cable may be a bit dodgy. That could definitely cause the sort of graphics corruption you're seeing (particularly that in the first and fourth pictures). I would try it with a different cable, if at all possible.
Actually, I referenced the connector on the card, not the connector on the cable.  The cable has been doing a yeoman's job for several years now.  I tightened the retaining screws a little; I don't know whether that had an effect, but it seems to be working now.

Thanks much for your help.  I appreciate it.

---

### Post by isantop on 2012-08-06
> **Dan Wiebe said:**
> I brought up the Additional Drivers part of System Settings, and it said the NVidia driver was inactive.  I activated it, and got a couple of progress bars that looked like network access; that's why I said "downloaded."
 

Worked very nicely--mostly--thanks.  I'm still having the occasional glitchy temporary freeze (that is, the monitor will develop a sudden case of magenta chickenpox and the computer will become completely unresponsive for twenty seconds to a minute, then the chickenpox disappear and the machine responds again), but the frequency of it seems to be declining.


Actually, I referenced the connector on the card, not the connector on the cable.  The cable has been doing a yeoman's job for several years now.  I tightened the retaining screws a little; I don't know whether that had an effect, but it seems to be working now.

Thanks much for your help.  I appreciate it.

Sounds good. Let me know if there are any other problems, and sorry for any misunderstanding on my part above. You might still ensure the card is seated in the PCI slot well, as that could be causing the pink graphics artifacts.

---

### Post by Dan Wiebe on 2012-08-06
> **isantop said:**
> Sounds good. Let me know if there are any other problems, and sorry for any misunderstanding on my part above. You might still ensure the card is seated in the PCI slot well, as that could be causing the pink graphics artifacts.
 Thanks again.  Now I just have to get hold of enough of those weird disk-mounting screws to mount two or three old disk drives in the case, and I can close it up and forget about it.

---

