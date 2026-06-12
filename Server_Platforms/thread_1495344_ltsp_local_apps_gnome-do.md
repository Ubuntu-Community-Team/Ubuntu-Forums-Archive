---
title: "ltsp local_apps gnome-do"
date: 2010-05-28
forum: Server Platforms
---

### Post by map7 on 2010-05-28
I've been using LTSP for a while now and just started to use local_apps.  

I've installed glchess under my chroot section as a small example and then added these lines to my lts.conf file:
```

[Default]
LOCAL_APPS=True
LOCAL_APPS_MENU=True
LOCAL_APPS_MENU_ITEMS=glchess
```

If I start glchess from the menu it works as a localapp.  That's all good.

If I start it from the command line using the command:
$ ltsp-localapps glchess

it works as a localapp as well.

My question is when I use gnome-do it's picking up the server copy of glchess not the local version.  Is there a way to configure gnome-do to play nicely with the local apps?

---

### Post by map7 on 2010-05-31
Now that a few days have gone past and a few client reboots I think gnome-do just had to reindex itself to pick up the localapps.  It works now.

---

