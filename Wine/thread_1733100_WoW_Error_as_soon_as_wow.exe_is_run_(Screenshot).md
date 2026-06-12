---
title: "WoW Error as soon as wow.exe is run (Screenshot)"
date: 2011-04-18
forum: Wine
---

### Post by 0perator on 2011-04-18
Hey, I've followed the instructions on the wowpeida, and wowwiki sites, and also am running the latest version of wine.

I am also invoking WoW.exe with the -openGL flag, and the Config.wtf file has been modified to use openGL.

I have also installed the package: nvidia-glx-185.

I have attached a screenshot of my problem, hopefully you'll be able to help :)

Thanks, opr.

---

### Post by cwwilson721 on 2011-04-19
Erm....

What hardware?

And why such an OLD driver? Newest Nvidia driver (installed from Ubuntu) is 270.41.03 (System > Additional Drivers   'current')

Try that first. And fill in some details (hardware, versions (wine & Ubuntu))

Also, the flag is "-open[COLOR="RoyalBlue"]gl[/COLOR]', NOT '-open[COLOR="Red"]GL[/COLOR]'. In Linux, it makes a difference.

Also, if you post the actual results from the terminal, and not a hard-to read screenshot

---

### Post by 0perator on 2011-04-19
aha, it was a problem with the drivers, i just updated to the "latest" ones in the additional drivers menu.

thanks for the help :)

---

