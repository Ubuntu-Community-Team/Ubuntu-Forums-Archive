---
title: "Move Vertical Scrollbar to Left?"
date: 2007-08-07
forum: The Cafe
---

### Post by Mike-97470 on 2007-08-07
I don't seem to find a way to flip the vertical scrollbar from the right edge to the left edge of windows.

Very strange!

I going to claim that maybe 75% of viewing focus is on the left 1/2 of the screen, for web browsing at least.  == The scrollbar should be located on the left or relocatable to the left.  Sure the kb arrow buttons can do scrolling most of the time, but frequently the mouse has to find the scrollbar.  (you know this is a problem when your eye and neck muscles are getting sore ;-))

It's my opinion that the scrollbar is on the right because most people are right handed, a valid reason for touchscreens, but a bogus one for mice.  Not very intelligent.

---

### Post by kanem on 2007-08-07
I don't have time to explain, but the solution is supposed to be in [here](http://bugzilla.gnome.org/show_bug.cgi?id=157025). I'll be back on in a few hours if this isn't clear.

---

### Post by Mike-97470 on 2007-08-07
Thanks kamen,
Yes, it looks like the bug fixers have  a solution, but I don't seem to be able to find the right gtk file to modify.  Maybe you can help with that. 

The bug fixers seem to think this is about lefthandedness--that kind of thinking is what got the scrollbar on the right in the first place.   It's more important to design the gui based on where the user's eyeballs are likely to be--on the left most of the time.

Also,  I'm hoping to find this showing up in System/Preferences rather than a hack.  Let's get that fix bubbled up into the system!

---

### Post by kanem on 2007-08-07
the .gtkrc-2.0 file doesn't exist by default. You can just make it with gedit and put it in your home folder.  You can do lots of nifty things with this file. Here's what's in mine.
```

gtk-scrolled-window-placement = top-right

gtk-menu-popup-delay=0

gtk-icon-sizes = "panel-menu=26,26:gtk-large-toolbar=26,26"
#gtk-icon-sizes = "gtk-large-toolbar=16,16:panel-menu=16,16:gtk-button=16,16:gtk-dialog=16,16:gtk-menu=16,16"
#gtk-font-name = "EaglefeatherFormalRegular 14"

style "my_color"
{
#font_name = "URW Gothic L Book 12"
fg[NORMAL] = "#ffffff"
}

widget "*PanelWidget*" style "my_color"
#widget "*PanelApplet*" style "my_color"
widget_class "*.Panel*GtkLabel" style "my_color"
```

Which does things like choose the font and font color for certain items and pick icon size for some menu bars.

As well as put the scroll bar on the left. Unfortunately, as I've just found out, it doesn't work for all applications. At least not for me. I'm running Gutsy right now, so things may be a little screwy.

---

### Post by tcpip4lyfe on 2007-08-07
Scroll bars ALWAYS go on the right!  Blasphemer! :)

---

### Post by markp1989 on 2008-10-08
> **kanem said:**
> the .gtkrc-2.0 file doesn't exist by default. You can just make it with gedit and put it in your home folder.  You can do lots of nifty things with this file. Here's what's in mine.
```

gtk-scrolled-window-placement = top-right

gtk-menu-popup-delay=0

gtk-icon-sizes = "panel-menu=26,26:gtk-large-toolbar=26,26"
#gtk-icon-sizes = "gtk-large-toolbar=16,16:panel-menu=16,16:gtk-button=16,16:gtk-dialog=16,16:gtk-menu=16,16"
#gtk-font-name = "EaglefeatherFormalRegular 14"

style "my_color"
{
#font_name = "URW Gothic L Book 12"
fg[NORMAL] = "#ffffff"
}

widget "*PanelWidget*" style "my_color"
#widget "*PanelApplet*" style "my_color"
widget_class "*.Panel*GtkLabel" style "my_color"
```

Which does things like choose the font and font color for certain items and pick icon size for some menu bars.

As well as put the scroll bar on the left. Unfortunately, as I've just found out, it doesn't work for all applications. At least not for me. I'm running Gutsy right now, so things may be a little screwy.

thankyou!

---

