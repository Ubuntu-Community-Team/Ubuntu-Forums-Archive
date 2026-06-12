---
title: "GDM start/stop video issues"
date: 2007-05-17
forum: Server Platforms
---

### Post by mattb13 on 2007-05-17
Ok, so I installed feisty on my test server. All installed well, I updated it and everything is great.
I installed the desktop for occasional maintenance. i.e. login to the server via VNC, start GDM, do my thing, stop GDM and logout. 

My problem come when starting and stopping GDM. I can start it from the command line in tty1, shift over to tty7, login and work, logout, switch back to tty1 and stop GDM and all works ok. Problem is after starting stopping it a few times, I'll start it, go to tty7 and the screen is flickering. I'll go back to tty1 and stop it, start it again and it is still flickering. Only way to stop it is to restart the machine. Not acceptable for prouction environment.

I have looked at serveral video driver posts and notsure that they help much. Machine is running intel chipset with the i810 drivers as of now. vesa driver works as well, but problem still exists. Altered /etc/X11/xorg.conf file, changed resolution, depth, frequency(Hz) and still the problem is there. any suggestions??

To start GDM I enter:   /etc/init.d/GDM start
to stop  GDM I enter:   /etc/init.d/GDM stop

are my commands wrong? new to this but catching on fast...

---

### Post by The Soundophiliac on 2007-05-17
Almost all commands are in lower case. Try sudo gdm start. If you get a message saying gdm is already running, run sudo killall gdm.

---

### Post by mattb13 on 2007-05-17
understand about the lower case typing, I just placed it uppercase to emphasize what I was typing.

Anyways, I tried sudo killall gdm and it stopped everything, then I started it up again, and switched to tty7 and the screen is flickering, so no resolve yet....

Curious if KDE desktop would do this? can I apt-get kbuntu  desktop if I already have ubuntu desktop installed? how could I remove ubuntu desktop? and leave just the server intact?

---

### Post by mattb13 on 2007-05-18
Anyone have any answers?

---

### Post by lazertek on 2007-05-22
you can install kubuntu using synaptic manager... or type : **apt-get install kde-desktop** in terminal. add sudo before the command if you arent in the root account.

---

