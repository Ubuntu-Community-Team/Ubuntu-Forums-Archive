---
title: "Install Servers on Desktop Edition - bad idea?"
date: 2006-06-17
forum: Server Platforms
---

### Post by printmkr on 2006-06-17
I am thinking of trying out Ubuntu. I would like to eventually use it as an Apache, MySQL, Ruby on Rails server, but I would also like to give it a whirl as a desktop also. Is there a downside with installing the Desktop CD and manually installing the servers I need, or should I just stick to the Server edition? (I don't need the LAMP install option). Or am I going to be confusing myself by doing this, and should just install the Desktop and Server on two different machines to try them out? I am a Linux noob (aside from running Smoothwall). Any advice would be appreciated!

---

### Post by Randomskk on 2006-06-17
There's no downside, and using the desktop version may well make your life easier as some people find that easier to use and play around on.

However, it will run a little slower, since it has a GUI as well as the server apps. For a dedicated server once you are happy with Ubuntu, I would go for a server-install and then add the servers you want (or remove the GUI from the current server but that can get messy).

---

### Post by bluefrog on 2006-06-18
if you have enough ram (e.g. 512 RAM) just install the servers you need on the GUI ubuntu.

If you need more ram, disable the start of gdm at boot (sudo update-rc.d gdm remove) then if you really want to start gdm once in a while you can   sudo /etc/init.d/gdm start

to enable it again at boot  sudo update-rc.d gdm defaults

James

---

### Post by printmkr on 2006-06-18
Thanks for the help! The box I am thinking of has 1.5 gigs of RAM so I am hoping that will do!

---

