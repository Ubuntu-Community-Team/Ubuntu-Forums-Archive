---
title: "disable suspend key on lemur ultrathin"
date: 2010-04-02
forum: System76 Support
---

### Post by huntedman on 2010-04-02
I would like to disable the FN + F4 key combination, because it falls in between volume down and mute on the keyboard. Is this possible?

disabling the suspend key in the keyboard shortcuts has no effect because it is a function key combination

---

### Post by thomasaaron on 2010-04-05
Open a terminal and run this command...

gconf-editor

In the resulting window, go to...

 apps -> gnome-power-manager -> buttons

...and change the "suspend" action to "nothing"

Did that fix it?

---

### Post by huntedman on 2010-04-05
Exactly what I was looking for,

thank you

---

