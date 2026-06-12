---
title: "Two conkyrc's at once?"
date: 2008-04-27
forum: The Cafe
---

### Post by DAE_JA_VOO on 2008-04-27
How's it guys. I've tried to read around but nothing is quite explanitory enough.

How do i run two conkyrc files at once?

Thanks :)

---

### Post by Engnome on 2008-04-27
> **DAE_JA_VOO said:**
> How's it guys. I've tried to read around but nothing is quite explanitory enough.

How do i run two conkyrc files at once?

Thanks :)

Read the man pages for conky? (man conky in terminal) with the -c option you can specify a different conky config file.

conky -c $HOME/.conkyrc2

And conky will read .conkyrc2 instead. Maybe not what you meant but you weren't very specific.

---

