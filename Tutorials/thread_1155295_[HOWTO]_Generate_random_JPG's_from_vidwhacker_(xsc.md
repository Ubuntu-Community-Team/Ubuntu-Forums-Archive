---
title: "[HOWTO] Generate random JPG's from vidwhacker (xscreensaver module)"
date: 2009-05-10
forum: Tutorials
---

### Post by lemonberry on 2009-05-10
I've replaced the Ubunutu/Gnome screensaver with the superior (IMHO) Xscreensaver, using [this guide](http://ubuntuforums.org/showthread.php?t=195557).

I like the VidWhacker module, and have it set to choose a random image from my ~/Pictures/ dir.  I wanted to save some of the funky random images it produces, so I did this:

```

while true; do /usr/lib/xscreensaver/vidwhacker -stdout | convert - `date +%s`.jpg ; echo "Generated jpg"; done

```

And random images will be saved to your current directory endlessly, until you press CTRL-C.

You'll need ImageMagick installed (sudo apt-get imagemagick) for the convert utility.

Just wanted to share :)

---

### Post by jpeddicord on 2009-05-12
Approved, thank you for your tip contribution! :)

---

### Post by Fenderian_Mayhew on 2011-12-21
this is an awesome script. did it take you a long time to make? and could it use the original image name?

---

### Post by Fenderian_Mayhew on 2011-12-22
I believe i may have immproved the code. now it can be easily stoped.  I ran in to that problem. I would run the program as a shell script, and it wouldn't always close on ctrl-c now it seem to no problem

```
while true; do /usr/lib/xscreensaver/vidwhacker -stdout | convert - `date +%s`.jpg ; echo "Generated jpg"; wait ; done
```

---

