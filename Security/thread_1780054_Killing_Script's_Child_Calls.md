---
title: "Killing Script's Child Calls"
date: 2011-06-11
forum: Security
---

### Post by MetalheadGautham on 2011-06-11
I ran a certain script which repeatedly calls a certain script which in turn calls thousands of instances of wget one after another. (I was creating a map cache for MGMaps using scripts here: [http://www.mgmaps.com/cache/](http://www.mgmaps.com/cache/)).

Now I killed the parent script using killall. Why does it not kill all the processes called by the parent ? Is there a way for doing such an operation ?

---

### Post by MetalheadGautham on 2011-06-25
BUMP! Any solution ?

---

### Post by Lars Noodén on 2011-06-26
Would **pgrep** help?

---

