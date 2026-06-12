---
title: "UDP port 18011"
date: 2009-09-28
forum: Security
---

### Post by mehaga on 2009-09-28
Firestarter is showing about 1 hit per second to this port, from various addresses. Anyone else?

---

### Post by skatinjj on 2009-09-28
Nope not here.  Running any programs that would use this port?

Maybe use the command 

```
top
```

to view your processes and kill any that are out of the ordinary for you if there are any.

---

### Post by mehaga on 2009-09-28
No, the port isn't open. I was just surprised by the number of hits I was getting. Anyhow, it stopped. Now its 32650 at much slower rate, several per minute.

---

### Post by lovinglinux on 2009-09-28
Probably just "ghost packets". If I were you I would remove Firestarter, install [gufw](apt:gufw) and forget about monitoring blocked connections. It's probably just a waste of time.

See this [http://ubuntuforums.org/showthread.php?p=7961725](http://ubuntuforums.org/showthread.php?p=7961725)

If you want to know more about "ghost packets" visit the BitTorrent tutorial on my signature.

---

### Post by mehaga on 2009-09-29
That's exactly what I did last night, lovinglinux. And, I wasn't really monitoring anything, I was trying to disable firestarter for local traffic, and noticed weird events. Thanks for the info :)

---

