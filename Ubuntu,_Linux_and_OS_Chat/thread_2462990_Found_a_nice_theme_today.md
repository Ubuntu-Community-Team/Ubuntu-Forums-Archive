---
title: "Found a nice theme today"
date: 2021-05-31
forum: Ubuntu, Linux and OS Chat
---

### Post by dddman on 2021-05-31
[ATTACH=CONFIG]288587[/ATTACH]

gtk3

---

### Post by dddman on 2021-05-31
I see it's also gtk2 and gnome-shell

I activated gnome-shell and now in Appearance I have EFBrigthGtk and other shell themes installed.  I'm seeing very little change with the various shell themes installed.  I don't understand these shell themes.  Default setting seems to be as good as any of them.

---

### Post by wildmanne39 on 2021-05-31
gtk2 is really outdated, I doubt the themes are working or not correctly, gtk4 is now available.

---

### Post by dddman on 2021-05-31
That gave me concerns so I deleted the gtk2 folder.  Do you use any shell themes?

---

### Post by wildmanne39 on 2021-05-31
No, I do not use Gnome anymore I switched to Ubuntu Mate

---

### Post by dddman on 2021-05-31
I have ran the Mate Green Laguna theme on my gnome3 desktop and liked it.  I know nothing about gtk4 and right now I'm happy with the themes I picked up today.  Maybe these shell themes are still under development.

---

### Post by dddman on 2021-06-01
[SIZE=7]bump[/SIZE]  [SIZE=6]bump [/SIZE] bump

---

### Post by dddman on 2021-06-01
I got this thing about scroll bars being so thin.  All themes come with thin scroll bars, what's with this?

I can't do thin on my tablet, not even good at it with stylus.

So I hack the theme and fix it.  Then I find a better theme I want to run.  Again have to hack it.

Yesterday I yet again found my latest and greatest theme and now off we go to the hack shack again.  This is getting old.

---

### Post by ajgreeny on 2021-06-01
It's possible to make changes to the scroll bars of many, or maybe all, gtk3 themes by adding a simple css text file, ~/.config/gtk-3.0.gtk.css with the following content.
```
/* Set thickness of scrollbars */
.scrollbar.vertical slider,
scrollbar.vertical slider {
    min-width: 12px;
    background-color: #34a853;
}

.scrollbar.horizontal.slider,
scrollbar.horizontal slider {
    min-height: 12px;
    background-color: #34a853;
}

.scrollbar.vertical.slider:hover,
scrollbar.vertical:hover slider {
    min-width: 12px;
}

.scrollbar.horizontal.slider:hover,
scrollbar.horizontal:hover slider {
    min-height: 12px;
}

/* Include scrollbar steppers */
.scrollbar,
scrollbar {
    -GtkScrollbar-has-backward-stepper: 1;
    -GtkScrollbar-has-forward-stepper: 1;
}

scrollbar button {
min-width: 20px;
min-height: 20px;
}

```
This also adds a simple click arrow at top and bottom of the scrollbar, ie, the steppers mentioned in the file.

You can play with the dimensions of the various parts showing in that file and make changes to fit your own likes/dislikes.

---

### Post by dddman on 2021-06-01
OMG this is awesome

I shall hang a picture of you avatar on my wall for worship purposes only.

---

### Post by dddman on 2021-06-01
Works great, but I had to put it in the existing /.config/gtk-3.0/gtk.css file for it to work.

Thanks again

---

### Post by ajgreeny on 2021-06-02
I couldn't remember of another version of that file already existed but it sounds as if it did.
I'm happy you got it to work!

---

### Post by dddman on 2021-06-02
BlueBlinds theme needed some tweaking, too much white in it.

[ATTACH=CONFIG]288595[/ATTACH]

---

### Post by dddman on 2021-06-03
Ok, I now have three solid themes to run.  Green, blue and the latest is tan.  I want one more and my collection will be complete.  A dark theme with eye candy.

---

