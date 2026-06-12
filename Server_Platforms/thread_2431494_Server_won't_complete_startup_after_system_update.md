---
title: "Server won't complete startup after system update"
date: 2019-11-17
forum: Server Platforms
---

### Post by esprimo2 on 2019-11-17
My system updated several days ago and has been unable to complete startup. Startup gets gets far enough that Apache starts and allows serving web pages. Through Virtualmin, I can get a Terminal window. I can also get a terminal when using Recovery Mode.

Although this may be heresy to some Ubuntu Server zealots, I have installed the Gnome interface on it. I really need startup to finish so I can access the GUI.

I also ran boot-repair; the report can be found at:  [http://paste.ubuntu.com/p/b3SJrFD92p/plain/](http://paste.ubuntu.com/p/b3SJrFD92p/plain/)

Any assistance would be greatly appreciated.

Many thanks

Patrick

---

### Post by esprimo2 on 2019-11-22
I fixed this by removing the gnome desktop and installing the Xfce desktop.

---

