---
title: "EVE Online client freezing on Ubuntu 11.04 via Wine"
date: 2011-06-05
forum: Wine
---

### Post by Tornikee on 2011-06-05
Hello.

I installed EVE on Ubuntu 11.04 according to [[this]("http://danielj.se/2010/11/14/how-to-install-eve-online-in-ubuntu-10-10/")] link, successfully logged in, but the client freezes seconds after I log in. Any hints?

Also, I installed EVE in my home directory in Ubuntu, could this cause any problems? Where should I have installed it?

---

### Post by Narkolas on 2011-06-19
I have the exact same problem.

Running Nvidia 8800GT with recomended propriotary drivers for ubuntu (new install)

Did you find a solution?

---

### Post by MourningWood on 2011-09-17
Same problem same card here too clean install

---

### Post by Narkolas on 2011-09-19
> **MourningWood said:**
> Same problem same card here too clean install

I Actualy manage to fix it back then, i have change to ATI these days, but as i recall it was quite simple fix.

Something like disable hdr or shadows or something like that in the Eve Client.

Sorry i can't be more specifik, but try disabling all the smart stuff and see if that solves it, then start enableing one by one.

Hope it helped.

---

### Post by ergo-proxy on 2011-09-20
> **Tornikee said:**
> Hello.
 
I installed EVE on Ubuntu 11.04 according to [[this]("http://danielj.se/2010/11/14/how-to-install-eve-online-in-ubuntu-10-10/")] link, successfully logged in, but the client freezes seconds after I log in. Any hints?
 
Also, I installed EVE in my home directory in Ubuntu, could this cause any problems? Where should I have installed it?
 
It doesn't matter where it's installed just make sure you have updated propietary drivers then
 
winetricks corefonts, d3dx9_43, vcrun2005

after the installation EVE will crash but no worries it's "intended" ;)

and finally start the games :) EVE works really fine on Ubuntu.

---

