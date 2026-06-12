---
title: "Ubuntu 13.04 won't work after logging in"
date: 2013-04-23
forum: Ubuntu Development Version
---

### Post by mike984 on 2013-04-23
I have tried installing 13.04 a couple times in the last 20 days using daily builds and today I tried again using update manager -d.  Each time (except this last time), I have chosen a complete new install wiping the hard disk clean.  Each time, I have the same results.  After installing 13.04, I am asked to reboot and when I do, I get no errors and I get the login screen.  Everything on that screen looks fine.  When I enter my password,the desktop opens, I see no top panel and I do see the unity icons.  However, nothing works.  Anything I click on does nothing, I can't even draw a box on the screen with the mouse, I cannot do Alt-f2, I cannot do a ctrl-alt-f1, and with a few minutes of clicking around or trying to get something to come up, the mouse will eventually disappear.  I always have to hard boot and when it boots up, I can do a ctrl-alt-f1 at the login screen and I am able to sign in and use the CLI.  I've been using Ubuntu since Warthog on this computer and have never had a problem.

It's a home built pc with nvidia geforce 8800, 8GB memory.  Nothing fancy or new in the computer.  

I'm not a total newbie and not afraid of using the CLI but I don't know what to check or do and I've googled this extensively and I don't see anyone else having this problem.  I have also tried it on a new hp dv6t 7300 laptop (no SSD) and got similar response on it.  They both have nVidia video cards but both are using nouvo.  

I would like to open a bug report but not sure what I need to include like log files.

---

### Post by dino99 on 2013-04-24
When you get the login screen (the greeter), you can choose the DE (aka ubuntu (unity), gnome (gnome-shell), gnome-classic (gnome-shell without compiz)). So do you experience your issue if all those choices ?
At that time you should be able to open a terminal (ctrl+alt+t) or switch to tty and reset compiz/unity:

compiz --replace ccp &
setsid unity

The other way is to boot on recovery mode, enble the network, and repair the packages (in case of ), then try to find something usefull into the logs.

about the graphic driver: nvidia-313-updates should be the best choice

---

