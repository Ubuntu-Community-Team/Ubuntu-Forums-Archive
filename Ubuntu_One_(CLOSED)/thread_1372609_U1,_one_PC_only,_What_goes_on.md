---
title: "U1, one PC only, What goes on?"
date: 2010-01-04
forum: Ubuntu One (CLOSED)
---

### Post by candtalan on 2010-01-04
I use one PC only, I paste some files and folders into the U1 folder. Files upload to the webstore, I can see them via the web.

Now, *what* is subsequently used as a *reference* for content? For example, what should happen if I rename a folder in the PC U1 folder? Should the new name later appear appropriately on the webstore?

What should happen if I use the web access, and delete a folder in the webstore? The PC U1 folder remains full, does the web store get filled and corrected?

At a time when the webstore is complete and correct, if the contents of the PC U1 folder is deleted by me, will the webstore contents act as a form of backup? Or will the webstore contents also get removed by U1 process?

tia

---

### Post by jonest1 on 2010-01-04
I have not completed testing myself, but according to the UK Loco podcast, once a file is deleted in the U1 directory it is updated to the cloud and the change is populated to other hosts.  I'm not sure about the other way around.

There should be a feature which allows a grace period for deletions or a manual trigger to synchronize deletions.

---

### Post by joshuahoover on 2010-01-15
> **candtalan said:**
> I use one PC only, I paste some files and folders into the U1 folder. Files upload to the webstore, I can see them via the web.

Now, *what* is subsequently used as a *reference* for content? For example, what should happen if I rename a folder in the PC U1 folder? Should the new name later appear appropriately on the webstore?

The new folder name should show up on the web as well.

> **candtalan said:**
> What should happen if I use the web access, and delete a folder in the webstore? The PC U1 folder remains full, does the web store get filled and corrected?

If you delete a folder via the web, you'll currently need to disconnect and connect the Ubuntu One client on your PC for the deletion to occur on the PC.

> **candtalan said:**
> At a time when the webstore is complete and correct, if the contents of the PC U1 folder is deleted by me, will the webstore contents act as a form of backup? Or will the webstore contents also get removed by U1 process?

The contents in the webstore will be removed as well. The file service is all about synchronizing and not backup. We've talked about putting backup functionality into the service, but that is not the way it works currently.

Thank you,

Joshua

---

