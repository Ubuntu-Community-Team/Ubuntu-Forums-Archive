---
title: "What does prelinking mean?"
date: 2009-08-31
forum: The Cafe
---

### Post by Sashin on 2009-08-31
Recently I've been reading up on two programs called prelink and preload, which aim to make a computer faster. Does anyone here know how it works?
And if it would have any affect on battery life of a laptop.

---

### Post by ssam on 2009-08-31
preloading is about reading things from the disk before they are actually needed, so that when the are needed they are already in the ram cache. this works pretty well. just install the preload package, and it will monitor what files ought to be kept in the cache. it makes programs like OOo and firefox start quicker.

prelinking is to do with shared libraries, and linking them into the binary that needs them. for several versions ubuntu has used compiler options that give you most of the benefit of prelinking without some of the problems associated with it. you probably wont see much benefit from installing prelink

---

