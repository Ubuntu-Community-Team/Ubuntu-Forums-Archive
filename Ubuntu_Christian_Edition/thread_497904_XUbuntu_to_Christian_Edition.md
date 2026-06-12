---
title: "XUbuntu to Christian Edition?"
date: 2007-07-10
forum: Ubuntu Christian Edition
---

### Post by 7Priest7 on 2007-07-10
I was wondering if the Convert to Christian Edition will work on XUbuntu (Feisty)

I found a similar topic that may still hold true [http://ubuntuforums.org/showthread.php?t=317969](http://ubuntuforums.org/showthread.php?t=317969)

But they only refer to old versions of ubuntu

to summarize my question
Can I upgrade to Christian Edition from XUbuntu?

---

### Post by mysticrider92 on 2007-07-10
That guide will work fine for any Ubuntu version as long as there is a convert_me script for that release.

---

### Post by 7Priest7 on 2007-07-11
This is the only convert script I found

Convert:
Are you already using Ubuntu 7.04 "Feisty Fawn"? Do you want to convert?
Click Here

But will it work on XUbuntu?

Or Give me a link to the XUbuntu Convert script?

Please Help

Alex

---

### Post by 7Priest7 on 2007-07-11
Also I need a link to the "Dans Guardian GUI"
For Feisty...

Please and Thank You

Alex

---

### Post by mysticrider92 on 2007-07-11
That is the only script that we have so far. It will work fine on XUbuntu, as long as you add zenity and gedit (like in doobit's tutorial) with this terminal command:
```
sudo apt-get install zenity gedit
```

The script will automatically add the Dansguardian GUI, so you will not need the one in his tutorial (that is an older version than the 3.* GUI that will be installed).  

I am sorry I didn't make my last post very clear, I was in a hurry.

[edit] I didn't notice doobit's reason for getting the Dans GUI, but if that ends up as a problem, I can give you a terminal command that will make Dansguardian let you download the GUI.

---

