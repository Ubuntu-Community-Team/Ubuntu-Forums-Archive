---
title: "Appindicators Icons"
date: 2012-09-11
forum: Ubuntu Application Development
---

### Post by Conzar on 2012-09-11
How should icons be set for Appindicators?  Can unique icons be used or should window manager icons be used? 

On the appindicator dev page, it states:
> The icons need to use icon names from themes, direct paths to icon files are not supported. For example, icon names used with gtk_status_icon_new_from_file() won’t work.

It seems from this, that programs should use standard icons.  What are the icons that can be used?

From the example code:
```
app_indicator_set_attention_icon (indicator, "indicator-messages-new");
```

Where is "indicator-messages-new" defined?

Thanks

---

### Post by mhall119 on 2012-09-11
Have you tried using the full path to the icon file anyway?  It works for me using the Python GObject API.  Otherwise you can try using app_indicator_new_with_path to specify a custom icon_theme_path to where your app's icon are.

---

### Post by Conzar on 2012-09-11
I haven't tried full paths yet.  

Should applications use their own icons though?  Isn't the "point" of appindicators to have a unified look and feel?  

Which brings me to my next question: how does an application integrate with an existing menu?  For instance, the messaging window, how does say Pidgin & Empathy plug into the same appindicator menu?

---

### Post by mhall119 on 2012-09-12
App Indicators should use mono-color icons, but otherwise it can be specific to your application.

The Messaging Menu and Sound Menu have separate APIs if you want to integrate with them:

Messaging Menu: [http://developer.ubuntu.com/resources/technologies/messaging-menu/](http://developer.ubuntu.com/resources/technologies/messaging-menu/)
Sound Menu: [http://developer.ubuntu.com/resources/technologies/sound-menu/](http://developer.ubuntu.com/resources/technologies/sound-menu/)

---

### Post by Conzar on 2012-09-25
How do I set an icon with the full path?
Here is the function proto-type
```
AppIndicator *      app_indicator_new_with_path         (const gchar *id,
                                                         const gchar *icon_name,
                                                         AppIndicatorCategory category,
                                                         const gchar *icon_theme_path);
```

Doing something like this doesn't work:
```
    indicator = app_indicator_new_with_path ("example-simple-client","jnostromo_systemicon_gray.png",
                                             APP_INDICATOR_CATEGORY_APPLICATION_STATUS, "/home/mspeth/Projects/test/app_indicator");

```

Thanks

---

### Post by Jordiston on 2012-09-27
1.self.ind = appindicator.Indicator("MyApp",                                                                     2.                      "/home/jordiston/Pictures/Numbers/0.png",
4.                                         5.appindicator.CATEGORY_APPLICATION_STATUS)
6.        self.ind.set_status(appindicator.STATUS_ACTIVE)
7.        self.ind.set_attention_icon("new-messages-red")

the first 5 lines will let you set an icon of your choice just change the path to what you need lol.
the  6th lines sets the app status to active
the 7th changes the icon used for its specific app status, you can change it later on in the code, and can change it to your own icon as well. like 
if messages = 1	 then   self.ind.set_attention_icon("/home/jordiston/Pictures/Numbers/1.png")
i have different icons that come up for different things. i've never changed the regular active icon but i believe you should be able to change it later on in the code to.

edit: each number with a dot after it is supposed to be a new line. idk how to put code in the forums.

---

### Post by Conzar on 2012-09-27
Thanks.  That worked!

---

### Post by Conzar on 2012-10-23
> **Conzar said:**
> Thanks.  That worked!

It worked in Cinnamon but does not work in Unity :(  I would expect it to work in gnome-shell since cinnamon is based on gnome-3.

Anyways, here is the code

```

indicator = app_indicator_new_with_path ("JAppIndicator",
                                          gtkIcon,
                                APP_INDICATOR_CATEGORY_APPLICATION_STATUS,
                                          gtkIconPath);
app_indicator_set_status (indicator, APP_INDICATOR_STATUS_ACTIVE);
app_indicator_set_menu (indicator, GTK_MENU (gtkMenu));

```

gtkIcon is the file name (like test.png).  gtkIconPath is the absolute path to the file.

If you would like to try out my code (or pull the source), check out my [new project]("http://sourceforge.net/projects/jappindicator").

---

