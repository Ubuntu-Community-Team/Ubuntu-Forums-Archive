---
title: "Problem with WOW"
date: 2009-04-26
forum: Wine
---

### Post by benster0080 on 2009-04-26
So I installed regular WoW and decided that the patch time would take to long and decided to just go ahead and buy BC and WOTLK. I installed WOTLK and updated to the current release. Now when I click on the WoW desktop icon it launches old WoW and tries to patch up to 3.0 but when I run terminal as root I am able to drag and drop the installer.exe file into the terminal and run it from that. 

So it appears that I have two versions of WoW installed onto my computer. But in the wine file browser there is only one World of Warcraft folder.

When I try to play WOTLK it crashes almost instantly. No error message at all just an exit of the game and a return to the desktop. 

I have went into my config.wtf and added the stuff for opengl and all that to no avail. 

So basically my question is how do I get rid of the older version and how do I get the newer version to work?

---

### Post by NightMKoder on 2009-04-26
Never (EVER!) run wine as root. Wine doesn't need root access, and in fact many things won't work. This is one of them - you have two wine installations - one for the root user, and one for your user.

```

sudo rm -Rf ~/.wine
sudo rm -Rf /root/.wine

```
Clean your menu, and reinstall.

---

### Post by benster0080 on 2009-04-26
Ok I did that now i have a new problem. When I try to copy the files form the wow cd to a folder to install it it tells me. "The folder "DirectX" cannot be handled because you do not have permissions to read it." and i noticed that all the files have x'ed out boxes in the upper right corner of them. How do i get permission? I am the root user.

---

