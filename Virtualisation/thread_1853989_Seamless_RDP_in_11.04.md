---
title: "Seamless RDP in 11.04"
date: 2011-10-03
forum: Virtualisation
---

### Post by ataylor1988 on 2011-10-03
So i am having some issues with this and i am not sure why
i have followed the instructions here 
[http://ubuntuforums.org/showthread.php?t=433359&highlight=seamlessRDP](http://ubuntuforums.org/showthread.php?t=433359&highlight=seamlessRDP)
I did omit some of the registry key entries because i dont really care about the color and all that just need it to function

i try and test to make sure i can remote to the computer and it always errors out.  I am just running a basic rdesktop commmand
rdesktop <ip>:3389
says it autoselects the us keyboad then error cannot connect after some time

Anyone else had this issue

---

### Post by dcstar on 2011-10-07
> **ataylor1988 said:**
> So i am having some issues with this and i am not sure why
i have followed the instructions here 
[http://ubuntuforums.org/showthread.php?t=433359&highlight=seamlessRDP](http://ubuntuforums.org/showthread.php?t=433359&highlight=seamlessRDP)
I did omit some of the registry key entries because i dont really care about the color and all that just need it to function

i try and test to make sure i can remote to the computer and it always errors out.  I am just running a basic rdesktop commmand
rdesktop <ip>:3389
says it autoselects the us keyboad then error cannot connect after some time

Anyone else had this issue

The current Linux RDP clients do not support the higher encryption that Windows 7 and current Windows server platforms use by default.

Change the Remote settings on the systems you are trying to connect into to the less secure setting, or you may want to try the **remmina** package (I have just tried it and it seems to work really well - and it's **fast**!).

The remmina package is in the Ubuntu repositories from 10.04 onwards, or you can use the PPA for the latest version:

[http://remmina.sourceforge.net/downloads.shtml](http://remmina.sourceforge.net/downloads.shtml)

---

