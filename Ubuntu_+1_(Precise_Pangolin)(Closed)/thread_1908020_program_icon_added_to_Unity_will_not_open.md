---
title: "program icon added to Unity will not open"
date: 2012-01-12
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Robertjm on 2012-01-12
I did a custom install of GIMP 2.7.4 on my system recently. It was installed to:

/opt/gimp-2.7.4/bin

Since it didn't start automatically, I added that line to my .bashrc file and then restarted my computer. Now I can go to the command line and simply enter gimp-2.7 and the program launches. 

I then decided I wanted to add a program icon to my Unity bar. Simplest way I have found to pin programs is to launch them, and then click the Keep In Launcher option. 

However, that's where I'm having problems. I can pin the program just fine. However, when I go to launch the program it flashes light/dark a couple of times, but never launches.

Is there some other file I need to add the path to for this to work other than /home/.bashrc?

Thanks!

Robert

---

### Post by JRV on 2012-01-12
The launcher is a .desktop file located in /home/USER_NAME/.local/share/applications.

Navigate to it. 
Right click the icon and select Properties.
Change the Command field to the full pathname of the program you wish to run.

---

