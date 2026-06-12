---
title: "Ctrl+Alt+D From Terminal"
date: 2006-05-21
forum: The Cafe
---

### Post by ChrisNTR on 2006-05-21
How do I use Ctrl+Alt+D from the terminal? Basically I've got brightside running and I want "Ctrl+Alt+D" to happen when ever I go to the top right, so I can give it a custom command.. but have no idea how to use Ctrl+Alt+D.

Stupid question I know..

---

### Post by Wolki on 2006-05-21
[QUOTE=ChrisNTR]How do I use Ctrl+Alt+D from the terminal? Basically I've got brightside running and I want "Ctrl+Alt+D" to happen when ever I go to the top right, so I can give it a custom command.. but have no idea how to use Ctrl+Alt+D.

Stupid question I know..[/QUOTE]

Hm, you probalby can somehow emit the key combination... anyway, if you jaust want to have your desktop show/unshow, here's how you can do it:

[LIST=1]
[*] install wmctrl
[*] save the following script in a convenient location
```
#!/bin/bash
if wmctrl -m | grep OFF
then
    wmctrl -k on
else
    wmctrl -k off
fi
```
[*] make it executable
[*] point brightside to it
[*] profit
[/LIST]

Personally, I prefer the show desktop button on the panel, as it's harder to activate by mistake, and it works immediately without showing a brightside progress window... but that shouldn't keep you from doing it, of course. :)

---

