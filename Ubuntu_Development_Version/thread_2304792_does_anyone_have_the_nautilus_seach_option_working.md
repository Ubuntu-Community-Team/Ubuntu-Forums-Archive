---
title: "does anyone have the nautilus seach option working?"
date: 2015-11-30
forum: Ubuntu Development Version
---

### Post by ventrical on 2015-11-30
Perhaps it's just me but why is the nautilus search option always busted from cycle to cycle?

---

### Post by sammiev on 2015-11-30
I just tried it with Ubuntu-Gnome and it worked here.

---

### Post by ventrical on 2015-11-30
Looks like I have a really bad install of the last cycle on another machine. I just checked and , yes, it is working on other installs.

My bad.

Thanks..

---

### Post by sgage on 2015-11-30
> **ventrical said:**
> Perhaps it's just me but why is the nautilus search option always busted from cycle to cycle?

Working fine here.

---

### Post by dino99 on 2015-11-30
> **ventrical said:**
> Looks like I have a really bad install of the last cycle on another machine. I just checked and , yes, it is working on other installs.

My bad.

Thanks..

Does not think about a bad installation; i also have seen this many times (3.14 -> 3.16 -> 3.18 upgrades; but not with intermadiate ones). With the next opened session it usually works. I would say its a bug somewhere

---

### Post by grahammechanical on 2015-11-30
It will not find system files unless we have opened "computer". So, the "All files" button is really the same as the "Home" button. It does not search in root. And this is on an install without a separate /home partition.

Regards.

---

### Post by ventrical on 2015-11-30
> **grahammechanical said:**
> It will not find system files unless we have opened "computer". So, the "All files" button is really the same as the "Home" button. It does not search in root. And this is on an install without a separate /home partition.

Regards.

Ahhh... thanks. So I am wrong when I assume it is searching globally by default. "All files" is , for all intents and purposes,  the English definition for 'global' and it is logically assumed. So it is a bug. This is what we get  with tweaker's syndrome! :)

Regards..

---

### Post by grahammechanical on 2015-11-30
If we open "computer" then "All files" will search outside root. If we open any folder, then "All files" will search from /home downwards but not in root. I guess there is a logic behind it - users don't mess with system files!

---

### Post by ventrical on 2015-11-30
> **grahammechanical said:**
> If we open "computer" then "All files" will search outside root. If we open any folder, then "All files" will search from /home downwards but not in root. I guess there is a logic behind it - users don't mess with system files!

Yes .. even if "All files" is "No files" at all. :)

Regards..

---

### Post by styx4 on 2015-11-30
Is there any way to have it search inside root even if you start outside? I don't know how practical that would
be but this is completely out of curiosity. Cheers.

---

### Post by mc4man on 2015-11-30
nautilus search searches recursively from the directory the search is made from, period.

---

