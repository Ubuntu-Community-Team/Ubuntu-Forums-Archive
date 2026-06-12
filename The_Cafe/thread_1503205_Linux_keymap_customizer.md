---
title: "Linux keymap customizer?"
date: 2010-06-06
forum: The Cafe
---

### Post by dragos240 on 2010-06-06
I want to make a "gaming dvorak" keyboard. What's a good program for doing this?

---

### Post by j.bell730 on 2010-06-06
Try getting keyboard keycodes with:
```
xev
```

Then, using those keycodes for [xmodmap]("http://wiki.archlinux.org/index.php/Xmodmap#xmodmap_within_a_shell").

You can create a shell script that maps all the keys to Dvorak, when you're gaming, then, when you log out, they'll all be back to normal.

Alternatively, have a look [here]("http://dvorak.mwbrooks.com/unix.html#xmod").

---

### Post by dragos240 on 2010-06-06
> **j.bell730 said:**
> Try getting keyboard keycodes with:
```
xev
```Then, using those keycodes for [xmodmap]("http://wiki.archlinux.org/index.php/Xmodmap#xmodmap_within_a_shell").

You can create a shell script that maps all the keys to Dvorak, when you're gaming, then, when you log out, they'll all be back to normal.

Alternatively, have a look [here]("http://dvorak.mwbrooks.com/unix.html#xmod").

Thanks! :)

---

