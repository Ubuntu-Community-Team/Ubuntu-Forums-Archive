---
title: "How to add the &quot;Create Launcher&quot; command to the right click menu in 11.10 and up"
date: 2011-12-17
forum: Tutorials
---

### Post by relik1989 on 2011-12-17
OK, so if your like me you really miss the ability to right click in a folder or on your desktop and create a launcher for a application. I especially used the feature for Wine apps. 

So here is a very simple guide on how to - more or less - regain the ability to right click and create a launcher.

1.Install Nautilus Scripts manager from the software center.

2.In a terminal run 
```
gksu nautilus
```
then navigate to 
```
usr/share/nautilus-scripts 
```
and create a new document, I called mine "create_launcher"

3.Open the new file and paste in 
```
gnome-desktop-item-edit --create-new ~/Desktop
``` 
then save and mark the file as execuatable through right clik then premissions tab.

4.Before going any further just make sure the script you just made works by double clicking it and selecting run, if you see the old syle create launcher dialog then your on the right track, go ahead and close it for now, were going to take this one step further.

5.Open nautilus scripts manager (Should be in your unity dash it may not have an icon though), then just put a check mark in the box that says active.

6.Lastly open a terminal or hit alt+F2 and type,
```
nautilus -q
``` 
when you reopen nautilus you should now have the create launcher command in your right click menu under scripts.

Enjoy.

---

