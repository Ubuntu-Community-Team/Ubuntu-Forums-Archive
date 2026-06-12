---
title: "Where to place icons for Indicator Applet?"
date: 2010-11-06
forum: Ubuntu Dev Link Forum
---

### Post by lampak on 2010-11-06
I'm writing a program which is supposed to show an icon in the Indicator Applet. 

The indication is created in C like this: 
```

/* Indicator */
  indicator = app_indicator_new ("example-simple-client",
                                 "indicator-messages",
                                 APP_INDICATOR_CATEGORY_APPLICATION_STATUS);

```
where "indicator-messages" is a name of a sample icon. Icons seem to be stored in /usr/share/icons/<theme>/scalable/status/*.svg (and some other subfolders). 

This <theme> is the problem. Writing my app I don't know what a theme the user will use. Is there a place where I can place my icons so that they will be available globally?

EDIT: I've already tried /usr/share/icons/gnome and hicolor. Doesn't work. My app shows the icon properly only if it's in the theme folder.

---

### Post by worksofcraft on 2010-11-06
> **lampak said:**
> I'm writing a program which is supposed to show an icon in the Indicator Applet. 

The indication is created in C like this: 
```

/* Indicator */
  indicator = app_indicator_new ("example-simple-client",
                                 "indicator-messages",
                                 APP_INDICATOR_CATEGORY_APPLICATION_STATUS);

```
where "indicator-messages" is a name of a sample icon. Icons seem to be stored in /usr/share/icons/<theme>/scalable/status/*.svg (and some other subfolders). 

This <theme> is the problem. Writing my app I don't know what a theme the user will use. Is there a place where I can place my icons so that they will be available globally?

EDIT: I've already tried /usr/share/icons/gnome and hicolor. Doesn't work. My app shows the icon properly only if it's in the theme folder.

I put my icons in:
/usr/share/pixmaps
because desktop and applications menus seem to find them there automatically

---

### Post by lampak on 2010-11-07
Thanks :) It works.

---

