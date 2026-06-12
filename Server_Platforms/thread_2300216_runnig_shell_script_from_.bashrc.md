---
title: "runnig shell script from .bashrc"
date: 2015-10-24
forum: Server Platforms
---

### Post by jimmyh1972 on 2015-10-24
Hello

I have a Ubuntu server & I installed xorg on it
I would like to run a bash script that will start the x server after login
how can I run the script from .bashrc?
I have the script on the user directory 
Thank's ahead
Jimmi

---

### Post by TheFu on 2015-10-24
Running the startup for X/Windows from ~/.bashrc is a not-so-great idea.  That script is run every time a terminal is opened, not just at a console window. 

I suspect the better answer is to install gdm, but I'm not positive.  I'm running **lightdm** here. Which DE or Window Manager have you installed? xorg by itself isn't very useful for controlling window placement, having borders, having a title, things like that.  For those, you need a window-manager, WM.

---

