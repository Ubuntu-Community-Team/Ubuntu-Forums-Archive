---
title: "How to enable &quot;Autostart Applications&quot; to run again all disabled in last session"
date: 2017-11-16
forum: Ubuntu/Debian BASED
---

### Post by annismonadjem on 2017-11-16
Hi,

In an attempt to optimize the speed of restarting pc I've disabled all autostart default applications. Now i don't have access to any app including Terminal (Terminator etc). Long ago i had removed the startup button to save on my screen real estate. 

Now, i have been struggling with no success to launch Terminal. 

My os system is based on Ubuntu 16.04 (Peppermint 7). I've also posted same on peppermintos.net (with little success as of now).

I've a backup of pc settings using Aptik. So not coming up with any solutions I decided to reinstall Peppermint 7 (Ubuntu 16.04) from original DVD and next to recover Aptik (pc settings and updates/upgrades). 

To my complete surprise, after restarting my pc - i still have no access to any of my earlier created os shortcuts. 

**_Question:_** 
1) How is it possible to start Terminal under such circumstances (again no start menu button and the Ctrl-Alt-t, window-s or any other shortcut keys are not responding)?
2) How to enable autostart default applications not having a startup menu and not having access to Terminal?

Please help.

---

### Post by deadflowr on 2017-11-16
*Thread moved to** Ubuntu/Debian BASED***

---

### Post by again? on 2017-11-16
How did you disable autostart applications?
If you just used the Gui as a normal user you could probably just rename your ~/.config/autostart directory.
At the greeter hit ctrl+alt+F1 to open a TTY console.
Login then rename ~/.config/autostart
```
mv ~/.config/autostart ~/.config/autostart.bak
```
Then hit ctrl+alt+F7 and login as normal. (try  ctrl+alt with F2-F8 if doesn't work).

If you can't login to a TTY console, try recovery mode as shown in the first part of this howto.
[http://psychocats.net/ubuntu/resetpassword](http://psychocats.net/ubuntu/resetpassword)

Could also use a live usb to edit any necessary files.

---

