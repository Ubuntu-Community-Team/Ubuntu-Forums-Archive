---
title: "Can a large Home directory cause slowdowns?"
date: 2009-05-05
forum: The Cafe
---

### Post by Mazza558 on 2009-05-05
I created a new user to test gnome-shell, and everything is about 5x faster than it was on my main user. The main user has a home directory which is about half full with 50gb of files.

I'm using pretty much the default compiz settings on my main, so this can't be the cause. However, I am running emerald and gnome-do, which might have something to do with it?

---

### Post by LightB on 2009-05-05
Opening the home in nautilus, of course. Some old config could also slow things down.

---

### Post by Mazza558 on 2009-05-05
> **LightB said:**
> Opening the home in nautilus, of course. Some old config could also slow things down.

I'm talking about the speed of the entire session, not just opening my home directory.

---

### Post by mips on 2009-05-05
I'm not familiar with gnome but does it have any indexing services running like strigi&nepomuk in kde?

---

### Post by Keith Hedger on 2009-05-05
The physical size of your home partition should not make any difference to session speed, what you probably have is something running at start up that is different between the two users, check what is running at start up from the session manager and/or run```
top -bn1
``` and get rid of the offending app

---

### Post by geoken on 2009-05-05
Why don't you make a new directory outside of your home directory and temporarily move everything out of your home directory.

That way you'll be able to test your theory without the influence of all the other variables that are introduced with a different account.

---

