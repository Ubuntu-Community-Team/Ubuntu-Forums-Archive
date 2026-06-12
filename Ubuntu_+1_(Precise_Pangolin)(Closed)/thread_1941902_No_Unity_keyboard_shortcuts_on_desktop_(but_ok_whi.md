---
title: "No Unity keyboard shortcuts on desktop (but ok while running any app) on 12.04 beta"
date: 2012-03-16
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Xelort on 2012-03-16
Hi there.

I can't use (almost) any keyboard shortcut while on desktop and no app running. 
However, when any application is running, the shortcuts are there again.

For example: after login, i can't call unity launcher with Super, i can't launch applications with alt+f2, i have a custom alt+f3 shortcut for gnome-terminal that also does not works, and so on. 
Until i realized how to show Unity's launcher with the mouse, i couldn't launch any app.

This way, trying to restart the computer (unity-panel is also having a bad time this days, and seems to ramdomly crash) i've found that ctrl+alt+del keyboard shortcut do work. And when the little dialog window is showing, all the other keyboard shortcuts are there again. This is happening not only with that dialog window, but with any app (firefox, gnome-terminal, synaptic, gedit...).

Also, i use a lot desktop switching. I have the compiz cube enabled, and use ctrl+alt+arrow to change desktop. When i do that, and enter into a desktop with no apps running, the problem is back again.

So, i keep calling ctrl+alt+del to be able to run apps :(
Just call the dialog window, do alt+f2, and then cancel the logout.

The keyboard is working fine during unity-greeter.

This begun a few days ago after an update. I do constantly update this pc (a netbook) so can't remember what update was.

Could it be some compiz configuration?
Maybe some Xorg-input plugin?
An Unity issue?

Don't know how to face this problem. :(

---

### Post by Xelort on 2012-03-16
up.

Tried enabling and disabling compiz "commands" plugin. No difference at all. Any idea?

---

### Post by Xelort on 2012-03-17
up.

Does anybody knows how Unity handles desktop keyboard shortcuts? Wich component? Anything? :S

---

### Post by grahammechanical on 2012-03-17
I am not sure if this is what you are looking for but the Switcher tab in the Ubuntu Unity Plugin shows what keys are bound to what actions in Unity.

You may have a conflict. I am wondering if there is a conflict between certain key bindings that Compiz Config Settings Manager (CCSM) uses to do its stuff with those used by default for Unity.

It was intended to remove the use of Ctrl+Alt+arrow key to switch workplaces. In fact for a few weeks it was another key combination that did the switching but this was later corrected in an update.

When I call up the shortcuts overlay I do no see any mention of Ctrl+Alt+arrow key. I see Ctrl+Alt+Cursor K...  What Cursor K... means i have no idea.

I think that the default keyboard short cuts for 12.04 are being altered. May be. I do not know.

I am of the opinion that the Unity adjustments in CCSM should be transferred into System Settings and the CCSM enhancements that work without a conflict with Unity be also put in System Settings. Then CCSM 
should not be allowed to work in Ubuntu until each of its effects have been proven not to cause problems.

Regards.

---

### Post by Xelort on 2012-03-18
> **grahammechanical said:**
> I am not sure if this is what you are looking for but the Switcher tab in the Ubuntu Unity Plugin shows what keys are bound to what actions in Unity.


Thanks :)
But no, that's not the data i need =/

> **grahammechanical said:**
> 
You may have a conflict. I am wondering if there is a conflict between certain key bindings that Compiz Config Settings Manager (CCSM) uses to do its stuff with those used by default for Unity.


I've had compiz commands since the beta release without any trouble. Yes, there are conflicts by default, but i don't even remember them: just resolving the conflicts was enough. 
This is a different problem: the keyboard shortcuts DO work, WITHOUT conflicts, but ONLY WHEN ANY APP IS RUNNING; the keyboard is useless when you only have the desktop on screen (wich is, frankly, absolutelly annoying).


Hmmm... maybe "display desktop" option... :-k
I remember there's a compiz option for that...



> **grahammechanical said:**
> 
It was intended to remove the use of Ctrl+Alt+arrow key to switch workplaces. In fact for a few weeks it was another key combination that did the switching but this was later corrected in an update.

When I call up the shortcuts overlay I do no see any mention of Ctrl+Alt+arrow key. I see Ctrl+Alt+Cursor K...  What Cursor K... means i have no idea.

I think that the default keyboard short cuts for 12.04 are being altered. May be. I do not know.


The shortcuts didn't changed for me so far.


> **grahammechanical said:**
> 
I am of the opinion that the Unity adjustments in CCSM should be transferred into System Settings and the CCSM enhancements that work without a conflict with Unity be also put in System Settings. Then CCSM should not be allowed to work in Ubuntu until each of its effects have been proven not to cause problems.

Regards.

Agree. Except for "should not be allowed to work in Ubuntu". I love compiz, i think it's the right way to go in terms of windows managers/decorators, and every other distro seems to be dumping compiz from their repos. :(

Thanks for the answer :)

---

### Post by mc4man on 2012-03-18
Are you allowing "file manager will draw the icons on the desktop." (manage the Desktop
If not then some keyboard shortcuts will not work till a window is open on the Desktop

If you want open dconf-editor as in screen. (path org.gnome.desktop.background 
 If enabled then disable & re-enable, if disabled then enable, & if need be then disable,  re-enable

---

### Post by Xelort on 2012-03-24
After yesterday updates, the keyboard is working again :)
Don't know what the problem was.

Anyway, thanks.

---

