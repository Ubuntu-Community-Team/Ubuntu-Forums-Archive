---
title: "sed command to change sources to Lunar?"
date: 2022-10-29
forum: Ubuntu Development Version
---

### Post by ubername on 2022-10-29
Can anyone remind me of the sed command I need to use to change my apt.sources to lunar (or lobster) please? And anything else I need to get on to the toolchain quickly?

---

### Post by deadflowr on 2022-10-29
```
sudo sed -i 's/kinetic/lunar/g' /etc/apt/sources.list
sudo apt update
sudo apt upgrade
```
Should do it.

Note if you have any 3rd party repos in the sources.list.d sub-directory you might need to disable them, foe now.

---

### Post by ubername on 2022-11-02
Thanks! I have the command somewhere on other machines, but I knew the brilliant forum would help me sooner!

---

