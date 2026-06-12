---
title: "Ubuntu Temp. Disable GUI"
date: 2010-12-30
forum: Server Platforms
---

### Post by mechaflash on 2010-12-30
We are settings up Ubuntu as a print server, so we have installed Ubuntu  Server 10(.xx).  We also wanted to have the GUI for easier access to  editing common files/processes, and we did so by installing gnome  (apt-get install ubuntu-desktop). 

What we want to do is have the server boot into text only, and use the  GUI only when necessary via 'startx' command.  We don't want to edit the  runlevel scripts to make the runlevels work, as all of them run X if it  exists on the install.  

I've used sysv-rc-conf and rcconf and disabled the GDM services without  any luck.  

Possible/how to disable X at boot?
If yes will 'startx' command work to temporarily bring up the GUI?
If yes, is there a command to kill 'startx' to take it back to text mode  without rebooting?

OR

If there is an easier way to get a temporary GUI without 'apt-get  install ubuntu-desktop', 
What should I be looking for?
How to use it?

Thanks!

~Mecha

---

### Post by drave on 2010-12-30
[http://www.cyberciti.biz/faq/prevent-xorg-from-starting-in-linux/](http://www.cyberciti.biz/faq/prevent-xorg-from-starting-in-linux/)

thats 3 years old. does it still apply?

if for some reason you cant get rid of gdm, look at gdm.conf.
i cant remember the exact syntax but under the [servers] section you put "0=",(or something like that) and then it will not start the local server (ie. no gui).

---

