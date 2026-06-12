---
title: "tree command"
date: 2009-02-19
forum: The Cafe
---

### Post by shmoesus on 2009-02-19
dose anyone have a command or shell script that displays the tree command in ubuntu 6.10 i need one that displays files and directorys 
if you could help it would be greatly appreciated
_shmoesus the anime god_

---

### Post by bsharp on 2009-02-19
umm, tree?

if it's not installed, sudo apt-get install tree && tree?

---

### Post by Simian Man on 2009-02-19
Ubuntu doesn't come with tree??

---

### Post by bsharp on 2009-02-19
Now that I think of it, why are you using 6.10? Support for that version ended last year I think.:confused:

---

### Post by shmoesus on 2009-02-19
ops i meant 8.04 i was thinking of something else but when i go to use the command: sudo apt-get install tree && tree 
it just keeps telling me 
reading package lists... Done
Building dependency tree
Reading state information... Done
E: Could't find package tree

---

### Post by SeanHodges on 2009-02-19
> **shmoesus said:**
> ops i meant 8.04 i was thinking of something else but when i go to use the command: sudo apt-get install tree && tree 
it just keeps telling me 
reading package lists... Done
Building dependency tree
Reading state information... Done
E: Could't find package tree

tree is in the Universe repository, [follow these instructions]("https://help.ubuntu.com/community/Repositories/Ubuntu") to enable it.

Then install it using apt-get, or by [clicking here]("apt://tree").

---

