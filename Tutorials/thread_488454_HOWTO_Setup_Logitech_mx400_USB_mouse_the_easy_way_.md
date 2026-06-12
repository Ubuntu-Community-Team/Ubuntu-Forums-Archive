---
title: "HOWTO: Setup Logitech mx400 USB mouse the easy way in Feisty"
date: 2007-06-30
forum: Tutorials
---

### Post by mulperi on 2007-06-30
There seems to be a lot of guides on how to setup a multi-button mouse.
For the excellent Logitech mx400 USB mouse I found out that all that is really needed is to:

```
sudo gedit /etc/X11/xorg.conf 
```

And the edit the correct section like this:

```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device" "/dev/input/mice" 
	Option		"Protocol" "auto"
	Option		"ZAxisMapping" "4 5"
	Option		"Emulate3Buttons" "false"
	Option		"Buttons" "9" 
	Option		"ButtonMapping" "1 2 3 6 7"
EndSection
```

Now you should have working forward/back buttons.

EDIT: Emulate3Buttons should be false

---

### Post by bodhi.zazen on 2007-07-01
Nice how to mulperi ;)

1. You should use gksudo for graphical programs :

so ... ```
gksudo gedit /etc/X11/xorg.conf
```

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)


2. You do *not* want to emulate a 3 button mouse. This feature is for two button mice and enables clicking the two buttons at the same time = push scroll wheel down.

so ... ```
	Option		"Emulate3Buttons" "false"
```

It will not hurt anything (as you can see) by emulating a 3 button mouse.

---

### Post by mulperi on 2007-10-20
Thanks for the comments, needed this tip again when I did a clean upgrade to Gutsy :guitar:

---

### Post by louisgag on 2013-01-26
Thanks, this works well for ubuntu 11.10

---

