---
title: "Samba group in group"
date: 2009-12-18
forum: Server Platforms
---

### Post by PinkyTr4ffic on 2009-12-18
hi i would like to create the following share structure

                       subfolder1.1 
Folder --- subfolder1  subfolder1.2
           
           subfolder2   subfolder 2.1
                        subfolder 2.2


1.1 has access to its own folder, subfolder 1.1, and the folder above, subfolder1, but must not have access to 1.2, subfolder1.2.

1.2 has access to its own folder and to folder above but not 1.1 and so on ....

I created this share structure because every group has their own share which other groups aren't allowed to access but they can share files with each other by putting them in the folder above.

Is it possible to create a group in a group in samba or are there other ways of solving this?

---

### Post by xifer on 2009-12-18
> **PinkyTr4ffic said:**
> hi i would like to create the following share structure

                       subfolder1.1 
Folder --- subfolder1  subfolder1.2
           
           subfolder2   subfolder 2.1
                        subfolder 2.2


1.1 has access to its own folder, subfolder 1.1, and the folder above, subfolder1, but must not have access to 1.2, subfolder1.2.

1.2 has access to its own folder and to folder above but not 1.1 and so on ....

I created this share structure because every group has their own share which other groups aren't allowed to access but they can share files with each other by putting them in the folder above.

Is it possible to create a group in a group in samba or are there other ways of solving this?
Using standard authentication, assign membership of correct group to each user and then
```

chgrp group1 folder1 folder1.1 folder 1.2
chmod 660 folder1
chmod 600 folder 1.1 folder 1.2
chgrp group2 folder2 folder2.1 folder 2.2
chmod 660 folder2
chmod 600 folder 2.1 folder 2.2

```

or something like that

---

### Post by PinkyTr4ffic on 2009-12-18
The problem is that subfolder 1.1 is accessed by a group to.

---

### Post by xifer on 2009-12-18
> **PinkyTr4ffic said:**
> The problem is that subfolder 1.1 is accessed by a group to.


ok chmod 666 on stuff to be accessed by ALL
chmod 660 to restrict to group
chmod 600 to restrict to owner

give the same USER to everyone in each workgroup...

---

