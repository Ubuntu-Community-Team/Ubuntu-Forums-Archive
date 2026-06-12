---
title: "None of the games I install open/run but when I had Xp before they did"
date: 2010-03-12
forum: Wine
---

### Post by Blindshot666 on 2010-03-12
I built the latest WINE from source version 1.1.40 and I install my games like WOW, Guild Wars, and Runes of Magic and they don't want to install. When I am trying to install them I get an error. the only one I managed to install is Guild Wars but it opens up a window of all black. IDK if it's my Graphics card or not because I managed to get the games to work on my cousins pc This is my Graphics card:Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
Someone plz help me I don't wanna feel bad about ubuntu because of this and I hate Windows

---

### Post by CoolMaxUK on 2010-03-12
Go to [www.winehq.org](www.winehq.org) and search the page for the game you wish to play. There will be a rating on the page of that game (ie Gold, Silver etc) which show how compatible that game is on WINE. 

Remember, this is an emulator, it will never run 100% like XP ;)

---

### Post by Villiam on 2010-03-12
At least there is a step-by-step guidelines howto for installing and playing World of Warcraft using Wine under Ubuntu.Check it out over here: [https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

---

### Post by Blindshot666 on 2010-03-12
See well I don't thin wine is the problem because I did check all these games out before I tried them. I also followed step-by-step guides on installing all of them, I also have Playonlinux installed. I recently downloaded the Crossover games trial to make sure that the installations are not the problems and I can open the games but they do not play or go to the login screen I always get errors or the applications just do not open

---

### Post by portets on 2010-03-12
do you have your ati or nvidia drivers properly installed?

---

### Post by asdfoo on 2010-03-13
> **portets said:**
> do you have your ati or nvidia drivers properly installed?


he said he has an intel card.

Intel does not have proper drivers for linux because they don't care about their customers.  You're better off going back to windows or buying a cheap nvidia card second hand.  GF8 or something.

---

### Post by Blindshot666 on 2010-03-13
Do any of u guys know how much the cheapest Nvidia card is?

---

### Post by hikaricore on 2010-03-13
[www.newegg.com](www.newegg.com)

---

### Post by Blindshot666 on 2010-03-29
Is there any kind of workaround for this? I am kinda broke and I really wanna play World Of Warcraft soon. I really appreciate the help

---

### Post by asdfoo on 2010-03-30
> **Blindshot666 said:**
> Is there any kind of workaround for this? I am kinda broke and I really wanna play World Of Warcraft soon. I really appreciate the help

Get a job to to pay for a $100 video card or go back to Windows.

Alternatively:

* convince Intel to write and release proper drivers, but have to wait for the time that this takes
* become the greatest programmer on earth and through divine intuition write your own video drivers for your Intel video card.

---

### Post by hikaricore on 2010-03-30
Actually it many cases it's more of a hardware limitation than anything with intel chipsets.
They have horrid opengl support so better drivers may not help much.

---

### Post by Blindshot666 on 2010-03-30
Thank you for the very useful and none sarcastic reply I will consider these things.

---

### Post by Blindshot666 on 2010-03-30
I am talking about asdfoo

---

### Post by asdfoo on 2010-03-30
> **hikaricore said:**
> Actually it many cases it's more of a hardware limitation than anything with intel chipsets.
They have horrid opengl support so better drivers may not help much.


I've heard that even the windows drivers don't take full advantage of the hardware for some of the intel cards.

---

### Post by midknight2k on 2010-05-23
Hi all, with world of warcraft as long as it has bin installed on windows, you can just copy/move it to your home folder, then open a Terminal from the folder and type  wine '/World_of_Warcraft/Wow.exe' -opengl 

then all being well it should run, and of course if it don't just alt-tab to the terminal and press Ctrl+c

---

