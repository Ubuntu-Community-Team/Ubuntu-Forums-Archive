---
title: "Gnome Classic: workspace applet strange?"
date: 2012-04-05
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by keithpeter on 2012-04-05
Hello All

Using a stock 12.04 install with gnome-shell added and I have renamed the .config folder so I get defaults.

**Gnome Classic (no effects)** workspace switcher works as expected: click on workspace icon and you go to the workspace. The preferences window looks like this...

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=215485&stc=1&d=1333652345[/IMG]

**Gnome Classic (with effects)** workspace switcher looks like a small icon with two rows of two squares. Preferences window for the workspace switcher looks like this

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=215486&stc=1&d=1333652345[/IMG]

When I set preferences for four desktops in one row, and then click on another workspace in the workspace switcher applet, the panels and application windows disappear. Using Ctrl-Alt-Tab to bring up a terminal restores the panels and switches back to 'real' workspaces. The keyboard short cuts still work as normal. 

Is this a compiz thing? Is it a bug?

I'm thinking of those who migrate from 10.04 who might want a 'classic' user experience without the [extensive, and precise,  customisation that Kansasnoob has been working on]("http://ubuntuforums.org/showthread.php?t=1873765")

---

### Post by cariboo on 2012-04-05
It could very well be a problem with compiz, as it also set the number of workspaces.

---

### Post by Abandon on 2012-04-06
You have to use CCSM for getting what you want. I'm not using Classic Gnome at this moment so I can't give you a screenshot, but it is possible.

---

### Post by mc4man on 2012-04-06
> **keithpeter said:**
> 
When I set preferences for four desktops in one row, and then click on another workspace in the workspace switcher applet, the panels and application windows disappear. Using Ctrl-Alt-Tab to bring up a terminal restores the panels and switches back to 'real' workspaces. The keyboard short cuts still work as normal. 

Is this a compiz thing? Is it a bug?

Probably a bug though the overall state of Classic (compiz) is very poor. This issue has existed for quite some time
There is a way to fix this though if Classic (compiz) users also use unity-2d it will affect them there

What you need to do is open gconf-editor > apps > metacity > general & set num_workspaces to 1

or from cli
```
gconftool -s -t int  /apps/metacity/general/num_workspaces 1
```
(you **will** also need to set to 1X4 in ccsm, along the ^ 
If doing this in Classic (compiz) then if going to unity-2d there will only be 1 WS

---

