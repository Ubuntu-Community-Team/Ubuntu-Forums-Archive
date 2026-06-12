---
title: "Installing Ubuntu Server on a VIA EPIA CPU"
date: 2010-02-07
forum: Server Platforms
---

### Post by Iker Etxebarria on 2010-02-07
Hi

I am trying to install Ubuntu Sever 9.10 on an VIA EPIA based CPU. It has a display probem because when I start the installation, after selecting the language and starts in text mode based windows, the video gets crazy and the display is filled by a lot of strange colors and can not see the installer questions.

Does anybody have the same problem? I tried with different boot options but the problem continues. How can I solve it?

Thanks for your attention.

---

### Post by Flibblebot on 2010-02-15
After you select the install language, press Escape to go into the text mode installer.

Press Tab at the "Install Ubuntu" line, add
```
fb=false
```
to the end of the command line and press Enter.

Install should continue in text mode.

---

### Post by Iker Etxebarria on 2010-02-16
Thank you very much. With that option the installation works fine.:D
Thanks again.

---

### Post by simonf on 2010-04-28
Thanks, this sounds like good news. I have my music on a TranquilPC T7 with a VIA EPIA M cpu. I have generally installed Desktops up to now because of the server kernel issue with VIA cpus, but it sounds like 10.4 Server might be OK. I will try it this weekend.
I have also had video problems with this machine - you can tell what is supposed to be on the screen but the image is divided up into what I can only describe as narrow horizontal bands in which the pixels are pushed into almost horizontal diagonals.
I will try the tip above and post back.
This machine will be headless and attached to a wall in the basement - (squeezebox server).
If I can get 10.4 Server running on it, hopefully it should run even more economically (not that it runs hot now!) and I can forget it for a few years!
I'll post back next week.

Simon

---

### Post by zion2k on 2010-08-06
Hi,

I am using an Epia M 10000 and still in trouble. If I try to install any version (Desktop, Alternative, Server) in text mode or change to console I still have these twisted grafics.
Even if I use the "fb=false" boot option. Is it right to hit F6 at the menu and add it there?

Any other tips how I can get Ubuntu 10 runing on my Epia M?

regards
zion2k

---

