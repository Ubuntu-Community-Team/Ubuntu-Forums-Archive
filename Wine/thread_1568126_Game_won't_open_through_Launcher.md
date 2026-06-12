---
title: "Game won't open through Launcher"
date: 2010-09-04
forum: Wine
---

### Post by kroq-gar78 on 2010-09-04
Hello Ubuntu Community,

I'm trying to play Medieval 2 Total War on my computer through wine. I installed it on my computer's hdd (installed ubuntu on a permanent external drive) and am trying to run it on Ubuntu without installing it again. I found the file (medieval2.exe) in my windows partition in nautilus and opened it and it ran just fine. I wanted to create a Launcher for it, so I made a launcher on my desktop and set the command to "wine '/windows/Program Files/SEGA/Medieval II Total War/medieval2.exe'", but it odesn't open the game. It just opens a windows that has a title of "CA_LIBS" with nothing in it. I open up the terminal and put that in and it does the same thing. When I enter a command for the launcher to open up to the directory of the exe (nautilus '/windows/Program Files/SEGA/Medieval II Total War/') and run it from within nautilus, it works.

This also happens with my Dawn of War: Winter Assault game. Same exact result (except that it just doesn't do ANYTHING when I open the launcher).

Any idea on why this is happening?
Thanks in advance.

---

### Post by kmsalex on 2010-09-04
First don't put wine in front of it, second you have to specify that its on a different partion, right now the luncher is looking for a folder named windows on the ubuntu hdd. 
here's what it would look like for me to run firefox on my windows partion.
"/media/2C7457705DD85BA3/Program Files/Mozilla Firefox/firefox.exe"
to simplify this instead of manly typing in the command use the brows button to find the .exe on your windows drive and partition.

---

### Post by kroq-gar78 on 2010-09-04
sorry for not saying this but I did  custom partition thing at the insatl and told it to mount my hdd windows as /windows at startup. Why would I not put wine in front of it? isn't it a command that is required to run a windows application?

EDIT: Thanks it works, but why can't I have wine in the beginning?

---

### Post by jeight on 2010-09-04
Make sure that the file that you are linking to in the windows partition doesn't have any spaces. Put it somewhere other that lets say Program Files. Linux doesn't play nice with spaces in windows.

---

### Post by kroq-gar78 on 2010-09-04
the     ' s mean " also, so the spaces aren't a problem

---

### Post by kmsalex on 2010-09-04
> **kroq-gar78 said:**
>  but why can't I have wine in the beginning?

Its not necessary, when it says command...well its not a command in the same scene that a command from a terminal would be. It should relay be labeled as something like "path to .exe" as thats what it relay is. The luncher just sends the single to the .exe to execute and Ubuntu figures out that it needs wine. hay presto you got your game ruining.

PS: mark this thread as solved please):P

---

### Post by hikaricore on 2010-09-04
And next time you have a wine issue post in the wine forum..

---

### Post by kroq-gar78 on 2010-09-05
oops. Yeah sorry forgot there was wine forum. It's solved now

---

