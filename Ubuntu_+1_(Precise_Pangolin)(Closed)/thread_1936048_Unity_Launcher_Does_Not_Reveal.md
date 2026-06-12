---
title: "Unity Launcher Does Not Reveal"
date: 2012-03-05
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by MARP1961 on 2012-03-05
I have a fully updated install of Ubuntu 12.04 on Virtual Box. All Guest Additions are installed and working. Gnome Shell is installed and working also.

However, when I log into Unity and set the launcher to Autohide it does hide but will not reveal when the left hand side is touched, pushed or repeatedly bumped! I have installed CCSM and altered the pressure and sensitivity, all to no avail. Does this feature have problems at the moment? I have had to switch Autohide off.

---

### Post by fjgaude on 2012-03-05
There are issues... if they will be fixed, when, who can say?

---

### Post by sffvba[e0rt on 2012-03-05
Not sure about the issues... my install of 12.04 is working fine in this regards at the moment.


404

---

### Post by kurt18947 on 2012-03-05
You might give this a try, no warranty expressed or implied :P

On the desktop, right-click -> appearance -> behavior -> reveal sensitivity -> high.

I infrequently use Unity but I do occasionally.

Edit: This is on 12.04 also.

---

### Post by fjgaude on 2012-03-05
> **not found said:**
> Not sure about the issues... my install of 12.04 is working fine in this regards at the moment.
404

Mine acts in unstable ways, no way to explain. I use 'never hide' on my 24" monitor.

---

### Post by MARP1961 on 2012-03-07
Thanks for your thoughts. I'm sure things will improve. Perhaps it's an issue with Virtual Box. I almost always use Gnome Shell anyway.

---

### Post by ventrical on 2012-03-07
> **MARP1961 said:**
> Thanks for your thoughts. I'm sure things will improve. Perhaps it's an issue with Virtual Box. I almost always use Gnome Shell anyway.


 An issue here too. It works with the mouse but not when you drag a window over to the left side and they took that option away in the Unity Plugin in CCSM. I just loved that little feature, is was easy on my eyes.. and now it's gone. Not sure of the logic of this decision but if thay are having binding problems then why not build a macro-walker so a user can discriminate his current bindings or (sort of what  they have with ccsm, when a binding is crossed you are warned and given options) or reset a default.
??

---

### Post by martinisonline on 2012-03-15
Im having the same issue!

Using virtualbox also!

---

### Post by neu5eeCh on 2012-03-15
Not using virtual box. I have set it to only reveal when I move to the top left corner (be sure you haven't done this accidentally?). Initially this didn't work very well. But I run updates twice a day and everything is working beautifully at of the moment.

**Edit:** Ha! As soon as I wrote that, I noticed that the launcher won't **stay** revealed, even if I leave my mouse on it.

---

### Post by neu5eeCh on 2012-03-15
I created a bug report for my problem above:

[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/956458](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/956458)

The description is here:

This is a peculair bug.  I can reproduce it with the following:
 1.) The launcher is only set to be revealed by mousing to the upper left corner.
 2.) I switch to another workspace.
 3.) I scale (show windows).
 4.) Then, when I mouse over to the launcher, the launcher will always  prematurely hide, even if my pointer remains on the launcher - making  the launcher impossible to use.


Further details, I start out on the top left workspace, then switch to the top right, then "show windows", then mouse over to the launcher. I can reproduce this bug every time.

---

### Post by 8Kuula on 2012-03-15
For me auto-hide option do not work well, I use synergy to switch keyboard and mouse control to secondary desktop and on main (server) desktop auto-hide works ok, on secondary desktop (client), auto-hide just hides and won't show no matter how hard or long I hit left side of screen.
However if I plug mouse directly to secondary box it works as it should.

Funny part is that main screen is 24" so it would not be so bad thing to have allways visible but secondary screen is 19" and there auto-hide would be usefull :)

---

### Post by Bobhuber on 2012-03-15
> **marp1961 said:**
> i have a fully updated install of ubuntu 12.04 on virtual box. All guest additions are installed and working. Gnome shell is installed and working also.

However, when i log into unity and set the launcher to autohide it does hide but will not reveal when the left hand side is touched, pushed or repeatedly bumped! I have installed ccsm and altered the pressure and sensitivity, all to no avail. Does this feature have problems at the moment? I have had to switch autohide off.
+1 03/15/2012

---

### Post by bluenova on 2012-03-16
I also had problems in VB, I think the 11.04 host (using Unity) was interfering. It works fine on a normal install (for me).

---

### Post by 8Kuula on 2012-03-28
> **8Kuula said:**
> For me auto-hide option do not work well, I use synergy to switch keyboard and mouse control to secondary desktop and on main (server) desktop auto-hide works ok, on secondary desktop (client), auto-hide just hides and won't show no matter how hard or long I hit left side of screen.
However if I plug mouse directly to secondary box it works as it should.

Funny part is that main screen is 24" so it would not be so bad thing to have allways visible but secondary screen is 19" and there auto-hide would be usefull :)

To get autohide work with synergy, if someone is pondering... not.
```
section: options
  relativeMouseMoves = true
  keystroke(control+F9) = switchToScreen(desktop1) ; lockCursorToScreen(on)
  keystroke(control+F10) = switchToScreen(desktop2) ; lockCursorToScreen(on)
end
```

---

