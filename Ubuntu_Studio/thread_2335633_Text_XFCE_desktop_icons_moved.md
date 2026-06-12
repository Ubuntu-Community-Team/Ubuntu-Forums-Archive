---
title: "Text XFCE desktop icons moved"
date: 2016-08-30
forum: Ubuntu Studio
---

### Post by aitomail on 2016-08-30
After the last update the text of desktop icons appears displaced from its shadow. Does anyone know how to fix it?


[ATTACH=CONFIG]270938[/ATTACH]

---

### Post by QIII on 2016-08-30
Hello!

You have posted in an English-speaking area of the Ubuntu Forums.  We would love to help, but if you want to get help in this area your questions must be presented in English.

If you cannot do that, then you should look [here]("https://ubuntuforums.org/forumdisplay.php?f=183") for an area of the Forums where you may find help in your native language.

Cheers!

---

### Post by mook765 on 2016-09-02
This looks like a problem with the theme you currently use.
Check out the name of the theme you use.
Look in /usr/share/themes/name-of-your-theme/gtk-2.0/gtkrc
In this file you will find a section which looks like this
```

style "xfdesktop-icon-view" {
    XfdesktopIconView::label-alpha = 0
    XfdesktopIconView::selected-label-alpha = 60
    XfdesktopIconVIew::ellipsize-icon-labels = 1

    base[NORMAL] = @selected_bg_color
    base[SELECTED] = @selected_bg_color
    base[ACTIVE] = @selected_bg_color

    fg[NORMAL] = @selected_fg_color
    fg[SELECTED] = @selected_fg_color
    fg[ACTIVE] = @selected_fg_color

    engine "murrine" {
        textstyle = 5
        text_shade = 0.05
    }
```
Change the value for textstyle to textstyle = 0

---

### Post by Dennis N on 2016-09-02
> **aitomail said:**
> After the last update the text of desktop icons appears displaced from its shadow. Does anyone know how to fix it?
The workaround to change to textstyle = 0 removes the text shadow completely, and if you have a light background in whole or part, could makes the text difficult to read. So instead, I chose a theme which is not affected, Greybird. 
There is a bug report at:
[https://bugs.launchpad.net/ubuntu/+source/gtk2-engines-murrine/+bug/1598316](https://bugs.launchpad.net/ubuntu/+source/gtk2-engines-murrine/+bug/1598316)
You could add your "affects me" vote to the bug report.

---

