---
title: "Ubuntu Gnome 15.04 with flashback no mouse"
date: 2014-11-16
forum: Ubuntu Development Version
---

### Post by Hazzabin on 2014-11-16
20 minutes ago after an update, in the 'flashback' session can no longer "see" the mouse cursor moving around the screen, If my memory is correct we had this issue back away

Mouse works ok in the basic Gnome setup

anybody got any ideas

---

### Post by tista on 2014-11-16
@Hazzabin,

Please give it a try:
```
gsettings set org.gnome.settings-daemon.plugins.cursor active false
```
Is it a Metacity/Compiz issue in the lack of "Gnome/Meta Idle Monitor" compatibility or something else?

Best Regards,
Tista

---

### Post by Hazzabin on 2014-11-16
G'day Tista

After typing in your 'code' it's telling me there is No such Schema

It would have to be a compiz issue I think as I got nothing checked to use Metacity

Is getting past my bedtime so I'll be back in my morning, thanks for suggestions

---

### Post by mc4man on 2014-11-16
You may want to try that code again or use c&p
(- I don't have ubuntu gnome but can't imagine it doesn't use g-s-d plugins such as cursor

---

### Post by Hazzabin on 2014-11-16
Tried that code this morning and it worked

thanks guys

---

