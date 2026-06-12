---
title: "Help me with Microsoft Word"
date: 2009-04-27
forum: Wine
---

### Post by sheel1234 on 2009-04-27
Hello, I am a new user
I was wondering how to install Microsoft Word 2002 in Ubuntu 9.04
Please dont suggest openoffice, i tried it and don like it.
Ive read guides but they dont really work

Thank you

---

### Post by Marlonsm on 2009-04-27
I think MS Office will run well under Wine. (At least 2007 does).

To install Wine, go to:

System>Administration>Synaptic Package Manager, look for "Wine" and install it. (Or just type "Sudo apt-get install wine" on the terminal, Ubuntu will do the rest for you)

Now, with it installed, insert the MS Office CD, find the .exe used to install (usually it's called setup.exe), right click it and choose "Open with Wine Windows Program Loader". Follow the rest of the setup and you're good to go.

MS Office will be inside: Applications > Wine > Programs

---

