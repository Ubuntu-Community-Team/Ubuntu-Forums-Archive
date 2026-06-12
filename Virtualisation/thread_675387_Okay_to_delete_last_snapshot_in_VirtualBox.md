---
title: "Okay to delete last snapshot in VirtualBox?"
date: 2008-01-22
forum: Virtualisation
---

### Post by A-dogg on 2008-01-22
i use virtualbox and have one snapshot saved. When I look at my diskspace used (thru Filelight), it shows that I have a 3.9 gig Win XP hard drive (created in VirtualBox) and a 9.8 gig snapshot.

Is it possible to delete the snapshot and still keep all of the programs I've already installed? Or will it return me to an empty harddrive?

Maybe I should just recreate it anyway and stop using snapshots so I can gain that 10 gigs back...

---

### Post by fjgaude on 2008-01-22
I do believe snapshots are on your drive and the VM only uses in the virtual disk only what it needs to run the single image.

In vmware it is okay to delete the snapshot; you go back to the last image, and if that was when you loaded all your programs then it is okay.

---

### Post by A-dogg on 2008-01-22
Thanks for the reply, but not a CLUE what you're talking about.

Also, I'm talking about VirtualBox, not VMware.

---

### Post by fjgaude on 2008-01-22
I've used VBox for sometime but finally decided on VMwave server, for me.

If you setup your disk space in virtual as, say 6G, and then over time you have made a snapshot after adding many programs and data, the space occupied on your disk will be close to twice, or 12G. But you still use something less than 6G when you load you vm with its guest.

If you delete the snapshot you go back to what it was before making the snapshot. If the snapshot was made after all your programs were loaded and data added, then you don't need the snapshot.

That's about the best I can do with my English.

---

### Post by A-dogg on 2008-01-22
nice -- this is really helpful. as I think I've added stuff since that one snapshot I have on there, I think I'll just delete the snapshot and reinstall the crap I still need. I want that 9.8 gigs back!!! :)

---

### Post by mjag17 on 2008-01-25
(Late response, sorry)

I think this is what you were looking for: [http://www.virtualbox.org/ticket/1101](http://www.virtualbox.org/ticket/1101)

Basically what it says on that page is that discarding a snapsot will merge changes into the vdi image.

---

### Post by mech7 on 2010-03-25
mmmm if i delete the files in snapshot dir.. then the image not start anymore ;)

---

### Post by funnyperson1 on 2011-05-12
> **mech7 said:**
> mmmm if i delete the files in snapshot dir.. then the image not start anymore ;)

I know I'm thread resurrecting here, but this is one of the top google hits for "delete VirtualBox snapshots" so I though I would answer:

Snapshots represent the difference between the state when the snapshot was taken and the original Virtual Disk.

When you delete a snapshot through the VirtualBox UI, it merges those changes back into the main Virtual Disk and deletes the snapshot information.  This is likely what most people want to do.

If you delete the files from the snapshot directory using rm or Nautilus, you will lose all the information that changed between the time you took the snapshot and the time you deleted it.

Here are some good notes on this:
[http://srackham.wordpress.com/cloning-and-copying-virtualbox-virtual-machines/](http://srackham.wordpress.com/cloning-and-copying-virtualbox-virtual-machines/)

---

