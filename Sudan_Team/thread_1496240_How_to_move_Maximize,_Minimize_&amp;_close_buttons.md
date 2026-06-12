---
title: "How to move Maximize, Minimize &amp; close buttons to the right in Lucid ?"
date: 2010-05-29
forum: Sudan Team
---

### Post by zero-n on 2010-05-29
1- From terminal open gconf-edit:
```

[COLOR=Red]**gconf-edit**[/COLOR]

```2- Go to :** [COLOR=Red]apps[/COLOR]** >> [COLOR=Red]**metacity**[/COLOR] >>[COLOR=Red]** general**[/COLOR]

3- change the value of button_layout to:
```

[COLOR=Red]**:minimize,maximize,close**[/COLOR]

```4- Done ;)



Source: **full circle magazine issue 37 page 28 (Q&A)**

---

### Post by GregorDS on 2010-06-04
Didn't work for me...

---

### Post by Adntu on 2010-06-04
> **GregorDS said:**
> Didn't work for me...
try putting this:
menu:minimize,maximize,close

---

### Post by Soulcage on 2010-06-04
Its gconf-editor for me.

---

### Post by howefield on 2010-06-04
Or follow the sticky here

[http://ubuntuforums.org/showthread.php?t=1469475](http://ubuntuforums.org/showthread.php?t=1469475)

---

### Post by Adntu on 2010-06-04
> **Soulcage said:**
> Its gconf-editor for me.
thanks Soulcage, of course it is gconf-editor, I thought his problem was with the order.

---

### Post by zero-n on 2010-06-04
sorry it's 
```
gconf-editor
```

---

### Post by wojox on 2010-06-04
You guys are gonna screw up future updates with Gconf. Read howefield's post.

---

