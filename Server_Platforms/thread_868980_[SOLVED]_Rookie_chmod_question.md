---
title: "[SOLVED] Rookie chmod question"
date: 2008-07-24
forum: Server Platforms
---

### Post by mr.propre on 2008-07-24
At the moment I protect my image folder on my websites with a HTML file. But isn't there a way using chmod to prevent people of reading you directory (open dir) and still be able to see the files if you have the full file name.

Thanks in advance.

---

### Post by mech7 on 2008-07-24
With Apache you can turn off directory browsing with:

Options -Indexes

---

### Post by earthmeLon on 2008-07-24
Could you use .htaccess?

---

### Post by mr.propre on 2008-07-24
> **earthmeLon said:**
> Could you use .htaccess?

Yes I can :-)

---

### Post by Trail on 2008-07-25
I don't think that's related to chmod.

Supposing you disable search/list access on a directory (the 'x' for 'execute'), then you do not have the permission to see the contents of the directory, but you cannot access files by a full path inside that directory either.

---

### Post by Bachstelze on 2008-07-25
> **Trail said:**
> I don't think that's related to chmod.

Supposing you disable search/list access on a directory (the 'x' for 'execute'), then you do not have the permission to see the contents of the directory, but you cannot access files by a full path inside that directory either.

True. Setting [font="Courier New"]Options -Indexes[/font], either using .htaccess or directly in the Apache configuration, is the way to go.

---

### Post by mr.propre on 2008-07-26
Thank you for the help, it helped me allot :KS

---

### Post by K.Mandla on 2008-07-26
This has been solved, but I'm going to drop it in Server Platforms so someone searching for this information will find it in the logical place. Cheers. :D

---

