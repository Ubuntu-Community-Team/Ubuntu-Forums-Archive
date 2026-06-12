---
title: "2 Things I'm not satisfied with in Unity"
date: 2012-09-10
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by deeinmetrodc on 2012-09-10
The first is the icon size on the left menu bar.  I can't set it smaller than 32.  I'd like to set it to about 24.

Second is the workspace switcher.  It belongs on the top bar, not the icon bar.  The design as it now is, is nothing short of annoying extra steps with the mouse.  The top bar has all that wasted space and the workspace switcher belongs right smack dab in the middle.  No icon nonsense, just boom - 4 workspaces to click on and cycle through, like in the gnome 2 setup.  Quick, easy, efficient - Perfection.  And you could still add some compiz effect to the switch for some flash to show it off a bit.

---

### Post by VinDSL on 2012-09-10
"Super" + "S" is a dirty n' quick workaround for your second grievance...  ;)

---

### Post by afulldeck on 2012-09-10
> **VinDSL said:**
> "Super" + "S" is a dirty n' quick workaround for your second grievance... ;)
 
Can you explain this a little further?  "Super" + "S" is meaningless to me....

---

### Post by exploder on 2012-09-10
Super + S activates the desktop switcher.

---

### Post by VinDSL on 2012-09-10
> **afulldeck said:**
> Can you explain this a little further?  "Super" + "S" is meaningless to me....Hold down the "Microsoft Winders" key with your thumb, and tap the "S" key with your bird-finger.

You should see something like this...


[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-10-sep-2012-2(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-10-sep-2012-2.png")[/INDENT]

---

### Post by wojox on 2012-09-10
> **afulldeck said:**
> Can you explain this a little further?  "Super" + "S" is meaningless to me....

Hold down the Windows key and press S

---

### Post by vexorian on 2012-09-10
> **deeinmetrodc said:**
> The first is the icon size on the left menu bar.  I can't set it smaller than 32.  I'd like to set it to about 24.

Second is the workspace switcher.  It belongs on the top bar, not the icon bar.  The design as it now is, is nothing short of annoying extra steps with the mouse.  The top bar has all that wasted space and the workspace switcher belongs right smack dab in the middle.  No icon nonsense, just boom - 4 workspaces to click on and cycle through, like in the gnome 2 setup.  Quick, easy, efficient - Perfection.  And you could still add some compiz effect to the switch for some flash to show it off a bit.
Get compiz settings manager, activate desktop wall and fiddle with the settings, it can be made to switch instantly using corner events or hotkeys. 

You can also use it in conjunction with a gnome-panel and recover the good old instant desktop switching.

I wonder if this app indicator is still working: [http://www.ubuntugeek.com/workspaces-indicator-for-ubuntu.html](http://www.ubuntugeek.com/workspaces-indicator-for-ubuntu.html)

---

### Post by mc4man on 2012-09-10
> **vexorian said:**
> 
I wonder if this app indicator is still working: [http://www.ubuntugeek.com/workspaces-indicator-for-ubuntu.html](http://www.ubuntugeek.com/workspaces-indicator-for-ubuntu.html)
Very useful though the last build was for 11.10
It works ok in 12.04 & should in 12.10, may crash every rare once & awhile, may not.

Because it's  python 2 likely one would be missing a package that's not a dep but needs to be installed - 
python-wnck

It automatically is added to the startup apps on a 6 sec delay but won't start because there is a flawed line in the .desktop ([COLOR="Blue"]indicator-workspaces.desktop[/COLOR]), that rather than fix can be removed. 

Location of the .desktop is in screen, open in a root text editor however one chooses & remove this line & it's space (or fix if inclined or even possible

AutostartCondition=GNOME /apps/indicator-workspaces/autostart

There is one other thing to be done or the indicator can produce 'unexpected' results if using rotate - ck. the indicator pref's

---

### Post by deeinmetrodc on 2012-09-10
That's very good of all of you.  Thank you!  :popcorn:

---

