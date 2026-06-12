---
title: "Ubuntu one does nothing (9.10 x86)"
date: 2010-01-28
forum: Ubuntu One (CLOSED)
---

### Post by false_chicken on 2010-01-28
I just did a reinstall of 9.10. And when I open ubuntu one nothing happens. I cant link my account to my computer because it doesnt open a browser for me to add it. And when I open the folder for ubuntu one and click connect it just says connecting and doesnt do anything. If I drop a file into the folder it says syncing but its not linked to anything so I dont know whats up. Any suggestions?

---

### Post by andrea000 on 2010-02-01
There is a problem going around with u1 it seems to be a
bug that has been around for a while if your problem is
just that you can't get the web page to let you add your
computer then i can help you with that.Open a terminal
and copy and past this

> sudo apt-get install ubuntuone-client-tools

in the terminal copy and past this

> u1sync --authorize 

The webpage will come up asking you to login then it
should ask you to add your computer.

---

