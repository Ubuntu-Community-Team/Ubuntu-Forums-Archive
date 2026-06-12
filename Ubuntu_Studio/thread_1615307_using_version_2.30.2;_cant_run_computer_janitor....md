---
title: "using version 2.30.2; cant run computer janitor..."
date: 2010-11-06
forum: Ubuntu Studio
---

### Post by jjb945025 on 2010-11-06
can anyone tell me how to start computer janitor from the terminal. also, how do i find the trash can so that i can free up space on the hard drive? thank you.

---

### Post by Pablo_F on 2010-11-06
> gksu --desktop /usr/share/applications/computer-janitor-gtk.desktop computer-janitor-gtk

I figured out by dragging the computer janitor from System -> Administration to the Desktop or Panel, then looking at the properties of the launcher.

Anyway, 

sudo apt-get autoremove 

is shorter. 

The thrash is in .local/share, in your home directory. .local is a hidden directory.

You can just add to the Panel (right button on the panel): the Trash applet.

Cheers! Pablo

---

### Post by jjb945025 on 2010-11-10
hello. i reinstalled ubuntu 2.30.2 and now am able to open computer janitor... now i have a different problem.. when i go to system---->preferences or administration, isn't there supposed to be an icon for the firewall? i remember there was in the last install. how do i get it back there because i believe i had to do something in terminal to get the icon there and cannot remember. also, when i clickon tools in firefox, "stop private browsing" and "clear recent history" are dulled out ( i cannot select either). am i already browsingprivately? if so i didn't choose to be. i want to be able to clear my browsing history and cannot..i also want to block incoming traffic with the firewall  and cannot. any help would be greatly appreciated. thanks again.   -joe b.

---

### Post by jjb945025 on 2010-11-10
i figured out how to install the firewall but still have the other problems, who ever is looking into this - thanks alot, i dont know why ubuntu does this, it happend another time i had installed it too.........

---

### Post by Pablo_F on 2010-11-10
Hi, 

I suggest you ask the question in another board, maybe, general help. It is more probable you get an answer there.

Cheers! Pablo

---

