---
title: "Wine not opening programs"
date: 2009-12-03
forum: Wine
---

### Post by prions on 2009-12-03
I just upgraded to 9.10 and installed wine to test out some programs. I installed it through synaptic, but whenever I try to open a windows program, nothing happens. 

I'm not sure what to do here, since it worked fine for me in 8.10.

Edit:

In synaptic there were 2 versions of wine, Wine and Wine 1.2

I removed Wine and installed 1.2 over it and its working now.

---

### Post by bostjanv on 2009-12-04
Hello,
I'm new to Ubuntu (I just installed 9.10), and I'm having the same problem as described in the previous post. In somewhat more detail: I used to run Suse 11.1 (I still run it on another computer), and Wine ran fine there. On Ubuntu I set up the registry similarly to my old installation, including the PATH environment variable. When I enter SET in my Wine console, I get the listing of all my environment variables. However, when I enter the name of a program located in one of the PATH directories, I get the message "file not found". If I enter the full path of the program, the program runs fine.

This is happening with Wine version 1.0.1 installed. The previous post asserts that uninstalling Wine 1.0.1 and installing Wine1.2 solves the problem. I'm somewhat reluctant to take that step since version 1.0.1 is listed as "stable". Can someone comment whether Wine1.2 can be entirely trusted and why the described problem on 1.0.1 cannot be fixed?
Regards,
bostjanv

---

### Post by bostjanv on 2009-12-04
Hello,
Sorry, this was a false alarm. I discovered an error in the PATH variable.
Regards,
bostjanv

---

