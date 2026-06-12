---
title: "Global menu toggle  option in appearances."
date: 2014-02-21
forum: Ubuntu Development Version
---

### Post by philinux on 2014-02-21
[http://www.omgubuntu.co.uk/2014/02/locally-integrated-menus-ubuntu-14-04?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG%21+Ubuntu%21%29](http://www.omgubuntu.co.uk/2014/02/locally-integrated-menus-ubuntu-14-04?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG%21+Ubuntu%21%29)

Interesting change that.

---

### Post by mc4man on 2014-02-21
Works pretty good, vs. the previous dconf > whitelist it now affects all apps inc. gtk2, qt4 & nautilus
It is however an all or none option
(the previous dconf whitelist/blacklist is still there so for the moment can still be selectively applied if desired.

---

### Post by craig10x on 2014-02-21
Right...it's all or nothing...just tried it...however, it doesn't affect the top panel as far as the web browser being open...which i was hoping it would not...so, no screen space lost for web browsing and now all the open windows have the menus right on them...sounds like kind of a "win win" deal here :D

---

### Post by mc4man on 2014-02-21
well it shouldn't affect space as the menu goes to the title bar so in that regard like better, however here a log out in is required to get them to work properly after changing option
(seems like log out/ins are needed quite often

---

### Post by philinux on 2014-02-21
> **mc4man said:**
> well it shouldn't affect space as the menu goes to the title bar so in that regard like better, however here a log out in is required to get them to work properly after changing option
(seems like log out/ins are needed quite often

Maybe a setsid unity would do it.  I'll give it a whirl when back home.

---

### Post by mc4man on 2014-02-21
In the default, "In top bar" it seems that once an app menu in the panel is exposed & used,  the menu never disappears unless one clicks or d. clicks in an empty space in the unity panel.
Seems weird, no clue if intended or a bug
[https://bugs.launchpad.net/bugs/1283238](https://bugs.launchpad.net/bugs/1283238)

---

### Post by mc4man on 2014-02-21
Actually it doesn't appear that a log out/in is needed. The issue here is that when using an external usb mouse on this laptop LIM menu items work once ok, then it starts taking multiple attempts to expose another menu item. Also affects the laptops l. mouse click button but not 'tap on touchpad'
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1283260](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1283260)

If sticking with default in addition to the menu not disappearing after use there is this - 
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1283156](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1283156)

---

### Post by x-shaney-x on 2014-02-23
I find this option great and would make a good default but I wonder about the menubar itself.
It's fine when using a maximized app but the rest of the time it is just a long blank area of screen not being used, other than the indicators.
It just looks and feels wrong.

---

### Post by RGG on 2014-02-23
The topbar becomes almost useless and bad looking with menu bar in title enabled, and a waste of vertical space.
Only problem making it disappear are indicators...
Maybe integrates them in launcher???

---

### Post by x-shaney-x on 2014-02-23
> **RGG said:**
> 
Only problem making it disappear are indicators...
Maybe integrates them in launcher???

They would look pretty bad in the launcher I reckon, maybe add the indicators to the titlebars like the menus?  Could be a problem on small windows but they were supposed to be doing "windicators" years ago weren't they?
Only other way I see is to have a horizontal launcher so there is space for indicators but I don't think that would fit into the unity "design".

---

### Post by mc4man on 2014-02-23
I doubt this will become default setting & seriously doubt there will be any further changes other than in addressing current bugs, found or otherwise..

---

### Post by RGG on 2014-02-23
Almost certainly not...feature freeze after all.
But is a new situation with menus in title bar per aplication that must be exposed

---

### Post by VMC on 2014-02-24
I found what looks like an anomaly. I don't have "In window title bars" set, and yet when I full screen any window then normal the screen again, I have for that window a title bar appearance.

---

### Post by mc4man on 2014-02-24
> **VMC said:**
> I found what looks like an anomaly. I don't have "In window title bars" set, and yet when I full screen any window then normal the screen again, I have for that window a title bar appearance.

bug link here (2nd
[http://ubuntuforums.org/showthread.php?t=2206904&p=12935979&viewfull=1#post12935979](http://ubuntuforums.org/showthread.php?t=2206904&p=12935979&viewfull=1#post12935979)

---

### Post by VMC on 2014-02-24
> **mc4man said:**
> bug link here (2nd
[http://ubuntuforums.org/showthread.php?t=2206904&p=12935979&viewfull=1#post12935979](http://ubuntuforums.org/showthread.php?t=2206904&p=12935979&viewfull=1#post12935979)
Thanks, I "me too" bug#1283238.

---

