---
title: "Why does my nautilus open in full screen???"
date: 2008-10-15
forum: The Cafe
---

### Post by aschwerin.moses on 2008-10-15
I was playing with cairo and now even though cairo is not running, my nautilus is opening in full screen. what do i do. its so annoying.. hellllpppp....

---

### Post by rzrgenesys187 on 2008-10-15
A simple fix might be to unmaximize it, resize it and then close it.  For me it opened to the size I had it last

---

### Post by aschwerin.moses on 2008-10-16
im not talking about maximized screen.. its full screen .. no title bar visible cannot see gnome-panel.. its full screen.. the keyboard shortcuts aint working to unmaximize it....

---

### Post by chris4585 on 2008-10-16
open a terminal and type the following

```
rm .nautilus
```

```
killall nautilus
```

I'm 90% sure this will fix your problem

---

