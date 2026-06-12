---
title: "Automount removable media readonly"
date: 2009-04-07
forum: Security
---

### Post by jonolte on 2009-04-07
Hello!

The automount process for removable media like usb memory sticks should
mount the media readonly.

How to change the default readwrite behaviour?

Thanx a lot for every advice!

---

### Post by bodhi.zazen on 2009-04-08
Open a terminal

enter ```
gconf-editor
```

Under system -> storage -> default options set your options.

---

