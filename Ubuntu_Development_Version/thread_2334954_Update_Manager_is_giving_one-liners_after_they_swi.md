---
title: "Update Manager is giving one-liners after they switched to Gnome 3.20"
date: 2016-08-24
forum: Ubuntu Development Version
---

### Post by Smask on 2016-08-24
I don't know if this is a Flashback issue or not, but I have this issue on all my Yakkety boxes, which have Flashback installed.

When doing an update and clicking show details, UM will give you one line of download information and then 10-15 lines of terminal progress, unless you clicked show details after it downloaded all the files and were already installing them, you only get one line of terminal output. If you manage to click details while downloading and if you manage to maximize the window still while downloading, it will give you more terminal lines when installing.


[ATTACH=CONFIG]270841[/ATTACH]

---

### Post by cariboo on 2016-08-24
That's one of the reasons why I don't use GUI tools to do daily updates. With the latest version of apt, I run the following command in a terminal:

```
sudo apt update && sudo apt upgrade
```

you see all the details, what is going to be upgraded, then the process of downloading and installing the packages. I actually have the command aliased in .bashrc as update. So all I have to type is update, then my password, and then the fun begins. :)

---

### Post by VMC on 2016-08-24
> **cariboo said:**
> That's one of the reasons why I don't use GUI tools to do daily updates. With the latest version of apt, I run the following command in a terminal:

```
sudo apt update && sudo apt upgrade
```

you see all the details, what is going to be upgraded, then the process of downloading and installing the packages. I actually have the command aliased in .bashrc as update. So all I have to type is update, then my password, and then the fun begins. :)
I normally update using Terminal commands, but ironically yesterday I did use the Software Updater on Xubuntu and noticed the same one-liner.

---

### Post by ventrical on 2016-08-25
> **VMC said:**
> I normally update using Terminal commands, but ironically yesterday I did use the Software Updater on Xubuntu and noticed the same one-liner.

Update mangler is one of the flaws in the overall gem :) I am so used to using terminal that I just use the updater to set and unset my proposed repo. So it has it's uses.:)

 As for overall 'ubuntuesque' promotional ventures...it leaves new users wanting but when it does work , it works well. I will still rather weather ubuntuesque buggy updaters that other commercial hack-crapper updaters . I have perfected restoring ubuntu  systems to a fine art of 5 minutes rather than 5 hours of registry cleaning.

Regards..

---

