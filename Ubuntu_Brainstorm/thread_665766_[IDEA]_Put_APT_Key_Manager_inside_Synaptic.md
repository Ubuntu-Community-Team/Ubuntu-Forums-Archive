---
title: "[IDEA] Put APT Key Manager inside Synaptic"
date: 2008-01-12
forum: Ubuntu Brainstorm
---

### Post by sicofante on 2008-01-12
It sounds like a pretty obvious thing to me, but maybe I'm missing something?

---

### Post by 23meg on 2008-01-12
Why, when there's Settings / Repositories / Authentication?

---

### Post by smartboyathome on 2008-01-12
Yeah, I noticed that, but it wasn't until a couple months ago, and before that I also used APT Key Manager. Maybe make a way to have it more noticable?

---

### Post by sicofante on 2008-01-12
> **23meg said:**
> Why, when there's Settings / Repositories / Authentication?
Because the interface in Settings / Repositories / Authentication is asking for a file when I just have a string. That's exactly why I had to install Apt Key Manager and after seeing how it works, came here and posted this (obvious?) idea.

---

### Post by 23meg on 2008-01-12
If you think it should accept a string, file a bug that indicates that this option should be available. Tacking on another GUI for the same task will be redundant.

---

### Post by sicofante on 2008-01-12
Thanks for your suggestion.

Yes, it's redundant to have a specific app for doing what obviously Synaptic is trying to do.

This IDEA is a suggestion for Synaptic to integrate the functionality of Apt Key Manager in the next Ubuntu release, Hardy Heron.

---

### Post by 23meg on 2008-01-13
You're welcome. Just to make sure we're on the same page: it's not redundant to have a specific separate app, as long as that app is in Universe, and thus, optional. What I'm saying is that having two GUIs for the same task inside Synaptic or software-properties-gtk would be redundant. What should happen is that Settings / Repositories / Authentication (a.k.a. software-properties-gtk) should have a separate button for importing a string, and if really needed, other extra functionality provided by Apt Key Manager that it doesn't provide.

---

