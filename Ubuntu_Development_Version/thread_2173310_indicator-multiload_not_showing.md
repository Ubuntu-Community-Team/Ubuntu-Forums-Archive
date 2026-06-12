---
title: "indicator-multiload not showing"
date: 2013-09-09
forum: Ubuntu Development Version
---

### Post by miobrad on 2013-09-09
dear forum,
i have installed indicator-multiload,  my cpu/load monitor of choice. after installation i have started it manually and i have also checked that it is in startup applications - it is. 

when i look for the process.. 

ps ax  | grep indicator
1506 ?        Sl     6:57 indicator-multiload

.. i see that it is loaded/running, yet i do not see it in the panel.

maybe a bug? thanks for any ideas of how to get it to show, or else, maybe this helps the developers to fix a bug?
anyways - thanks for all the work/support!

---

### Post by grahammechanical on 2013-09-09
I have an install of Saucy that did not have System Load Indicator (indicator-multiload) installed. So, as a test I have just installed it and after loading from the Dash it at once appeared in the top panel and then after a restart it also appeared in the top panel. So, I do not have this problem. Are you using Unity? Are you using a default theme? I have no idea if any of these things can cause this. Oh, by the way this install is running on xmir and not the xserver and yet I do not have the problem.

Regards.

---

### Post by miobrad on 2013-09-09
i just downloaded the beta yesterday and did a clean install. after that i updated all the packages via sudo apt-get update/upgrade.. so, all standard. 
as for mir - i don't know it, so i'm not sure if by default it was installed or not.. ? thank you for the reply!

---

