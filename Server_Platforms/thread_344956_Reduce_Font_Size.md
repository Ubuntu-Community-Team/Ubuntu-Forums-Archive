---
title: "Reduce Font Size"
date: 2007-01-23
forum: Server Platforms
---

### Post by aegean on 2007-01-23
Just installed latest Ubuntu Server . The console fonts are huge. Is there a quick way (.i.e. not re-compiling kernel ) to make them smaller and fit more on screen? Tried editing menu.lst adding the vga=0x318 option but that did nothing. Is setfont the way to go? I recall doing this on a Redhat version years ago but not sure how to do it with Grub.
Thanks

---

### Post by aegean on 2007-01-23
Never mind. Found it
VGA= blah blah must be on same line as kernel params not on separate one.

---

