---
title: "GIMP-Unity-Integration"
date: 2012-10-11
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by thotz on 2012-10-11
When I set GIMP to the One-Window-Mode and I maximize GIMP it's good integrated in Unity.

But when I open GIMP the next time it's not fully integrated (there is a bar titled "GNU Image Manipulation Program"). So I have to maximize this window again.

What do you think? Can you reproduce this beaviour?

---

### Post by PaulW2U on 2012-10-11
> **thotz said:**
> Can you reproduce this beaviour?

Yes, same here.

Unlike other applications it doesn't open maximised if it is closed maximised. Also the program window is too large for the screen space available and extends below the bottom edge of the screen.

---

### Post by thotz on 2012-10-11
> **PaulW2U said:**
> Yes, same here.

Unlike other applications it doesn't open maximised if it is closed maximised. Also the program window is too large for the screen space available and extends below the bottom edge of the screen.

Thank you for confirming.

Made a bug report on Launchpad:
[https://bugs.launchpad.net/ubuntu/+source/gimp/+bug/1065578](https://bugs.launchpad.net/ubuntu/+source/gimp/+bug/1065578)

---

### Post by mcellius on 2012-10-11
Yep, it's the same for me.

---

### Post by mc4man on 2012-10-12
May be awhile till this is fixed, while not a fix gimp can be set in compiz to open maximized (window rules)
Though then it would only be either maxed or minimized, restore wouldn't exist.

---

### Post by thotz on 2012-10-12
The problem also occurs in Inkscape and Blender.

---

### Post by PaulW2U on 2012-10-12
> **thotz said:**
> The problem also occurs in Inkscape and Blender.

In which case the bug needs to be filed against those applications as well or refiled against Unity as it may not be a Gimp problem.

---

### Post by x-shaney-x on 2012-10-12
Don't know if it works in other but I get around the same problem in Gthumb by altering the window size in dconf-settings to the res of my monitor ( 1366x768 ).
It now always opens maximized.

---

### Post by thotz on 2012-10-12
I have asked a developer, so if you apply to the bug e-mails we will see what will happen to this bug.

---

### Post by alphacrucis2 on 2012-10-12
Curiously I notice the exact same problem with Gimp 2.8.2 in Windows 7. 

Well not the Unity integration of course but this one:

> Also the program window is too large for the screen space available and extends below the bottom edge of the screen.

---

