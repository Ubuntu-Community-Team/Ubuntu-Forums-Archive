---
title: "problem with themes..."
date: 2012-02-23
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by TheNessus on 2012-02-23
Since some recent update there is something wrong with custom themes. The gtk theme is light and the text is white, making it unreadable and particularly ugly. Bug happens for some themes, and not for others. doesn't happen with default themes.

anyone else has this issue?

---

### Post by TheNessus on 2012-02-23
example, with radiamentary:
(this worked perfectly before updating!)

---

### Post by dino99 on 2012-02-23
> **TheNessus said:**
> example, with radiamentary:
(this worked perfectly before updating!)

such theme is not an ubuntu one, so ask to the designer for bugs

---

### Post by TheNessus on 2012-02-23
> **dino99 said:**
> such theme is not an ubuntu one, so ask to the designer for bugs

So... again, I explain: this happened only following an update.
It did not happen before the update
it did not happen on 11.10, and 11.04.

This happens on **most** themes (I have like 50). It does not happen only on the 2 default themes and one or two others.

This can't be a problem with the designers but with something to do with 12.04.

---

### Post by dino99 on 2012-02-23
> **TheNessus said:**
> So... again, I explain: this happened only following an update.
It did not happen before the update
it did not happen on 11.10, and 11.04.

This happens on **most** themes (I have like 50). It does not happen only on the 2 default themes and one or two others.

This can't be a problem with the designers but with something to do with 12.04.

so file a report for the damaged themes

---

### Post by cariboo on 2012-02-23
There was an update to the gtk3-engines-unico (the theme engine) that could affect themes, so possibly the themes need to be updated to work with the new theme engine.

---

### Post by lucazade on 2012-02-23
> **cariboo907 said:**
> There was an update to the gtk3-engines-unico (the theme engine) that could affect themes, so possibly the themes need to be updated to work with the new theme engine.

absolutely true.. just wait some more weeks to have a stable unico release for the updated gtk stack.

---

### Post by prusswan on 2012-02-23
not sure what's going on with the themes, but gedit embedded terminal is finally usable again (it was white on white for quite some time)

---

### Post by jbicha on 2012-02-23
GTK 3.3 has made a whole lot of theming changes this release cycle. Those changes should be done for a while now, but it will take themes a while to catch up. Of course, there isn't a stable Linux distribution release that has GTK 3.3/3.4 yet.

---

### Post by prusswan on 2012-02-24
how is the theme used for gedit plugins? embedded terminal was working briefly yesterday, until it reverted to white on grey again with the latest updates today

---

