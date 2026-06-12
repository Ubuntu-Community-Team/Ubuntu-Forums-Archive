---
title: "boot problems"
date: 2008-05-27
forum: Server Platforms
---

### Post by Captain666 on 2008-05-27
Fist i am going to start off by saying that i am completely new to Linux Ubuntu.. well Linux in general. I am attempting to dual boot Ubuntu with Vista. The install and everything of Ubuntu went smooth but the first time i went to boot into Ubuntu from GRUB i was brought to a black screen, where i seen lots of work going on (lots of "OK"s on the right side of the screen), then  it asks me to sign in (in the black screen), but after that it just gives me a blinking line and doesn't load into the OS (or to the desktop..). I've tried to use the help command and all that but nothing is happening. Im not sure if i need to install anything, or type some command.. anyone know anything about this.. or what im talking about???

---

### Post by Titan8990 on 2008-05-27
Is it nothing more than a blinking cursor or does it look more like this:

myusername@mycomputername# 

If it looks like the above then you just need to install the GUI which does not install by default with the server version. To do this you simply type:

# sudo apt-get install ubuntu-desktop

---

### Post by NateMan on 2008-05-27
Did you mean to dual boot a server os? Why not try reinstalling with the desktop alt cd?

---

### Post by khelben1979 on 2008-05-27
Maybe [this guide]("http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm") can help you?

And you can have a look at [this video]("http://www.youtube.com/watch?v=-opSR3YM8KQ") too. I found it on YouTube.

---

### Post by Captain666 on 2008-05-27
Thanks alot guys, i figured that i was just missing a step and it was: 

# sudo apt-get install ubuntu-desktop (lol noob)

I never would have guessed that you have to install the desktop.. but it makes sense. 
After i did that everything installed and what not properly and i am actually on Ubuntu now for the first time! Thanks a load for the quick reply's and solutions!!

---

