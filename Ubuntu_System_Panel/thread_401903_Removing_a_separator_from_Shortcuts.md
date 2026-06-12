---
title: "Removing a separator from Shortcuts"
date: 2007-04-05
forum: Ubuntu System Panel
---

### Post by Prism on 2007-04-05
Hi there,

I've accidentally added a separator to my shortcuts plugin (right click -> insert separator), and I'd like to remove it. How can it be done?

Thanks!

---

### Post by Malac on 2007-04-05
> **Prism said:**
> Hi there,

I've accidentally added a separator to my shortcuts plugin (right click -> insert separator), and I'd like to remove it. How can it be done?

Thanks!
Well spotted, that seems to be broken. :)
For now go to ~/.usp and open places.list in gedit and remove the line with the word "separator" or "space".

** EDIT:** Now fixed in SVN (Revision 243)

---

### Post by Prism on 2007-04-05
Thanks, that did it :)

---

### Post by Malac on 2007-04-05
> **Prism said:**
> Thanks, that did it :)
You're Welcome and Thanks for spotting it.

---

