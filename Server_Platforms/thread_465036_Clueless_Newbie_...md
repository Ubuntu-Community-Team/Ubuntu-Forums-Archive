---
title: "Clueless Newbie .."
date: 2007-06-05
forum: Server Platforms
---

### Post by BigNeonGlitter on 2007-06-05
I have installed Ubuntu Server (and chose to install LAMP). I then did a "sudo aptitude install x-window-system-core gnome" and then a "sudo aptitude install x-window-system-core gdm" to get a GUI login interface. Now when I boot, I get the GUI login, which is fine, and then after log in I get the desktop (which seems to be a limited options version). I have no browser and  no terminal, or maybe I do and have no idea how to access them. So how does one go about getting these things, so I can use phpMyAdmin, or anything else I choose?

Thanks for your help ..

---

### Post by turinglabs on 2007-06-05
You don't necessarily need an X desktop to run a LAMP server, for example phpMyAdmin runs just fine standalone with Apache and MySQL, you would just have to connect to it from another box with a browser. If you do want the full-blown Gnome desktop, try 'tasksel install ubuntu-desktop' (or just run tasksel alone for the curses interface). This will pull in all the required dependencies for you.

---

### Post by BigNeonGlitter on 2007-06-05
Doug,

Thanks so much for the quick reply. I understand what you are saying about accessing from a browser on another machine, but if I did want the full blown Gnome desktop, how do i run "tasksel install ubuntu-desktop"? I can't seem to find any way of running anything! I know on the non-server Ubuntu edition, there is a terminal, but I don't see one on the server edition. Obviously I am missing something .. like I said, this is all new to me!

Thanks..

---

### Post by turinglabs on 2007-06-05
Ah, sorry. If you are logged into your minimal X session, you can type 'ctrl-alt-f1' to get to a console. Log in as the user you created during the installation, and type 'sudo tasksel install ubuntu-desktop' from the prompt. The password it prompts you for is your user's password. Typing 'ctrl-alt-f7' will get you back to the desktop.

One thing, it's probably a good idea to do the 'ctrl-alt-f1' from the gdm login screen, then after the task install has finished, restart gdm with 'sudo /etc/init.d/gdm restart' to get back to the login screen. After all that , you should have your nice new desktop available.

---

### Post by BigNeonGlitter on 2007-06-05
OK, well it looks like I am getting closer! When I get to the console, and do a "sudo tasksel install ubuntu-desktop", it says "sudo: tasksel: command not found"

---

### Post by turinglabs on 2007-06-05
Ah, I figured it would be installed already. No problem, just install tasksel with 'sudo apt-get install tasksel'.

---

### Post by BigNeonGlitter on 2007-06-05
OK, well that produces:

"Package tasksel is not available, but is referred to by another package. This may mean that the package is missing, has been obsoleted, or is only available from another source
E: Package tasksel has no installation candidate"

I feel bad for bothering you like this .. I'd love to get this working though!

Thanks for your help ..

---

### Post by BigNeonGlitter on 2007-06-05
But .. I did figure out how to install the packages individually without tasksel .. So I think that may do it!

Thanks again Doug

---

### Post by turinglabs on 2007-06-05
No problem, glad to help. I have tasksel installed on my Feisty desktop, it should be part of the base install, very strange. I'm glad you got it working in the end, however. Probably an 'apt-get update' before the install attempt would fix the error message.

---

