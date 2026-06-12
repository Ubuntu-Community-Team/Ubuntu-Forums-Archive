---
title: "Wayland vs X11 under Flashback session"
date: 2022-03-31
forum: Ubuntu Development Version
---

### Post by kansasnoob on 2022-03-31
I haven't even looked at the flashback session since 20.04 (Focal) was released and thought since the 22.04 Beta was released I might as well take a look. Any idea which display manager would be better suited for the flashback session?

---

### Post by DuckHook on 2022-03-31
I don't actually have any real rationale for saying this, just the vague feeling that Flashback would play nicer with the old and the [s]tired[/s] tried, but I would suggest Xorg?

---

### Post by Claus7 on 2022-04-01
Hello,

the display server of flashback is X11 and I do not think that there is a choice at the time being. Both gdm3 and lightdm can be used with flashback as display managers.
ps -e | grep tty
tty7     00:00:06 Xorg

Regards!

---

