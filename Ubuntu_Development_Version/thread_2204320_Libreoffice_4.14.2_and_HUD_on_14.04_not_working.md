---
title: "Libreoffice 4.1/4.2 and HUD on 14.04 not working"
date: 2014-02-07
forum: Ubuntu Development Version
---

### Post by prana on 2014-02-07
I wanted to confirm a bug with using the HUD (Left Alt key by default) and Libreoffice 4.1/4.2 on a fully updated 14.04 install.

If I  press Left Alt to bring up the HUD and type in anything that will bring up the appropriate Libreoffice menu and click it - nothing happens.

For example, if I bring up the HUD and type "About", it brings up the "about libreoffice" menu item but nothing happens when I click it.

I tried the HUD with Firefox and it works fine. I also clicked on the global menu for Libreoffice and clicking any menu item through that process is also successful.

Thanks

---

### Post by grahammechanical on 2014-02-08
It works for me. It will even present the name of a recently opened document if I get the name spelled right and it will open it. The HUD seems to be more useful now than when it first came out. I will have to use it more.

Regards.

---

### Post by Mateusz Stachowski on 2014-02-08
It doesn't work for me in LibreOffice (none of the menus) and I have also problems in Geany.

I use HUD in Geany for changing encoding to UTF-8 because it's faster than making your way through all those menus but recently it stopped working. I can still for example open recent documents or bring the about dialog but changing encoding doesn't work.

---

### Post by prana on 2014-02-08
So the behavior is not very consistent.

@graham, was wondering if you used hud or dash to open the recent document.

I may just create a bug report for Libreoffice and HUD though I am not sure which package is affected by this.

---

### Post by grahammechanical on 2014-02-08
I was trying to replicate your problem, so I was using the HUD. I can open the HUD and scroll down to Open ... (File) and by pressing Enter it will open the Libreoffice file open dialog. Clicking the menu line also works. When typing in a file name of a recently used document it will find that document and pressing Enter will open it. Seems to work as it should.

---

### Post by Mateusz Stachowski on 2014-02-09
Today I've tried using HUD from daily live image of Trusty and again I couldn't open any of LibreOffice menus.

---

### Post by prana on 2014-02-10
So it seems there was an old bug report that said that people with ATI cards running the Gallium 3D driver were affected by this bug and it so happens, I have an x1600 ATI card on my laptop and the display dialog box shows up with the 0.4 version of the Gallium driver.

---

### Post by Mateusz Stachowski on 2014-02-11
I on the other hand have GeForce 9600 GT. This is running in my normal install on NVIDIA drivers and in Live CD on Nouveau.

---

### Post by prana on 2014-02-11
Interesting, so we are back to square one. HUD is tailor made for the complex Libreoffice menus so it is a shame that it is not usable on my laptop. Alt (hold) doesn't work either so my only choice is to use the mouse to navigate menus which breaks my workflow. I haven't actually reinstalled 14.04 but based on your experience, the reinstall may be in vain.

---

### Post by Mac Boy on 2014-02-27
I can confirm that I have the same inability to use the HUD with LibreOffice, it had just started playing nice on 13.10 before I upgraded to 14.04.  Pressing Alt brings up the menus as the HUD should work but nothing happens when you hit enter.  I think the last time it was to do with the Nvidia driver, which I then updated on 13.10 but it has since updated again on installation of 14.04 - maybe on the next version of the Nvidia driver it will work again.

---

### Post by estamets on 2014-03-03
HUD is not working for me either in Libreoffice 4.2 in 14.04. I am not sold on the idea that Nvidia drivers are the culprit. I run straight Intel graphics on a stock lenovo box. I can get hud to appear correctly, I just can't execute anything. I guess I'll wait until April to see if it's fixed by then.

---

### Post by justoneslave on 2014-03-04
Same problem here on an Intel laptop. This one seems to be the Bug:
[https://bugs.launchpad.net/ubuntu/+source/hud/+bug/1278720](https://bugs.launchpad.net/ubuntu/+source/hud/+bug/1278720)
Please give it some attention, I really hope this is going to be fixed until release. HUD makes so much sense in Libreoffice.

---

### Post by Mateusz Stachowski on 2014-03-20
This is fixed now with recent updates.

[https://bugs.launchpad.net/ubuntu/+source/evince/+bug/1288025](https://bugs.launchpad.net/ubuntu/+source/evince/+bug/1288025)

[https://bugs.launchpad.net/ubuntu/+source/hud/+bug/1278720](https://bugs.launchpad.net/ubuntu/+source/hud/+bug/1278720)

---

