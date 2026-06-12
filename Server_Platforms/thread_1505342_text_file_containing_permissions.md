---
title: "text file containing permissions"
date: 2010-06-09
forum: Server Platforms
---

### Post by wesg on 2010-06-09
Is it possible to have a text file somewhere that contains a list of all users that are allowed access to a given folder? This would be fantastic for file servers on a network.

---

### Post by Drenriza on 2010-06-09
Lets say that you have a folder called

danger and you want
earl
bent and inge to be the only ppl out of 1000 to go into this folder.

Then you can make them member of a group called danger or w/e and then make it so only this group can enter the danger folder.
By changing the group on the folder with ```
chown
```

Users can be member of as meny groups as you want.
Primary group & secondary group(s). 

just an example.

---

