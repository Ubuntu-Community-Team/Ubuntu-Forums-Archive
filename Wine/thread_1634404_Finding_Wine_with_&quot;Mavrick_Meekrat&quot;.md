---
title: "Finding Wine with &quot;Mavrick Meekrat&quot;"
date: 2010-11-30
forum: Wine
---

### Post by Learnertt on 2010-11-30
Hello all,
 
Ubuntu "Meekrat"(10.10) is running swell as a virtual pc. While searching for the Wine for this release though i could not find it.
 
Can you all identify a workaround if not the version itself considering the following:
 
 
Beginner user
Laptop HP compaq
Vrtl PC-Vmware
 
Please check  my profile for any other info but in summary I'm new to Ubuntu.

---

### Post by Psyael on 2010-11-30
I'm not sure I understand the question.

Stable releases of Wine are available in the Software Center. You can download and install it through there. Unstable releases require you to add the PPA.

---

### Post by Soulcage on 2010-11-30
```
sudo add-apt-repository ppa:ubuntu-wine/ppa
```
```
sudo apt-get update
```
```
sudo apt-get install wine1.3
``` (or 1.2)

---

