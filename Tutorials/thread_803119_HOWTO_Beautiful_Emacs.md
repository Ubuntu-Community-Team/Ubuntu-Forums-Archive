---
title: "HOWTO: Beautiful Emacs"
date: 2008-05-22
forum: Tutorials
---

### Post by saaz on 2008-05-22
The standard emacs package for Hardy looks incredibly horrible. The main reason for this is the ugly font it uses. The ugliness is exacerbated on large monitors. Anti-Aliased fonts improve the look tremendously. Unfortunately, the standard package doesn't support this...but the 'emacs-snapshot' package does. You'll need the universe repository enabled and then from a terminal:

```
apt-get install emacs-snapshot
```

Edit the file: ~/.Xdefaults (which probably doesn't exist yet)
Add the following line to this file:
```

Emacs.font: Monospace-10
```

Monospace-10 is one of the AA fonts. 

Either restart X or just type the following form the terminal:

```
xrdb -merge ~/.Xdefaults
```

When you start emacs make sure you run "emacs-snapshot-gtk" and not the standard package, "emacs" in case you also have that installed.

I'd also recommend setting up a color theme with the color-theme library. Get it by typing this in a terminal:

```
apt-get install emacs-goodies-el
```

Start emacs and do (M-x = hit the esc key and then the x key, RET = the Enter key):
```
M-x load-library RET
color-theme
```

Then do:
```
M-x color-theme-select
```

Hit RET on each theme name to see it, 'd' to get a description including the real name of the theme.

Once you have a theme you like, you can put it in your ~/.emacs so it'll load every time. If I want the "Gnome 2" theme, I'd put:

```
(require 'color-theme)
(color-theme-gnome2)
```

ColorTheme site:
[http://www.emacswiki.org/cgi-bin/wiki/ColorTheme](http://www.emacswiki.org/cgi-bin/wiki/ColorTheme)

---

### Post by z0mbie on 2008-05-22
Screenshots pls?

---

### Post by saaz on 2008-05-23
This is using the "Monospace 10" AA font and the "Gnome 2" ColorTheme.

---

### Post by stairwayoflight on 2008-09-01
For a cleaner look, you can add
```
(scroll-bar-mode -1)
(menu-bar-mode -1)

```which will disable the scroll bar and menu bar respectively. You can always turn them back on if you need them, but I found leaving them on I was always tempted to use the gui instead of the key commands, which is where emacs' strength really lies.

---

### Post by unix1980 on 2008-09-01
Thanks saaz.  I've been using emacs22-nox because the X version looked so bad.  Now I have a choice.

---

### Post by frecon on 2008-11-15
[This is Monospace-10 in emacs.]("http://img230.imageshack.us/my.php?image=skrmbildemacssnapshotgthx2.png")

[This is also Monospace-10 but in gedit.]("http://img253.imageshack.us/my.php?image=geditui2.png")

[Here's emacs, gedit and the terminal side by side for comparison.]("http://img222.imageshack.us/my.php?image=skrmbildii7.png")


Why is the font so thick in emacs? I want it to be small and smooth like it's shown in gedit.

---

### Post by unutbu on 2008-11-15
I don't know the solution to your problem with certainty.
I believe the answer has to do with hinting. Full hinting yields thin font strokes, while no hinting yields thick font strokes. 

Hinting can be set in at least 3 different places and I'm not sure how these settings interact. 

The first place to set full hinting is by clicking on System>Preferences>Appearance>Fonts tab>Details.

The second place is to edit or create a file called ~/.fonts.conf and put this in it

```
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
<match target="font" >
<edit mode="assign" name="rgba" > <const>rgb</const> </edit>
<edit mode="assign" name="hinting" > <bool>true</bool> </edit>
<edit mode="assign" name="antialias"> <bool>true</bool> </edit>
<edit mode="assign" name="autohint" > <bool>false</bool> </edit>
<edit mode="assign" name="hintstyle"> <const>hintfull</const> </edit>
</match>
</fontconfig>
``` If you do "man 5 fonts.conf" you'll see that Fontconfig reads this file.

The third place where hinting can be configured is /etc/fonts/conf.avail. These, I believe are system-wide font configuration files. I don't know enough to say with confidence how to edit these files, but if you look in /etc/fonts/conf.avail/53-monospace-lcd-filter.conf you might see something like
```

    <edit name="hintstyle" mode="assign">
      <const>hintfull</const>
```

Which I think means that monospace fonts are rendered with full hinting by default. 

So maybe if you set all hintstyle to hintfull in all three locations, maybe emacs will get the message.

---

### Post by frecon on 2008-11-16
> **unutbu said:**
> 
The second place is to edit or create a file called ~/.fonts.conf and put this in it


Thanks, that took away the thickness. But the font is still not quite right. The font is still too big. Look at this new screenshot and you'll see it compared to Gedit.
[[IMG]http://img220.imageshack.us/img220/3120/skrmbildgx3.th.png[/IMG]](http://img220.imageshack.us/my.php?image=skrmbildgx3.png)[[IMG]http://img220.imageshack.us/images/thpix.gif[/IMG]](http://g.imageshack.us/thpix.php)

---

### Post by unutbu on 2008-11-16
Check that you have these 2 lines in  ~/.Xdefaults:
```
Emacs*Font: Monospace-10:antialias=True
emacs.FontBackend: xft

```
Then run ```

xrdb -merge ~/.Xdefaults
```
This will set your font size to 10pt Monospace.

If for some odd reason the above does not work for you, then you could also try putting this in your .emacs file:
```

(set-default-font "Monospace-10")
```

---

### Post by frecon on 2008-11-17
Still no luck. It still look the same as the last screenshot.

---

### Post by f4hy on 2008-11-20
Thank you so much. I have been fighting with gnuemacs for a while now to get it to look nice. This solved all of my problems!

---

### Post by yoav on 2008-11-20
> **stairwayoflight said:**
> For a cleaner look, you can add
```
(scroll-bar-mode -1)
(menu-bar-mode -1)

```which will disable the scroll bar and menu bar respectively. You can always turn them back on if you need them, but I found leaving them on I was always tempted to use the gui instead of the key commands, which is where emacs' strength really lies.

For a faster load time you can disable those in ~/.Xdefaults (or ~/.Xresources) instead of in ~/.emacs, with the lines:
```

emacs.menuBar: off
emacs.toolBar: off

```
and to get rid of the scroll bar add
```
 
emacs.verticalScrollBars: off

```

---

### Post by Eoghan Murray on 2009-01-24
My anti-aliased fonts disappeared in Emacs on the upgrade to Intrepid.  Does anyone know any techniques to get back antialiasing on intrepid?

---

### Post by robsol on 2009-03-28
Many thanks!  

I installed Ubuntu 8.10 Intrepid last week and had much trouble getting somewat readable emacs fonts.  Your recipe to transit to emacs-snapshot-gtk with Monospace-10 is a godsent.  

There was a secondary recipe to put 
  Emacs.menuBar: off 
etc choices in .Xdefaults rather than specify them in .emacs: that works, but Emacs needs to be spelled with a capital.

A big remaining problem I have is that emacs interferes devastatingly with the Gnome workspace shifter: use of any key combination (defined by key shortcuts) to switch to te workspace on the left or the right of the current one in an emacs window freezes my laptop (Tosphiba Portege R600).  I guess I should put this bug in another thread but my lore in this is yet small.

---

### Post by jpkotta on 2009-03-29
> **frecon said:**
> Still no luck. It still look the same as the last screenshot.

How about changing the font size?
```
Emacs*Font: Monospace-10:antialias=True:pixelsize=8
```

---

### Post by Wittaker on 2010-07-11
Thanks a ton for this tutorial!

---

### Post by gleedadswell on 2012-02-06
These days there seems to have been a slight change to all this.

If you just

```
apt-get install emacs-emacs-goodies-el
```

then in emacs

```
M-x load-library RET
color-theme
```

then

```
M-x color-theme-select
```

and pick one (by the way, it took me a while to figure out how to select a colour.  I tried clicking and double clicking in the color-theme-select screen.  Finally I figured out that you need to put the cursor on a color theme name and hit enter to select it).

Finally if you add

```
(require 'color-theme)
(color-theme-<theme-name>)
```

to your .emacs file the next time you start emacs you'll get the error

```
Symbol's function definition is void: color-theme-<theme-name>
```

This is easy to fix.  You now need the command

```
(color-theme-initialize)
```

after the require 'color-theme command in your .emacs file.

---

