---
title: "Best way to remove orphaned packages"
date: 2005-11-25
forum: Repositories &amp; Backports
---

### Post by tropican8 on 2005-11-25
Hello all,

I was recently considering how I would go about streamlining my breezy install by removing some programs I don't need.  If this is done however, former libs and programs that were installed as dependencies of those programs will not be removed.

Now as I understand this problem I could use either deborphan or debfoster to find these orphaned libs and programs, but once one round of them is removed, packages that only had those orphaned packages as a dependency will also become orphans, requiring me to repeat the process several times.

Is there a way to find out what packages would become orphans upon removal of the ones before them?

---

### Post by teaker1s on 2005-11-25
just a suggestion if you use synaptic it will tell you what it's planning to remove as well-possibly not the indepth answer you wanted but at least you won't break anything

---

### Post by tropican8 on 2005-11-25
Sorry if I wasn't clear.  Here's an example scenario:

cpp
..libc6-dev
......libc6-pic
......libg++272-dev
......ncurses3.4-dev

I'm talking about removing libc6-pic, libg++272-dev, and ncurses3.4-dev.  If you remove those apt will not remove libc6-dev, despite nothing you use needing it anymore.  If you run deborphan, it will come up as safe (more or less) to remove.  Then you go ahead and remove it, and now cpp has no dependancies, so there's another thing you can remove.  The result is having to run deborphan or a similar program several times.

teaker1s you are talking about how synaptic will let you know it will remove libc6-dev, libc6-pic, libg++272, and ncurses3.4-dev if you select to remove cpp.

Ironically you probably wouldn't want to remove any -dev libs as they are often used to compile programs against, so this is a bad example.  I hope what I'm talking about is better illustrated though.

---

