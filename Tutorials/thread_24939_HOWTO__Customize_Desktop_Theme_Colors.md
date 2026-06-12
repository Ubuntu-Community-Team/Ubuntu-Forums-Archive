---
title: "HOWTO:  Customize Desktop Theme Colors"
date: 2005-04-08
forum: Tutorials
---

### Post by callahan on 2005-04-08
This is a brief guide to changing the color scheme of your Ubuntu desktop.  It is subject to change as the little theme colorizer becomes more powerful and or easier to use.

1) sudo apt-get install gtk2-engines-clearlooks
(or grab it using synaptic)

2) Go to System->Preferences->Theme, Select Clearlooks.  Hit Theme Details, Go to icons, select Human.  You can also select a Window Border of your choice.  You should end up with 'Custom theme' if you change anything.  Select 'Save Theme' and give it a reasonable name.  'MyTheme' will be used for the remainder of this guide.

3) wget [http://www.xmission.com/~callahan/clearlooks-customizer-0.05](http://www.xmission.com/~callahan/clearlooks-customizer-0.05)
(or grab it using firefox).

4) python clearlooks-customizer-0.05 > ~/.themes/MyTheme/gtk-2.0/gtkrc
(Where 'MyTheme' is the name of your customized theme.)
This should bring up a somewhat primitive gtk+ applet.  Select a reasonably light background color and a medium-dark accent color.  The clearlooks options are already set to the defaults and can be safely ignored (or not, you won't break anything).  Hit the 'Print gtkrc' button after your colors are selected.

5) Go back to System->Preferences->Theme.  Reselect MyTheme to reload it.

6) Repeat 4) and 5) until your desktop suits your mood.  If you don't like the results you can always reselect 'Human' from the Theme selector, or just create a new scheme.

Here are some quick example screenshots. In ClearCharcoal I have just picked a light grey background and a dark grey accent color off of the color picker's palette. In ClearSlash I typed in the slashdot colors (#FFFFFF and #006666).

[http://www.xmission.com/~callahan/images/ClearCharcoal.png](http://www.xmission.com/~callahan/images/ClearCharcoal.png)
[http://www.xmission.com/~callahan/images/ClearSlash.png](http://www.xmission.com/~callahan/images/ClearSlash.png)

  Michael

Edit:  bumped up clearlooks-customizer version number, added screenshots

---

### Post by justaguynpc on 2005-04-08
I have got to try this.  I was a diehard KDE user until Ubuntu.  Now that I have been exposed to Gnome, here is where I will stay.  I was a little upset that Gnome did not give me the options for "customization" as did KDE.  I posted an earlier thread along the lines of what you ahve provided here.

After dinner I will indeed give it a try, Thanx!

---

### Post by callahan on 2005-04-09
I mixed up some quick example screenshots.  In ClearCharcoal I have just picked a light grey background and a dark grey accent color off of the color picker's palette.  In ClearSlash I typed in the slashdot colors (#FFFFFF and #006666).

[http://www.xmission.com/~callahan/images/ClearCharcoal.png](http://www.xmission.com/~callahan/images/ClearCharcoal.png)
[http://www.xmission.com/~callahan/images/ClearSlash.png](http://www.xmission.com/~callahan/images/ClearSlash.png)

   Michael

---

### Post by adamthompson on 2005-10-08
This didn't work for me. When I tried step 4, I got "No such file or directory". When I used "python clearlooks-customizer-0.05 > ~/.themes/MyTheme/index.theme" I got the gtk+ applet. But after I made changes and hit "Print gtkrc" and went back to System -> Preferences -> Theme, MyTheme was gone.

Any ideas?

---

### Post by Efwis on 2005-10-08
even worse for me all I get is no such directory or file no matter what I enter.
 > edward@IABusinessProjects:~$ python clearlooks-customizer.py > ~/.themes/my_theme/gtk-2.0/gtkrc
bash: /home/edward/.themes/my_theme/gtk-2.0/gtkrc: No such file or directory
edward@IABusinessProjects:~$ python clearlooks-customizer-0.05 > ~/.themes/my_theme/gtk2.0/gtkrc
bash: /home/edward/.themes/my_theme/gtk2.0/gtkrc: No such file or directory
edward@IABusinessProjects:~$



whats is being done wrong here???

---

### Post by vayu on 2005-10-09
This has great potential.  I got the same directory not found error.  So I went to my home .themes directory and there was a mytheme directory there.  So I created a gtk-2.0 directory inside that.  Then ran your nifty python program.  It created the gtkrc file and I got the dialog, but when I saved it (printgtk button) and then reloaded the theme it didn't retain my color choices.  I went back to the python dialog and the changes weren't reflected there either.  Do you think the permissions on the gtkrc file need to be adjusted?  Currently they are 644.

---

### Post by vayu on 2005-10-09
I looked in the gtkrc file and it appears that the python program is writing my color choices into it.  It seems like the file is not being read by the system.

---

### Post by DDZ on 2011-10-28
> **callahan said:**
> This is a brief guide to changing the color scheme of your Ubuntu desktop.  It is subject to change as the little theme colorizer becomes more powerful and or easier to use.

1) sudo apt-get install gtk2-engines-clearlooks
(or grab it using synaptic)

2) Go to System->Preferences->Theme, Select Clearlooks.  Hit Theme Details, Go to icons, select Human.  You can also select a Window Border of your choice.  You should end up with 'Custom theme' if you change anything.  Select 'Save Theme' and give it a reasonable name.  'MyTheme' will be used for the remainder of this guide.

3) wget [http://www.xmission.com/~callahan/clearlooks-customizer-0.05](http://www.xmission.com/~callahan/clearlooks-customizer-0.05)
(or grab it using firefox).

4) python clearlooks-customizer-0.05 > ~/.themes/MyTheme/gtk-2.0/gtkrc
(Where 'MyTheme' is the name of your customized theme.)
This should bring up a somewhat primitive gtk+ applet.  Select a reasonably light background color and a medium-dark accent color.  The clearlooks options are already set to the defaults and can be safely ignored (or not, you won't break anything).  Hit the 'Print gtkrc' button after your colors are selected.

5) Go back to System->Preferences->Theme.  Reselect MyTheme to reload it.

6) Repeat 4) and 5) until your desktop suits your mood.  If you don't like the results you can always reselect 'Human' from the Theme selector, or just create a new scheme.

Here are some quick example screenshots. In ClearCharcoal I have just picked a light grey background and a dark grey accent color off of the color picker's palette. In ClearSlash I typed in the slashdot colors (#FFFFFF and #006666).

[http://www.xmission.com/~callahan/images/ClearCharcoal.png](http://www.xmission.com/~callahan/images/ClearCharcoal.png)
[http://www.xmission.com/~callahan/images/ClearSlash.png](http://www.xmission.com/~callahan/images/ClearSlash.png)

  Michael

Edit:  bumped up clearlooks-customizer version number, added screenshots
I think this script is a good idea ! :idea:
Is there any update to set other options like colorize_scrollbar, animation, radius, style, ETC ?
I don't know all of them, so if someone can tell me where I can find a doc about Clearlooks features : Thank you in advance ! ;)

---

### Post by s.fox on 2011-10-28
Necromancy.

Thread Closed.

---

### Post by lisati on 2011-10-28
A lot has changed in the last 6 years, it might be a good idea to start a new thread and let this one go back to sleep.

---

