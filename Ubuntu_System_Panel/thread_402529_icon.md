---
title: "icon"
date: 2007-04-05
forum: Ubuntu System Panel
---

### Post by phin on 2007-04-05
how do i correctly set a usp icon? im trying to set this as mine, [http://jiiprah2.googlepages.com/menu_img_black.png](http://jiiprah2.googlepages.com/menu_img_black.png) and all im getting is a red X

the link is correct, i have it downloaded into my /usr/share/icons dir, its readable.... anyhttp://jiiprah2.googlepages.com/menu_img_black.png ideas?

---

### Post by Malac on 2007-04-06
> **phin said:**
> how do i correctly set a usp icon? im trying to set this as mine, [http://jiiprah2.googlepages.com/menu_img_black.png](http://jiiprah2.googlepages.com/menu_img_black.png) and all im getting is a red X

the link is correct, i have it downloaded into my /usr/share/icons dir, its readable.... anyhttp://jiiprah2.googlepages.com/menu_img_black.png ideas?
It should be in /usr/share/**pixmaps** then you can just specify it by name menu_img_black in the Preferences window.
/usr/share/icons is for themed support, i.e. if there isn't an icon in the set of icons your theme uses and at the correct resolution you will get the red X.

Hope this helps.

---

### Post by phin on 2007-04-06
worked like a charm :)

---

