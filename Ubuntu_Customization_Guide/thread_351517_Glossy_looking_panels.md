---
title: "Glossy looking panels?"
date: 2007-02-02
forum: Ubuntu Customization Guide
---

### Post by tyeracj41 on 2007-02-02
How do you get glossy looking panels like the ones in these screenshots? Is it via a theme manager, or is it in your window manager, or what? Is it just a custom image?

[http://gnome-look.org/content/pre1/50636-1.jpg](http://gnome-look.org/content/pre1/50636-1.jpg)
[http://gnome-look.org/content/pre1/43955-1.jpg](http://gnome-look.org/content/pre1/43955-1.jpg)
[http://gnome-look.org/content/pre1/45829-1.jpg](http://gnome-look.org/content/pre1/45829-1.jpg)
[http://gnome-look.org/content/pre1/32768-1.jpg](http://gnome-look.org/content/pre1/32768-1.jpg)  (especially nice)

And also, how do these people get the "Computer" menu on their panel?

[http://gnome-look.org/content/pre1/52050-1.jpeg](http://gnome-look.org/content/pre1/52050-1.jpeg)
[http://apollo.divshare.com/files/2007/01/28/81165/Desktop.png](http://apollo.divshare.com/files/2007/01/28/81165/Desktop.png)

---

### Post by macogw on 2007-02-02
You can set an image as the bg of a panel.  Maybe you can set a thing thats just a small snippet of glossy as the bg and itll repeat

---

### Post by FyreBrand on 2007-02-02
In KDE you can have some transparency and "glossy" effects.  In the examples you posted they are using the Beryl window manager.  You can tell this by the ruby like gem in the task bar.

Beryl and Compiz are window managers that have fancy compositing features.  They can do the glossy stuff, rotate your desktop like a cube or slide show, and manipulate window behavior.

---

### Post by tyeracj41 on 2007-02-02
Right, I also use Beryl. Where are the settings for the panel? Are they in the Beryl Settings Manager?

And also, why we're on the subject of Beryl, when ever I push certain button (shift, ctrl, alt, windows key, caps lock) it's makes this soft noise, and shakes the window...it's really annoying. When ever I capitalize a letter, the window shakes. How do I turn this off? In the settings manager, there were lots of shortcuts that use shift+*, but nothing with just shift. I don't know if that affects it.

---

### Post by compwiz18 on 2007-02-02
I use a semi transparent one, if you would like to try it, it is similar to [http://gnome-look.org/content/pre1/32768-1.jpg](http://gnome-look.org/content/pre1/32768-1.jpg)

Download the attachment, right click on the panel, click Properties, choose the Background tab, choose the image option, and select the file you downloaded.

---

### Post by Contrast on 2007-02-04
> **tyeracj41 said:**
> And also, why we're on the subject of Beryl, when ever I push certain button (shift, ctrl, alt, windows key, caps lock) it's makes this soft noise, and shakes the window...it's really annoying. When ever I capitalize a letter, the window shakes. How do I turn this off? In the settings manager, there were lots of shortcuts that use shift+*, but nothing with just shift. I don't know if that affects it.

It sounds like you have a hotkey set up for either window wave or shiver. Follow the arrows in the screenshot and if there is a hotkey for either of those effects, try disabling it.

---

### Post by Cybolic on 2007-02-04
Hey, you're linking to my theme! Cool! :D

That theme has the panel background image included in the tarball, so you can get it there.
The directory it's in is **/Black Plastic/gtk-2.0/panel/** in the tarball, which you can get here:
[http://www.gnome-look.org/content/show.php?content=43955]("http://www.gnome-look.org/content/show.php?content=43955")

As for the **Computer** menu, I'm guessing those people have installed the "**gnome-main-menu**" package, which provides an applet called "**Main Menu**" which you can just place on the panel.

---

### Post by tyeracj41 on 2007-02-05
These solutions are so simple. I feel like an idiot. Thanks. I actually found an applet called Ubuntu System Panel that I think is better than the main menu. Find it [here]("http://www.ubuntuforums.org/showthread.php?t=222546").

In what directory are the themes located? Is it possible to modify themes by taking parts of others, and adding to certain ones?  ie: say I really liked the Clearlooks theme, but I liked the panels from another theme. Could I take the panels from that, and add it to the Clearlooks theme?

---

### Post by tyeracj41 on 2007-02-06
Ok, thanks everybody for the help. I got my panel looking exactly the way I like it. I created the file /home/<user>/.gtkrc-2.0  and inserted the following lines
```
style "panel"
{
  fg[NORMAL]               = "#ffffff"#panel txt normal
  fg[PRELIGHT]            = "#ffffff"
  fg[ACTIVE]               = "#ffffff"
  fg[SELECTED]            = "#ffffff"
  fg[INSENSITIVE]            = "#ffffff"
  bg[NORMAL]               = "#ffffff" #Background of switcher and wl fine outline
  bg[PRELIGHT]            = "#1B1B1B"#Mouseover wl
  bg[ACTIVE]               = "#2D2D2D"#Selected wl
  bg[SELECTED]            = "#2D2D2D"#Mouseover outline
  bg[INSENSITIVE]            = "#FAFF00"#??
 base[NORMAL]            = "#ffffff"#Background of things like deskbar or 'add to panel'
  base[PRELIGHT]            = "#ffffff"#fine outline on windowlist items
  base[ACTIVE]            = "#ffffff"
  base[SELECTED]            = "#ffffff"
  base[INSENSITIVE]         = "#ffffff"

  text[NORMAL]            = "#000000"
  text[PRELIGHT]            = "#000000"
  text[ACTIVE]               = "#000000"
  text[SELECTED]            = "#ffffff"
  #text[INSENSITIVE]            = "#8A857C"
}
widget "*PanelWidget*" style "panel"
widget "*PanelApplet*" style "panel"
class "*Panel*" style "panel"
widget_class "*Mail*" style "panel"
class "*notif*" style "panel"
```

Then typed "killall gnome-panel" in the terminal.

---

### Post by Omnios on 2007-02-15
> **tyeracj41 said:**
> Ok, thanks everybody for the help. I got my panel looking exactly the way I like it. I created the file /home/<user>/.gtkrc-2.0  and inserted the following lines

Then typed "killall gnome-panel" in the terminal.

 How about a screen shot?

---

### Post by BuffaloX on 2007-03-01
> **tyeracj41 said:**
> Ok, thanks everybody for the help. I got my panel looking exactly the way I like it. I created the file /home/<user>/.gtkrc-2.0


Thanx: =D>
I've been looking for that.
Nice trick with the kilall too :)

---

