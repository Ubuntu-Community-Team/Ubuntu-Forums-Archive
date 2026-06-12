---
title: "QDVDAuthor - The 30-Second Menu Loop"
date: 2009-03-22
forum: Ubuntu Studio
---

### Post by clubsoda on 2009-03-22
The audio tracks in my menus aren't looping, they play just once.
I've followed the procedure at 
[http://qdvdauthor.wiki.sourceforge.net/Play+audio+in+a+menu](http://qdvdauthor.wiki.sourceforge.net/Play+audio+in+a+menu)
but the "Pause after movie is finished" setting is sticky at -1, i.e. it can be set to zero but on re-opening the dialog it's back to -1.

Bug reporting time?

Version 1:1.2.0-0.0ubuntu1 on Xubuntu Intrepid

---

### Post by clubsoda on 2009-03-26
For the main menu VMGM this seems to be fixed in version 1.7, which will ship with Jaunty.  However, installing QDVDAuthor v1.7 on Intrepid requires some package fiddling so here's a workaround.  Open up the xml file in an editor and find the line ```
<MenuName>Main Menu VMGM</MenuName>
```Immediately below that, add the following:-```
<MenuPause>0</MenuPause>
<MenuPost> jump vmgm menu 1; </MenuPost>
```This only works on the main menu though, it looks like SubMenu looping is broken.

---

