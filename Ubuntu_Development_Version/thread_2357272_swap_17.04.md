---
title: "swap 17.04"
date: 2017-03-31
forum: Ubuntu Development Version
---

### Post by rrnbtter on 2017-03-31
Greetings,
Don't know if anyone has noticed but a new install of the 17.04 release will use a swap file instead of a swap partition. I suppose a manual install will still use a partition if provided but a swap file makes a lot of sense to me. My new laptop has 4G ram and only uses 700Meg.  The only need for a swap is for sleep mode, and a dynamic file makes more sense for that function then mapping off an entire swap partition.

---

### Post by flocculant on 2017-03-31
iirc - if a swap partition exists it will be used, if there is none - e.g. a clean install using whole disk - swap file is used

[http://blog.surgut.co.uk/2016/12/swapfiles-by-default-in-ubuntu.html](http://blog.surgut.co.uk/2016/12/swapfiles-by-default-in-ubuntu.html) < one of the Canonical devs

---

