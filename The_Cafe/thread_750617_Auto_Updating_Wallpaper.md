---
title: "Auto Updating Wallpaper"
date: 2008-04-09
forum: The Cafe
---

### Post by uzusan on 2008-04-09
I just posted this in the screenshot thread, but i thought i would post it here as well.

I've created a script (for openbox) that will update the wallpaper to show the current date everyday by adding a small green overlay (attached) onto the wallpaper then setting that as wallpaper (also attached). Now i just need to update it each month.

(If you want to use it, you'll probably need to change the paths in the script / autostart.sh file. Also, you could modify the background by erasing the photo but leaving the calendar intact).

[[IMG]http://tn3-2.deviantart.com/fs26/300W/f/2008/100/3/5/Auto_Updating_Wallpaper_by_uzusan.png[/IMG]]("http://fc06.deviantart.com/fs26/f/2008/100/3/5/Auto_Updating_Wallpaper_by_uzusan.png")


The script:

```
#!/bin/bash

D=$(date +%d)
let dlt=0


if [ "$D" -ge 1 ]; then
if [ "$D" -le 6 ]; then
let dlt=0
let vdlt=0
fi
fi

if [ "$D" -ge 7 ]; then
if [ "$D" -le 13 ]; then
let dlt=1
let vdlt=7
fi
fi

if [ "$D" -ge 14 ]; then
if [ "$D" -le 20 ]; then
let dlt=2
let vdlt=14
fi
fi

if [ "$D" -ge 21 ]; then
if [ "$D" -le 27 ]; then
let dlt=3
let vdlt=21
fi
fi

if [ "$D" -ge 28 ]; then
if [ "$D" -le 30 ]; then
let dlt=4
let vdlt=28
fi
fi

let "y = 195 + (dlt * 60)"
let "dlt = dlt * ($D - $vdlt)"
let "x = 16 + (dlt * 110)"

$(composite -compose multiply -geometry  +$x+$y today.png original.png ~/Pictures/wallpaper.png)
```

Then its called in autostart.sh using:

```
~/Pictures/wp.sh
hsetroot -center ~/Pictures/wallpaper.png &
```

---

### Post by uzusan on 2008-04-10
Made a few mistakes in the code that caused it not to work. I've updated the first post with the fixed code.

---

