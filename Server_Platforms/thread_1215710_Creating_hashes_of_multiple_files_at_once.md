---
title: "Creating hashes of multiple files at once"
date: 2009-07-17
forum: Server Platforms
---

### Post by supanatral on 2009-07-17
My question is a rather quick one. I need to create hashes for about 50 different files - is there a better way to do this other then run 50 commands all selecting different files?

---

### Post by shizzy-t on 2009-07-17
A quick for script would work.  
cd to the directory with all the files and run something like

for i in * ; do md5sum $i ; done

---

### Post by supanatral on 2009-07-17
Perfect! That works great!

---

### Post by grantemsley on 2009-07-17
Or more simply:

"md5sum *"

---

### Post by supanatral on 2009-07-17
> **grantemsley said:**
> Or more simply:

"md5sum *"

That worked too. I don't know why I didn't think of that. Thanks!

---

