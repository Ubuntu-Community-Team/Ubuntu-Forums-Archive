---
title: "Current coordinates for mouse using uinput"
date: 2009-10-20
forum: Ubuntu Dev Link Forum
---

### Post by nikhil1986 on 2009-10-20
Hi,
I am creating a program which uses a smartphone as a trackpad to control a Ubuntu Desktop. Basically it is another derivation of a virtual trackpad so that the user can control his mouse pointer from his phone. I am writing to a uinput driver which helps users to inject data such as mouse, keyboard events to the Linux kernel. I have successfully been able to do this, but am having a problem making the mouse pointer move as I want it to. I have researched that a mouse only supports Relative coordinates, NOT absolute ones, thus there is no way for me to know where the current position of the mouse is on the screen. I do not want to use X11, GTK etc, since it does not make sense for my application. It is essential that I know the current mouse position so that I can calculate where the mouse should move based on user input on the trackpad. I would appreciate some sort of guidance as I've been unable to find any relevant information online.
 
Thanks

---

