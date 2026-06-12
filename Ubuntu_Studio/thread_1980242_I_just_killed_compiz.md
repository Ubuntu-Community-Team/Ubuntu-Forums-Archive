---
title: "I just killed compiz"
date: 2012-05-14
forum: Ubuntu Studio
---

### Post by mjhouska on 2012-05-14
I  right clicked on desktop>change desktop background>visual effects and selected extra(yeah i know stupid move) and compiz died never to return. 

i am running studio 10.04 lts  with proprietary drivers (fglrx) activated.

i have reactivated(reinstalled?) the drivers and reinstalled compiz. still no joy.

please help

---

### Post by mjhouska on 2012-05-14
i get the four panel switcher in stead of cube. wobbly window dont  wor either even though both are checked.

---

### Post by wilee-nilee on 2012-05-14
Set it where it was when it worked and logout and back in or reboot, or run in the terminal ```
compiz --replace & exit
```

All three should restart compiz I vote for the full reboot.

---

### Post by mjhouska on 2012-05-14
still nothin. i noticed however that the number of desktops is set to one and cannot be moved.

---

### Post by mjhouska on 2012-05-14
without using & exit i got:
starting gtk-window-decorator
compiz (cube) - Warn: Failed to load slide: /usr/share/gdm/themes/Human/ubuntu.png

---

### Post by wilee-nilee on 2012-05-14
> **mjhouska said:**
> still nothin. i noticed however that the number of desktops is set to one and cannot be moved.

Have you just tried a reboot?

---

### Post by mjhouska on 2012-05-14
i don't get it. a png file disappeared?

---

### Post by mjhouska on 2012-05-14
yes i   rebooted

---

### Post by mjhouska on 2012-05-14
should i try the command with sudo?

---

### Post by wilee-nilee on 2012-05-14
> **mjhouska said:**
> should i try the command with sudo?

No, sudo is not needed, here is some info on 10.04 running compiz.

[http://askubuntu.com/questions/4176/how-to-reset-default-window-effects](http://askubuntu.com/questions/4176/how-to-reset-default-window-effects)

---

### Post by mjhouska on 2012-05-14
I rebooted again still no go

---

### Post by mjhouska on 2012-05-14
i have no opton for  custom. will try in stalling simple- cssm then.

---

### Post by mjhouska on 2012-05-14
did not have to instal simple cssm after all!  i selected extra then it searched for drivers. then i  selected keep settings ( i think, i forget) then i went into cssm and enabled cube again and it worked!  thanks for the help. back to normal now.

---

### Post by mjhouska on 2012-05-14
incidentally, all three options under visual effects are unselected as they were before.
now i know to stay away from this tab! whew!

---

### Post by wilee-nilee on 2012-05-14
> **mjhouska said:**
> did not have to instal simple cssm after all!  i selected extra then it searched for drivers. then i  selected keep settings ( i think, i forget) then i went into cssm and enabled cube again and it worked!  thanks for the help. back to normal now.

Cool, enjoy. :)

---

