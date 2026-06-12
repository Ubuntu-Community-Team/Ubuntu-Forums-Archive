---
title: "New Wine Install, New Computer, New Ubuntu"
date: 2010-06-26
forum: Wine
---

### Post by AnotherKevin on 2010-06-26
As the Title says, got a new box, new Ubuntu install (4.10 32bit) and the most recent Wine in the repository (Wine 1.0).

Been away for a long time and missed a few distros...  Before I left Ubuntu I was getting Wine working pretty well.  I had found a file that would add dlls and other needed files to get Wine rocking.  Does this ring a bell to any one?

Thanks!

---

### Post by hikaricore on 2010-06-26
What are you trying to run?  There's no point in cramming a bunch of dlls you don't need into wine..

---

### Post by AnotherKevin on 2010-06-26
I'm HOPING to install Carrara 8 Pro (3d modeling/video).

---

### Post by cogadh on 2010-06-26
Considering Carrara [hasn't really worked in Wine since version 5]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=1619"), you might be out of luck. As for the script you were asking about, you probably mean [winetricks]("http://wiki.winehq.org/winetricks"), which is already installed by default with Wine. However, hikaricore is quite correct; you really shouldn't go about installing DLLs until you have confirmed that Wine's built-in DLLs are insufficient and then you should only install those DLLs that are faulting and nothing more. 

One minor piece of advice: don't bother with the Wine version that is in the Ubuntu repos. It is the current stable version, but Wine is on the verge of a brand new stable release and the release candidate of that version is way more capable than Wine 1.0. You can find instructions on how to get the Ubuntu package for that version [here]("http://www.winehq.org/download/deb").

---

### Post by AnotherKevin on 2010-06-26
> **cogadh said:**
> 
One minor piece of advice: don't bother with the Wine version that is in the Ubuntu repos. It is the current stable version, but Wine is on the verge of a brand new stable release and the release candidate of that version is way more capable than Wine 1.0. You can find instructions on how to get the Ubuntu package for that version [here]("http://www.winehq.org/download/deb").

Thanks...  I'll check it out...

Appreciate the attention and assist!

Kevin

---

