---
title: "Disable Screen Blanking in Server 9.10"
date: 2010-01-15
forum: Server Platforms
---

### Post by PhrankDaChickenGeek on 2010-01-15
I am trying to disable screen blanking on my Ubuntu server 9.10
I installed Xserver and firefox and am running a full-screen web-display app. I'm using ratpoison as wm.

I've added all of the following to .xinitrc, but the screen still blanks after ~20 min.

```

setterm -blank 0 
setterm -powerdown 0 
setterm -powersave off
xset s off
xset s noblank

```

Any ideas?

---

### Post by El Jamo on 2010-03-20
I have the same problem (well, except in Debian Lenny).  I think I found a fix.  Add the following line to .xinitrc (as well as the lines you put in your post).

```
xset -dpms
```

hope it works for you (and others), this was driving me insane.

---

### Post by rabbit70 on 2010-03-26
Try this and also see [http://www.cyberciti.biz/tips/linux-disable-screen-blanking-screen-going-blank.html](http://www.cyberciti.biz/tips/linux-disable-screen-blanking-screen-going-blank.html)

```
setterm -powersave off -blank 0
```

---

