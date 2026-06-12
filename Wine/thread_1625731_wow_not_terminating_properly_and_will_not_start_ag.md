---
title: "wow not terminating properly and will not start again after closing"
date: 2010-11-19
forum: Wine
---

### Post by cbilljones on 2010-11-19
My friend and i are having this issue, and oddly i cant find any info on it; this is a new issue since a wow update on tues. nov 16/2010. After closing wow and trying to reopen it nothing happens; if you try to run launcher.exe from terminal nothing happens, just goes to a new line ready for input. So i ran game initially from terminal and notice its not terminating when i close it, and if i try to start a new session it does what i mentioned above, if a close the shell i can start a new session. What i would like to do as a temp workaround is append my shortcut to run launcher.exe from a terminal, this way we can terminate the terminal when done and problem solved; is this possible? Sorry for the wordy post

[edit] figured it out, just had to add "gnome-terminal -x" to my shortcut, now launches from terminal and terminal can be closed after to properly terminate the program, then launcher.exe will work as normal

Pastebin of terminal output so maybe someone can see why its not terminating:

[http://paste.ubuntu.com/534355/](http://paste.ubuntu.com/534355/)

---

