---
title: "How to get the keyboard changer icon on GS 3.8.2 panel?"
date: 2013-06-08
forum: Ubuntu Development Version
---

### Post by Chanath on 2013-06-08
How to get the keyboard layout changer icon on GS 3.8.2 panel? It was there in GS 3.4, but lost in GS 3.6 & 3.8. In the Unity desktop, it is there on the top panel. Does anyone know how to get this keyboard layout changer working in Gnome-shell? When I need to write in another language, I usually logout and go to Unity.

---

### Post by zika on 2013-06-08
I use simple CLI bypass:
```
alias rs='/usr/bin/setxkbmap -option compose:rwin,lv3:ralt_switch,grp:sclk_toggle,grp_led:scroll,eurosign:5 rs,us,rs -variant latin, '
```
It works everywhere... ;)

---

### Post by Chanath on 2013-06-08
> **zika said:**
> I use simple CLI bypass:
```
alias rs='/usr/bin/setxkbmap -option compose:rwin,lv3:ralt_switch,grp:sclk_toggle,grp_led:scroll,eurosign:5 rs,us,rs -variant latin, '
```
It works everywhere... ;)

Meaning this would give me US or Russian keyboard layouts. I did that, but no icon had appeared in the GS top panel. I would like Polish too. Could you explain how to use it?

---

### Post by zika on 2013-06-08
> **Chanath said:**
> Meaning this would give me US or Russian keyboard layouts. I did that, but no icon had appeared in the GS top panel. I would like Polish too. Could you explain how to use it?You can choose layout You want... You can choose key (combo) tha You wish to change layout... In example given You get Serbian-latin, US, Serbian-cyrillic and Scroll-Lock as a switch-key... Also You get rAlt as compose key, ScrollLockLED as indicator...```
man setxkbmap
```... Never let me down...
No GUI indicator, alas...

---

### Post by Chanath on 2013-06-08
> **zika said:**
> You can choose layout You want... You can choose key (combo) tha You wish to change layout... In example given You get Serbian-latin, US, Serbian-cyrillic and Scroll-Lock as a switch-key... Also You get rAlt as compose key, ScrollLockLED as indicator...```
man setxkbmap
```... Never let me down...
No GUI indicator, alas...

Well, I still don't know how to use that. For the moment, I go back to Unity, when I want to use another language. It was there in GS 3.4, and don't understand why it was taken off--we are multi-language people here.

---

### Post by zika on 2013-06-08
Try this in Your Terminal:
```
/usr/bin/setxkbmap -option compose:rwin,lv3:ralt_switch,grp:sclk_toggle,grp_led:scroll us,ru
```
and try to change language with ScrollLock...
Mine is with three entries since we have latin and cyrillic version...

---

### Post by xc3RnbFO8P on 2013-06-08
Setting> Region & Language> Layouts> Options> Key(s) to change layout

---

### Post by Chanath on 2013-06-08
> **zika said:**
> Try this in Your Terminal:
```
/usr/bin/setxkbmap -option compose:rwin,lv3:ralt_switch,grp:sclk_toggle,grp_led:scroll us,ru
```
and try to change language with ScrollLock...
Mine is with three entries since we have latin and cyrillic version...

**&#1061;&#1074;&#1072;&#1083;&#1072; &#1090;&#1080; &#1087;&#1091;&#1085;&#1086;!**
I must try to read Serbian online newspapers. Sounds very much near Russian.:)

---

### Post by Chanath on 2013-06-08
> **Ringi said:**
> Setting> Region & Language> Layouts> Options> Key(s) to change layout

Thank you! 
It worked. :)

---

### Post by zika on 2013-06-09
> **Chanath said:**
> **&#1061;&#1074;&#1072;&#1083;&#1072; &#1090;&#1080; &#1087;&#1091;&#1085;&#1086;!**
I must try to read Serbian online newspapers. Sounds very much near Russian.:)
&#1053;&#1077;&#1084;&#1072; &#1085;&#1072; &#1095;&#1077;&#1084;&#1091;... ;)
(Not at all)

---

