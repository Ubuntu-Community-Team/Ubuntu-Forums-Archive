---
title: "Bug? Missing Windows...Screenshot within"
date: 2012-04-07
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by terrykiwi83 on 2012-04-07
I don't know if I have come across a bug while reporting another bug.

Basically all the open windows seem borderless? is this normal? as its quite annoying?

---

### Post by santosh83 on 2012-04-07
> **terrykiwi83 said:**
> I don't know if I have come across a bug while reporting another bug.

Basically all the open windows seem borderless? is this normal? as its quite annoying?

This isn't normal, AFAIK. Either your window manager is not functioning, or a setting has been toggled for removing window decorations.

---

### Post by jonnyboysmithy on 2012-04-07
Try running ```
compiz --replace
```
That did the trick with my older pc.
I also got something like you got there when I was playing with compiz-config-settings manager. If thats the case try restarting the xserver (ctrl+alt+print screen+k)

---

### Post by terrykiwi83 on 2012-04-07
Cheers for the replies, turned out a system restart fixed it up. :)

---

### Post by jonnyboysmithy on 2012-04-07
:guitar:> **terrykiwi83 said:**
> Cheers for the replies, turned out a system restart fixed it up. :)

---

### Post by prshah on 2012-04-07
> **terrykiwi83 said:**
> 
Basically all the open windows seem borderless? 

If it happens again, it means the window-decorator has quit (or crashed, more likely).

You can easily get it back by giving the appropriate command as below in either the run (alt+F2) box, or in a terminal. In a terminal, append an ampersand (&) to the command, or else the decorator will quit when the terminal is closed.

If you face this problem in:

Unity```
unity-window-decorator --replace
```
Gnome```
gtk-window-decorator --replace
```
XFCE```
xfce-window-decorator --replace
```

The command should take effect immediately, no need to log off/on or restart.

Replacing the ENTIRE dm (eg, compiz --replace) is recommended only as a second step.

---

