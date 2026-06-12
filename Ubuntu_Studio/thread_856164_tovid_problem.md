---
title: "tovid problem"
date: 2008-07-11
forum: Ubuntu Studio
---

### Post by hardysummer on 2008-07-11
```
Creating a black background

Creating a title image
Running convert -size 620x100 xc:none -font Helvetica -pointsize 30 -fill black -stroke black -gravity center -annotate +0+0 My Video Collection -fill #CDC0B0 -stroke gray -strokewidth 1 -annotate +1+1 My Video Collection miff:- | convert - -trim +repage -blur 0x0.4 /tmp/todisc-work.0/title_txt.png

[1 of 1] Seeking to 2  seconds in /home/user/videofile.mpg
/usr/bin/todisc: line 3201: strings: command not found
```
Even with quotations around "My Video Collection" and removing the extra "-" in the second convert would not fix it.  How do I deal with this?

---

### Post by aeiah on 2008-07-11
have you tried it usnig myvideocollection instead of words with spaces? (just for testing of course) or perhaps My\ Video\ Collection.

it may be nothing to do with that though. its saying there's a command not found on line 3201, so:

from the terminal do
```

gedit /usr/bin/todisc
```

and search for line number 3201 (you can do it from one of the menus in gedit and many other text editing programs) and see what its trying to do.

---

### Post by hardysummer on 2008-07-11
I did not input that command; that command was used automatically by todisc.  So I do not know how to add slashes nor remove spaces.

I do not see anything wrong with Line 3201 (along with 3202 and 3203):
```
if ! "${FFMPEG_CMD[@]}" 2>&1 |strings >> "$LOG_FILE";then
runtime_error "Problem creating images from the video."
fi
```
File was not modified.

---

### Post by grepster on 2008-07-23
> **hardysummer said:**
> ```

[1 of 1] Seeking to 2  seconds in /home/user/videofile.mpg
/usr/bin/todisc: line 3201: strings: command not found
```
Even with quotations around "My Video Collection" and removing the extra "-" in the second convert would not fix it.  How do I deal with this?

"strings: command not found"
You are missing the 'strings' command, which is part of binutils.  todisc in SVN has been modified to remove this unneeded dependancy.

grepper

---

