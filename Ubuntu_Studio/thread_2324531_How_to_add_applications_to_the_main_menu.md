---
title: "How to add applications to the main menu?"
date: 2016-05-14
forum: Ubuntu Studio
---

### Post by javierdl on 2016-05-14
There's a couple apps I got, but I think all I did was to download and expand a compressed file. Then they can run from their expanded folder. For now I created links on my desktop. But it would be nice to have them in the main menu instead.

Thanks guys :)

JDL

---

### Post by javierdl on 2016-05-15
Update:
I found the way! With the Menu Editor, in the Settings Manager.
Except now that I added the apps, one directory disappeared :(
I used to have Photography, with Gimp, Krita, etc inside, and now it's gone. I did expanded it to see what was inside while in the Menu Editor, but never hit Delete. 
And those programs seem really gone now :( I did a search with File Manager in Home and it did not find them.
Actually, I found Gimp, Krita, and MyPaint files in /usr/lib
The Video Production directory no longer shows in the menu either, but it is still there in the Menu Editor, but empty. When selecting it, it only offers one choice: Hide from menus. It's Off by default. But even if I turn it on, the moment I save changes, it goes back to default.

Any ideas?

Thanks guys,

JDL

---

### Post by javierdl on 2016-05-15
Update:

I found the Photography directory!
It was inside the Graphic Design directory. I have no idea how it ended up there. I got it out where it should be. Problem is, it's not expandable as before. 
Also, I manually added Gimp back into the Photography directory, but neither the Photography dir nor Gimp are showing in the menu still :(

---

### Post by javierdl on 2016-05-19
So everything is back to the way it was before. But thanks to "reinstalling everything from scratch" :(
Now I do know how to add and remove program shortcuts to the main menu. Unfortunately based on the previous experience, this can also result in messing the Main Menu really bad. So I guess I'll have to leave it alone.

---

### Post by oscalypso on 2016-05-22
I had the same problem
I deleted the file xfce-applications.menu in ~/.config/menus/ 
and everything went back

tweaking the menu is easier for me with Alacarte
[https://apps.ubuntu.com/cat/applications/precise/alacarte/](https://apps.ubuntu.com/cat/applications/precise/alacarte/)

---

