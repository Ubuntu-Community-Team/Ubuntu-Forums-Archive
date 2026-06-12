---
title: "apt-get/update and synaptic minor issue?"
date: 2005-09-21
forum: The Cafe
---

### Post by trash on 2005-09-21
I don't know if this annoys anybody else but there are minor differences in the way that these three programs handle repositories listed... editing apt with '#' with a terminal, synaptic 'add' and 'remove' and update 'add' and 'remove'.
Recently I started using the auto update more often and realized that when i 'remove' from the list of repositories, it literally removes them when i was expecting it to kindly mark said repo with a '#'. Synaptic is equally as calous for example it will lump together Ubuntu main and universe into one line which is fine, but when I remove universe it just removes the entire line and doesn't replace the deb main, just leaving the main sources.

At one time in auto update and synaptic(i think), in preferences it allowed you to check or uncheck a repo and did not delete the repo the way 'remove' does, but this is no longer the case. Anybody else bothered by this and is there maybe a better way than i am doing it?

---

### Post by Xian on 2005-09-21
[QUOTE=trash]At one time in auto update and synaptic(i think), in preferences it allowed you to check or uncheck a repo and did not delete the repo the way 'remove' does, but this is no longer the case. Anybody else bothered by this and is there maybe a better way than i am doing it?[/QUOTE]
The best way to do this in Synaptic is to highlight the desired repo and click 'Edit'. Then add or remove (Settings > Repositories) the repos from the 'Sections' box as you see fit.

To add them back just type in the repos again in the 'Sections' box.

---

### Post by trash on 2005-09-23
Yes thats what i do but it doesn't allow putting a '#' so that the repo isn't used... so lets say I have 1,2 or 3 extra repos in there they will  simply be deleted which is not very nice.
So in short I MUST use the commandline to comment those repo's i don't want to use but still would like to keep.

---

### Post by UbuWu on 2005-09-23
Don't know about hoary, but in breezy there are checkboxes to the left of the repositories in the list that allow you to enable/disable them.

---

### Post by trash on 2005-09-23
Ah ok, i'm in breezy so i guess it's just mac users would don't get the check boxes:(

---

