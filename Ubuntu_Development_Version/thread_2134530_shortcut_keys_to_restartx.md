---
title: "shortcut keys to restartx"
date: 2013-04-11
forum: Ubuntu Development Version
---

### Post by rburkartjo on 2013-04-11
does anyone know what they are for 13.04. alt+sysrq+k no longer seems to work. done a bunch of googling and cant seem to find a solution if one exist at all. tks/

---

### Post by dino99 on 2013-04-11
there is one to get out : ctrl+alt+backspace
but i does not know/remember of one to get in : you might need to define it if you want one

---

### Post by rburkartjo on 2013-04-11
that was an older combo that hasnt worked for the past few distros. already tried tks

---

### Post by deadflowr on 2013-04-11
You have to go into system settings > keyboard layout > options > key sequence to kill xserver and set it.
Where it used to be set enabled, for the last few releases it's been set disabled.
Just enable it.
Or for fun, try making your own.

Edit: wait nevermind, this is for Ubuntu.
No clue as for Xubuntu.

---

### Post by deadflowr on 2013-04-11
Did find this for ya,

[http://comments.gmane.org/gmane.org.user-groups.linux.boston.discuss/43603](http://comments.gmane.org/gmane.org.user-groups.linux.boston.discuss/43603)

For precise, though.
Don't know 'bout raring, but might be worth a look.

---

### Post by rburkartjo on 2013-04-12
dead tks for the link i fixed the problem by adding

setxkbmap -option terminate:ctrl_alt_bksp to my shortcut keys and then assigning whatever key combo i wanted to.

---

