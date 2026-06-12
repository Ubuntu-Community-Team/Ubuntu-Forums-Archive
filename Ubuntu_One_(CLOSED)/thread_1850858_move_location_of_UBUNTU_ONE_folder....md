---
title: "move location of UBUNTU ONE folder..."
date: 2011-09-27
forum: Ubuntu One (CLOSED)
---

### Post by liquidmonkey on 2011-09-27
is it possible to move the location of the UBUNTU ONE folder in 11.04?
i want to move it to another partition.

how can it be done?


thanks!

---

### Post by oldos2er on 2011-09-27
Thread moved to Ubuntu One.

---

### Post by Dragonbite on 2011-09-27
As far as I know, your "Ubuntu One" and other synchronized folders have to be under your /home/<username> directory.

Now, if this directory or if the folders are a separate partition mounted to this location, then THAT may work.

I am doubtful about symlinks either.

---

### Post by mr007rin on 2011-09-28
er

---

### Post by liquidmonkey on 2011-09-29
> **oldos2er said:**
> Thread moved to Ubuntu One.

i did have a thread open with this question in ubuntu one BUT NO ONE ANSWERED.

---

### Post by liquidmonkey on 2011-09-29
> **Dragonbite said:**
> As far as I know, your "Ubuntu One" and other synchronized folders have to be under your /home/<username> directory.

Now, if this directory or if the folders are a separate partition mounted to this location, then THAT may work.

I am doubtful about symlinks either.



hopefully we can choose where to put the folder in 11.11?
cause right now when i backup my ubuntu system (with clonezilla) the ubuntu one folder is included which is a waste of space (and time) since its in the cloud anyway.

---

### Post by Dragonbite on 2011-09-29
> **liquidmonkey said:**
> hopefully we can choose where to put the folder in 11.11?
cause right now when i backup my ubuntu system (with clonezilla) the ubuntu one folder is included which is a waste of space (and time) since its in the cloud anyway.

I don't think they are planning on allowing the Ubuntu One folder to be moved or removed.  This is the root level of your Ubuntu One account if you check it through the website.

Something that may be of interest whne cloning is how Ubuntu One sees the contents of the Ubuntu One folder when it re-synchronizes.

The system *may* "merge" and give you duplicates, "remove" and put into the folder what you have online, or "update" and remove what is online with what is in the local version.

---

