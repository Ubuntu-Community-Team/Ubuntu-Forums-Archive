---
title: "Truecrypt and Thumbnails"
date: 2008-07-17
forum: Security
---

### Post by spvo on 2008-07-17
Hello,

I have a truecrypt volume filled with pictures that I, for several reasons, do not want to be visible without a password.  Every once in a while I would mount the volume, look at the files, and unmount assuming the pictures were safe.  Well, I recently realized that each time I mounted the file gnome would go through and generate thumbnails for each image and store it, unencrypted, in .thumbnails.

I realize that in the future I can just turn of the thumbnail generation before I mount the file, but is there any more elegant solution?  For example, is there any way to tell it not to generate thumbnails for a removeable volume?

Also, can anyone think of other places gnome, or 'eye of gnome', might store or cache the images?

Thanks

---

### Post by /etc/init.d/ on 2008-07-18
GNOME is chock full of information leakage.  Recently used lists, thumbnail caches, the list is never-ending.  A safe bet is to blank the file (or shred it and "touch" the file again) and remove write permissions.

The data leakage doesn't necessarily end there, though.  Some apps will deliberately correct permissions on files so that they can continue to track your history.  In this case, you might want to delete the offending history file and create a directory of the same name.  This should quash the app's attempts to track you.

A lot of tracking crap seems to get saved in .gnome2 (I think that's the name).  You might want to check there.

---

### Post by hyper_ch on 2008-07-18
you could fully encrypt your system so it won't matter anymore ;)

---

### Post by Biochem on 2008-07-18
> **hyper_ch said:**
> you could fully encrypt your system so it won't matter anymore ;)

That would work if it's not a shared system.

I wonder if looping .thumbnail to /dev/null might work??

---

