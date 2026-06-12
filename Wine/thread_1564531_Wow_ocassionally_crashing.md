---
title: "Wow ocassionally crashing"
date: 2010-08-30
forum: Wine
---

### Post by sabenfox on 2010-08-30
Hello All,
 
Recently i installed Wow on ubuntu linux using the easy guide that was on the ubuntu forums. Occasionally however wow will lock up when i am first logging on. Everytime this occurs i'm forced to restart the computer.
 
I was wondering if there was a way to stop having to restart when this happens. I try alt-tab / super-tab / ctrl-alt delete, and i've also bound the terminal to ctrl-alt-end but nothing seems to be able to close wow, or to switch out of it....
 
Can anyone provide me with some ideas ?

---

### Post by akoskm on 2010-08-30
Hi!
What is your system configuration?
Have you installed the appropriate drivers for your video card?
Have you tried disabling desktop effects?
Do you see the login screen, is there any graphical garbage, corrupted textures, buttons?

---

### Post by Iowan on 2010-08-30
Moved to Wine subforum.

---

### Post by sabenfox on 2010-08-31
i have a athlon x2 dual core with 4 gigs of ram and a ati 4600 graphics card. 
I installed the graphics drivers like a week or two ago when it popped up asking me for the drivers, it automatically found them and installed them
 
i'll have to look to see what the dates are on the drivers. I havn't disabled desktop effects, and really wouldn't even like to consider that. I believe there should be a way to kill wow without having to restart my whole computer...given linux's flexibility
 
When wow crashes, the login screen stays up, and at the bottem of teh screen where the taskbar is i can see a regular mouse icon, and i click on the bottem right of the screen to switch desktops, but with no avail. but nothing looks corrupted per say, just stuck on that specific login screen

---

### Post by cwwilson721 on 2010-08-31
Well, if you DON'T disable Compiz, GOOD LUCK. It's easy: Install/use compiz-fusion-icon, and choose Metacity as windows manager.

You also have to use opengl if you want any type of decent framerate. Either edit WTF or add "-opengl" at end of command.

Do both of these, and let us know if it continues

---

### Post by akoskm on 2010-08-31
> **sabenfox said:**
> i have a athlon x2 dual core with 4 gigs of ram and a ati 4600 graphics card. 
I installed the graphics drivers like a week or two ago when it popped up asking me for the drivers, it automatically found them and installed them
 
i'll have to look to see what the dates are on the drivers. I havn't disabled desktop effects, and really wouldn't even like to consider that. I believe there should be a way to kill wow without having to restart my whole computer...given linux's flexibility
 
When wow crashes, the login screen stays up, and at the bottem of teh screen where the taskbar is i can see a regular mouse icon, and i click on the bottem right of the screen to switch desktops, but with no avail. but nothing looks corrupted per say, just stuck on that specific login screen

What is the output of
```

glxinfo | grep rendering

```?
Disabling the desktop effects may improve both framerate and stability.
Also, add the following line to your *.wine/drive_c/Program Files/World of Warcraft/WTF/Config.wtf* file:
```

SET gxAPI "OpenGL"

```.

---

