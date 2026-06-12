---
title: "Removable Media - Software = &quot;Run Software&quot; (?!)"
date: 2016-08-25
forum: Security
---

### Post by johnmne on 2016-08-25
I don't understand why Ubuntu 16 default option for a removable media, when it is a software, is "Run Software" ???

In Ubuntu 16.04, go to Settings -> Details.
In the left pane choose "Removable Media".
On the right pane you'll see "Software" while value in the drop-down menu is "Run Software".

Why would it be the default option?
It seems like a major security risk.
(In the old days people laughed at Windows that it "autorun"s executables from CDs and Flash drives...)

---

I replaced the value from "Run Software" to "Do nothing".
In addition, I ticked the checkbox that says "Never prompt or start programs on media insertion."

---

Why is this the default option ..? 
Why no one changes it ..?

----

_Edit_:
Where do I report about this bug ?

---

### Post by reese1379 on 2016-08-25
How to autorun files and scripts in Ubuntu when inserting a USB stick like autorun.inf in Windows?
[http://askubuntu.com/questions/642511/how-to-autorun-files-and-scripts-in-ubuntu-when-inserting-a-usb-stick-like-autor](http://askubuntu.com/questions/642511/how-to-autorun-files-and-scripts-in-ubuntu-when-inserting-a-usb-stick-like-autor)

---

### Post by johnmne on 2016-08-26
> **reese1379 said:**
> How to autorun files and scripts in Ubuntu when inserting a USB stick like autorun.inf in Windows?
[http://askubuntu.com/questions/642511/how-to-autorun-files-and-scripts-in-ubuntu-when-inserting-a-usb-stick-like-autor](http://askubuntu.com/questions/642511/how-to-autorun-files-and-scripts-in-ubuntu-when-inserting-a-usb-stick-like-autor)

You didn't understand my post.
I'm not asking how to make autorun.

I'm saying that the default autorun value is very bad !!
It executes software from external, unknown resource, automatically !  This is bad !

Also I'm asking where should I report this bug ???
In launchpad? If so, then in which project ??

---

### Post by howefield on 2016-08-26
Yes, in launchpad and probably against gnome-control-center, I'd think.

You can start the process in a terminal with..

```
ubuntu-bug gnome-control-center
```

---

### Post by T2uiYKb7 on 2016-08-26
It's the same in Xubuntu and has been for years. I always thought is was bizarre but not exactly a bug.

---

### Post by cogset on 2016-08-27
Certainly not very wise or safe, either.

---

