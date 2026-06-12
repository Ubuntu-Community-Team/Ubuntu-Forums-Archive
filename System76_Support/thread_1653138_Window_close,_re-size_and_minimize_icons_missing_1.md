---
title: "Window close, re-size and minimize icons missing 10.04 on star1"
date: 2010-12-26
forum: System76 Support
---

### Post by david12 on 2010-12-26
I did a clean install of 10.04 on my daughter's star1.  (9.10 had been the previous OS.) All seems to have gone well except for the fact that it is no longer possible to resize, close, or minimize open windows in Nautilus or Firefox using the familiar 'X', '_', and box icons which appear in the upper left (or right) corner of each window. OpenOffice windows retain the 'X', but lack the '_' and box.

So wassup with that? :-&  Is this  intentional, or is it an installation error of some kind?  If an error, how can these icons be restored?

Thanks for your help.

---

### Post by Dave_L on 2010-12-26
This may correct it:

Run gconf-editor from a command shell, and add Firefox and Nautilus to the key /apps/maximus/exclude_class.

---

### Post by david12 on 2010-12-26
Thanks, Dave_L.  Seems the problem was my misunderstanding and not a configuration issue.  Double-clicking on the gray bar above the window shrinks the window slightly and restores the icons. Thanks for the reply.

---

### Post by planetpatrick on 2011-02-15
how do u do that?

---

### Post by isantop on 2011-02-16
What are you having trouble with?

---

