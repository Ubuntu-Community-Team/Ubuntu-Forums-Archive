---
title: "Keep 'Places' configurable?"
date: 2006-08-07
forum: Ubuntu System Panel
---

### Post by chanders on 2006-08-07
Should we leave it as it is or let Nautilus do it for us?

---

### Post by cantormath on 2006-08-07
> **chanders said:**
> Should we leave it as it is or let Nautilus do it for us?

configurable.....
I thought that was why linux is....

---

### Post by _profox on 2006-08-07
yes, configurable is the way to go..

---

### Post by Uncle Spellbinder on 2006-08-07
Another vote for Configurable.

---

### Post by lazyd2 on 2006-08-07
> **cantormath said:**
> configurable.....
I thought that was why linux is....
+1

---

### Post by Hells_Dark on 2006-08-07
Configurable because i don't wanna the places be the same as the Nautilus Bookmarks.
I have some bookmarks i dont wanna see in the places ;)

Thanks

---

### Post by mat on 2006-08-07
I hate having a ton of configuration options. I really do. But at the same time I think that would be a wise choice here: there are people like myself who don't want to have custom places, there are others, and they can't really coexist :-)

I could live with the current situation though - using gtk bookmarks as the default and be able to customize the places afterwards.

---

### Post by mat on 2006-08-07
> **cantormath said:**
> configurable.....
I thought that was why linux is....

Well, you can configure these using the gtk filechooser, nautilus, etc. Homogeneity is the key to simplicity... Why have different definitions for your places, when you can have multiple apps sharing the same info ?

---

### Post by duff on 2006-08-09
I just want to see mounted volumes (I have 5 ssh servers mounted).

---

### Post by mat on 2006-08-09
> **duff said:**
> I just want to see mounted volumes (I have 5 ssh servers mounted).

Actually, it's pretty easy to do, I almost added this when submitting the bookmarks import patch. There is one big problem with this, however: it's going to take a lot of space :)

I'll provide a patch that does this this week-end for you to see. Might be a good candidate for a plugin when the plugin system is ready.

---

### Post by Fluffy, the jolly sheep on 2006-08-12
I think the poll is somewhat confusing because the nautilus bookmarks are 'configurable' too. Drag'n dropping to the places pane could be used to add bookmarks to the nautilus backend just as well. It's more like a choice of backend. Do you want the same bookmarks in the places pane as the nautilus ones or not so? 
Personally, I agree with mat. I don't need two different sets of bookmarks so I voted 'no'.

As for mounted volumes problem, I'd put them in a cascading menu when there are too many of them.

---

### Post by mat on 2006-08-12
I think that now that we have a plugin system, we can either move mounted volumes in a different plugin (this is what I'll release soon) or do another plugin that adds them in a cascaded menu, but I think it's not going too well with USP design.

---

### Post by mat on 2006-08-12
I also think that, with the plugin system, we can separate:
[LIST]
[*]Gnome Places
[*]USP Places
[*]GTK Bookmarks
[*]Mounted Volumes
[/LIST]

Gnome Places and USP Places would have the same name ("Places") all would have a common appearance. One problem would be that the heading would take too much room, but it's easy to make the display of headings configurables per plugin.

---

### Post by mat on 2006-08-12
I've started moving the current places plugin to a real plugin (it's currently still in the core), I will split it afterwards. Stay tuned, it will probably require a new USP release.

---

