---
title: "Mouse scrolling button nearly move at all"
date: 2019-12-06
forum: Ubuntu/Debian BASED
---

### Post by Perfect Storm on 2019-12-06
Greetings,

A fresh install of eos 5.1 everything seems to work fine, but the scrolling button on the mouse. It move a little bit when I give the scrolling button a spin. Unfortunate there's no option to set the scrolling speed in eos.
The mouse is a M705 Logitech.

regards


```
orion@universe:~$ xinput list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Logitech K750                           	id=8	[slave  pointer  (2)]
&#9116;   &#8627; Logitech M705                           	id=9	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Power Button                            	id=7	[slave  keyboard (3)]
    &#8627; Eee PC WMI hotkeys                      	id=10	[slave  keyboard (3)]
    &#8627; Logitech K750                           	id=11	[slave  keyboard (3)]

```

Tried with:
```
orion@universe:~$ cat > ~/.imwheelrc
".*"
None,      Up,   Button4, 8
None,      Down, Button5, 8
Control_L, Up,   Control_L|Button4
Control_L, Down, Control_L|Button5
Shift_L,   Up,   Shift_L|Button4
Shift_L,   Down, Shift_L|Button5

^Z
[1]+  Stopped                 cat > ~/.imwheelrc
orion@universe:~$ imwheel --kill --buttons "4 5"
INFO: imwheel(pid=25241) killed.
INFO: imwheel started (pid=25309)
orion@universe:~$ 

```

I got some speed but i's not smooth as I wish.

---

### Post by Perfect Storm on 2019-12-06
Now it's working! ... and have done none in the meanwhile, strange....

---

### Post by uRock on 2019-12-08
It knew you posted about it and got scared? Glad it's fixed, though.

---

### Post by Perfect Storm on 2019-12-08
Yeah, noone mess' with me :p :p

---

