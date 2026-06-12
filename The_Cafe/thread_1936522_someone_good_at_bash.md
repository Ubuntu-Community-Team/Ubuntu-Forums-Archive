---
title: "someone good at bash?"
date: 2012-03-06
forum: The Cafe
---

### Post by chickenPie4breakfast on 2012-03-06
on windows I used AutoHotkey and a little script combined with a keyboard shortcut so that I could make the active programs gui go to one half of the screen.  There is no AutoHotkey for Linux so I wonder if instead I could use two different bash scripts that I could link to keyboard shortucts to call them.  I would like one script to put the active window at the left half of the screen and one to put it to the right. Basically what I want is to be able to see two windows side by side with each one occupying half the screen.
any one got a bash script that can do this? I dont know bash at all.

---

### Post by diesch on 2012-03-06
Right half:
```
#!/bin/sh

set -- $(xwininfo -root| awk -F '[ :]+' '/ (Width|Height):/ { print $3 }')
width=$1
height=$2

wmctrl -r :ACTIVE: -e 0,$((width/2)),0,$((width/2)),$height

```


Left half:
```
#!/bin/sh

set -- $(xwininfo -root| awk -F '[ :]+' '/ (Width|Height):/ { print $3 }')
width=$1
height=$2

wmctrl -r :ACTIVE: -e 0,0,0,$((width/2)),$height
```

---

### Post by chickenPie4breakfast on 2012-03-06
Thanks, excellent just what I needed.

---

