---
title: "Repository problem and question"
date: 2005-11-29
forum: Repositories &amp; Backports
---

### Post by PatrickMay16 on 2005-11-29
Hello,

Somehow, I came to get the backports enabled in my sources.list, which I didn't actually want. Now I've realised it, several packages have been updated with versions from the backports. 
I would like to remove the backports from my sources.list file, but since some packages (including some things like the enterprise volume management system) have been updated with versions from the backports, I'm worried it could cause problems.
Would it be safe to remove the backports from the sources.list file and use synaptic to downgrade to the previous versions which weren't from the backports? Or could that break things?

Would it be fine just to remove the backports from the sources.list file and leave things as they are? 

I'm really sorry if this is a stupid question, but I'd really appreciate help with this. The reason I don't want to get stuff from the backports is because a program (Eye of GNOME) is being updated with a new version which comes from the backports. This new version doesn't work as well as the previous version. The previous version is eog 2.12.1, the new one from the backports is 2.13.2.

Thanks very much in advance to anyone who could help me.

---

### Post by matthew on 2005-11-29
Hey, Patrick.

In Synaptic you can force a certain version to be installed/used. Highlight the package you want and go to Package->Force Version and choose the version you want to have installed.

---

### Post by PatrickMay16 on 2005-11-29
[QUOTE=matthew]Hey, Patrick.

In Synaptic you can force a certain version to be installed/used. Highlight the package you want and go to Package->Force Version and choose the version you want to have installed.[/QUOTE]
Thanks. I'll do this for all the packages which were replaced with ones from the backports.

---

