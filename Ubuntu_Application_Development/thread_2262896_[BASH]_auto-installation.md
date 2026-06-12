---
title: "[BASH] auto-installation"
date: 2015-01-28
forum: Ubuntu Application Development
---

### Post by iacoposk8 on 2015-01-28
hello everyone! I am creating a script sh it install a program that has multiple dependencies.
 there are two problems:
 1) there are many "sudo apt-get install" in the code, the first asks me the password, then if it passes some time, and it re-run another sudo, it asks me password another time. I want its to ask me for the password only once?
 2) How can I program the responses from the various installations?
 example:
 sudo add-apt-repository> it will ask me to press enter
 sudo apt-get install>  it will ask me to press yes or no

 how to solve? thank you.

---

### Post by TheFu on 2015-01-28
Make a .deb package with the dependencies specified.

Run all the PPA additions at once (most commands have a **-y** option) and then run the apt-get install with every package listed at once.
This way most sudo settings will only ask for a password once, at the beginning, and if all the sudo commands begin within the timeout period (5 min is default), no further prompt for that will happen.

---

