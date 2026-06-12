---
title: "set the language of the [qwerty] keyboard"
date: 2011-09-06
forum: Ubuntu Studio
---

### Post by WasMeHere on 2011-09-06
Hello everybody,

I am very happy with Ubuntu Studio. but there is one little annoying problem, that I cannot solve.

Can you help me to set the language of the [qwerty] keyboard in Ubuntu Studio, so that it does not revert back to US. I am Swedish and I have a Swedish keyboard and I want to have the software configured accordingly. This works for all other Ubuntu flavours. But when I open the terminal in Ubuntu Studio, it has US keys, so that I have to select Swedish, even after I have pre-selected *only* Swedish keyboard and tried to save it.

Thanks in advance
Olle

---

### Post by jejeman on 2011-09-06
There shouldn't be any differance beetween Ubuntu and Ubuntu Studio on this matter.
Just make swedish keyboard layout as default, if thats what you want.
Go to keyboard preferences (system>preferences>keyboard) and in layout tab make swedish be first on top of the layout list. That will make it deafult.

---

### Post by WasMeHere on 2011-09-06
hello jejeman,

Thank you for taking your time to help me!

I agree that
> There shouldn't be any differance beetween Ubuntu and Ubuntu Studio on this matter.
 but there is. I have tried more than once to use the GUI method with only temporary success. Somehow the system forgets about it.

I have Ubuntu Studio 11.04 32-bit with gnome.

```
uname -a
Linux xw8400 2.6.38-11-generic #48-Ubuntu SMP Fri Jul 29 19:05:14 UTC 2011 i686 i686 i386 GNU/Linux

```

Is there an ascii file where the keyboard information is kept? In that case, what should I write into it, and what access should I set (with chmod)?

Looking forward to a solution
Olle

[I]Edit: I found another menu.
The menu item System--Settings--Methods för Keyboard Input--Advanced
gives me the possibility to uncheck 'Use the keyboard layout of the system'
but it did not solve my problem[/I]

---

### Post by whatthefunk on 2011-09-06
You want 
```
setxkbmap se
```

Im pretty sure that se is for Swedish.

```
setxkbmap -query
```
To see what the current keyboard layout is.

---

### Post by WasMeHere on 2011-09-06
Thanks whatthefunk,

I tried your recipe, and it helps for the moment (like the GUI method), but after restart I'm back with US keyboard. By the way, the notification on the panel says Swe, but still, it is US until I press the notification icon. I made the computer run '/usr/bin/setxkbmap se' at start-up, but no luck.

There must be something else, that overrides my setting.

Anyway, if I find a solution, I will post it.

/Olle
[I]
Edit: I entered the following lines into .bashrc
and it solves the problem with Terminal (CLI), which I use frequently.
```
# set Swedish keyboard (at least for Terminal)
/usr/bin/setxkbmap se
```
After launching Terminal, I also have Swedish keyboard in other programs :-)
[/I]

---

