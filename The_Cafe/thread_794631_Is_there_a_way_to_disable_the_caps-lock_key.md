---
title: "Is there a way to disable the caps-lock key?"
date: 2008-05-14
forum: The Cafe
---

### Post by days_of_ruin on 2008-05-14
BECAUSE I HATE IT!
Seriously I did the above just by holding shift.Caps lock is just a pain!
Its too close to tab which I use a lot.
:lolflag:

---

### Post by loell on 2008-05-14
pluck it out from the keyboard..

---

### Post by days_of_ruin on 2008-05-14
I would like to do it in the software.

---

### Post by HumanAnarchist on 2008-05-14
make a file in home that is called ".Xmodmap" then you can remap you keybord as you want it :)

I got these lines in mine
```

remove Lock = Caps_Lock 
keysym Caps_Lock = Escape

```

An extra Escape is nice to have in VIM

```

man xmodmap

```

to learn more

---

### Post by perce on 2008-05-15
You can also try from the GUI:

System > Preferences > Keyboard Preferences > Layout Options > CapsLock key behavior

however it's far less flexible than xmodmap.

---

### Post by D-EJ915 on 2008-05-15
go to the keyboard section in the gnome control center and it lets you change it into a control key (I do this) like on Sun keyboards.  There's also a way to do it in xorg.conf, put in nocaps:ctrl
```

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"ca"
	Option		"XkbOptions"	"ctrl:nocaps"
EndSection
```

of course this doesn't make it a dead key, but a control is better in that position.

---

### Post by Tteddo on 2008-05-15
> **D-EJ915 said:**
> go to the keyboard section in the gnome control center and it lets you change it into a control key (I do this) like on Sun keyboards.  There's also a way to do it in xorg.conf, put in nocaps:ctrl
```

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"ca"
	Option		"XkbOptions"	"ctrl:nocaps"
EndSection
```

of course this doesn't make it a dead key, but a control is better in that position.

I have that in my xorg.conf, but it quit working (i.e CAPS LOCK came back) when I upgraded to Hardy.

---

