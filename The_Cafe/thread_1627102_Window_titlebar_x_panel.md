---
title: "Window titlebar x panel"
date: 2010-11-21
forum: The Cafe
---

### Post by Oxwivi on 2010-11-21
Is there a way to combine the titlebar of windows into the panel in normal GNOME just like Unity does?

---

### Post by joey-elijah on 2010-11-21
Several; you could install the Window Picker applet that netbook edition used to use or Window Applets and Indicator-App menu together

[http://gnome-look.org/content/show.php/Window+Applets?content=103732](http://gnome-look.org/content/show.php/Window+Applets?content=103732)

---

### Post by Oxwivi on 2010-11-21
Which is the simplest solution? Where do I get Window Picker?

By the way, are you part of the OMG! Ubuntu! team?

---

### Post by joey-elijah on 2010-11-21
> **Oxwivi said:**
> Which is the simplest solution? Where do I get Window Picker?

By the way, are you part of the OMG! Ubuntu! team?

Oh yeah that's a point - window picker *should* still be in the Ubuntu repos because of the 2D netbook version provided. Just search for 'window-picker' in Synaptic then add it to your gnome panel 

I'm the editor of OMG! :)

---

### Post by Oxwivi on 2010-11-21
Well, I installed the applets duo, but the titlebar is still there in addition to the separate panel.

I'll try to get window-picker then.

Awesome! Nice knowing you! :P By the way, if I may, I would like to recommend an article about the same thing as this thread. IMO, Two panels plus titlebar takes too much space away from the window. There might be others out there looking for the same thing. ;)

---

### Post by madjr on 2010-11-21
> **Oxwivi said:**
> Which is the simplest solution? Where do I get Window Picker?

By the way, are you part of the OMG! Ubuntu! team?

i think the big orange logo says it all

---

### Post by madjr on 2010-11-21
> **joey-elijah said:**
> 

I'm the editor of OMG! :)

it would sound better if you said it backwards:


*OMG! am the editor!*

:D

lol nvm

---

### Post by Oxwivi on 2010-11-23
Bump.

Okay, both solutions suggested by joey-elijah works great, except that the titlebar doesn't disappear. Any solutions?

---

### Post by NightwishFan on 2010-11-23
Run maximus as well as the above solutions, maximus removes the titlebar.
[http://packages.ubuntu.com/maverick/maximus](http://packages.ubuntu.com/maverick/maximus)

---

### Post by Oxwivi on 2010-11-23
I was just told to do that by the author of the applets duo. No other manual method, I suppose?

---

### Post by KeLa on 2010-11-23
I have removed totally the panel from top of desktop and put all necessary stuff in bottom panel. That way i can get bigger work area for widescreen laptop display.
How to do that i found from this forum.
Maybe this thread can help you to do it [http://ubuntuforums.org/showthread.php?t=856190](http://ubuntuforums.org/showthread.php?t=856190)

---

### Post by Oxwivi on 2010-11-23
Boo, maximus' effects is not permanent either!

---

### Post by jfreak_ on 2010-11-23
add maximus to your startup program list

---

### Post by jfreak_ on 2010-11-23
If you are trying to save vertical space, try this:

---

### Post by Red_Steve on 2010-11-23
> **Oxwivi said:**
> Is there a way to combine the titlebar of windows into the panel in normal GNOME just like Unity does?

The easiest way would be installing the gnome window indicator applet and if you happen to use compiz then there is an option to deactivate window decorations for maximized windows -> CompizConfig manager -> window decorations -> decoration for windows -> change any into !state=maxvert

voila. you are done.

I think the gnome applet also supports direct editing of this setting in the applet menu.
(I don't use it myself as I don't use any window control buttons)

---

### Post by Oxwivi on 2010-11-23
> **jfreak_ said:**
> If you are trying to save vertical space, try this:
How'd you get the titlebar like that?

By the way, decreasing the dock size might make it look better.

---

### Post by jfreak_ on 2010-11-23
> **Oxwivi said:**
> How'd you get the titlebar like that?



Ah that, its a theme made jurialmunkey, look at the screenshots thread. 
the dock I moved to the left and it is permanently on top and since there is nothing on the left of the titlebar, space is saved. 

I had tried the window picker applet + maximus combination earlier, but wasn't satisfied. It had the undesirable side effect of opening all apps in the maximised mode and eating a lot of resources. I like this configuration way better and it doesn't consume a lot of RAM since I have thrown out gnome-panel altogether.

If you don't like docks but would like to have gnome-panel and vertical space, then I would suggest this order in the panel:
Menu: WindowPickerApplet: globalmenu: notification area: indicator applet: logout
This comes in the panel above and you will immediately note that every possible bit of the panel is occupied.
Global menu also saves space for all gnome applications by shifting the menubar to the panel. For firefox, install the addon Hide Menubar, it will hide the menubar and will reveal itself only on pressing the alt key.

As for switching windows, create a panel to the left increase the width to about 30-35, add dockbarx to it and any app launcher if you wish.

---

### Post by jfreak_ on 2010-11-23
> **Oxwivi said:**
> 
By the way, decreasing the dock size might make it look better.

Decrease the dock size as in height or the width?

---

### Post by KeLa on 2010-11-23
Hello and wake up.
Easiest is to delete top panel and add needed stuff in the bottom panel.
No need to install anything extra stuff to heat up your computer.

---

### Post by Oxwivi on 2010-11-23
> **jfreak_ said:**
> Decrease the dock size as in height or the width?
Height.

And KeLa, that is not enough, which is why I am seeking to save more space be getting rid of the titlebar, thank you for your input.

---

### Post by Svento on 2010-12-11
Compiz can be set to undecorate. I also have a window border theme based on Dust Sand that has no title bar in maxed windows if you're interested.

I also recommend DockbarX, which displays open windows very compressed.

I have in my only panel: Main Menu; Window Buttons; GlobalMenu; DockbarX; some starters; Notification Area. In the program windows no Status Bar, no Menu Bar and no Title Bar. Running Firefox or Thunderbird, the only thing that differs from full screen is the Toolbar (which in Firefox also functions as Address bar) and that upper panel. Two effectivly used fields compared two Windows where there's normally six...

---

### Post by Oxwivi on 2011-05-11
> **Red_Steve said:**
> The easiest way would be installing the gnome window indicator applet and if you happen to use compiz then there is an option to deactivate window decorations for maximized windows -> CompizConfig manager -> window decorations -> decoration for windows -> change any into !state=maxvert

voila. you are done.

I think the gnome applet also supports direct editing of this setting in the applet menu.
(I don't use it myself as I don't use any window control buttons)
Is there a way to do this in GConf or something?

---

