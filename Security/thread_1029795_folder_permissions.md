---
title: "folder permissions"
date: 2009-01-03
forum: Security
---

### Post by gothtrance on 2009-01-03
how do i delete a file that says that i am not the owner so i can't change permissions

---

### Post by Rob_H on 2009-01-03
From a terminal, change to the parent directory of the one you want to delete. Then, delete it as root with a command like this.
```
sudo rm -rf <directory_name>
```
Where <directory_name> is the name of the directory you want to blow away. BE VERY CAREFUL to specify the correct one! There's no quicker way to misery than a "sudo rm -rf" at the wrong place.

---

### Post by 2hot6ft2 on 2009-01-03
It's much safer to use
```
sudo rmdir (directory name goes here)

```from the parent directory that way it will only delete the folder that is named.

---

### Post by Rob_H on 2009-01-03
> **2hot6ft2 said:**
> It's much safer to use
```
sudo rmdir (directory name goes here)

```from the parent directory that way it will only delete the folder that is named.

That only works if it's empty.

---

### Post by 2hot6ft2 on 2009-01-03
Actually the question had to do with a file not a folder so it would be

Open a terminal
Applications>Accessories>Terminal
```
cd (name of the folder where file is here)

```
then use
```
sudo rm (name of file here)
```
 Don't use the ()'s in the commands that's just to show that it's seperate.
LOL

---

### Post by Rob_H on 2009-01-03
Ahh, good point. I got the title of the thread stuck in my head.

---

