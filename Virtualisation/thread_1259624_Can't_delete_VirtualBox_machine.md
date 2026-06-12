---
title: "Can't delete VirtualBox machine"
date: 2009-09-06
forum: Virtualisation
---

### Post by Vunutus on 2009-09-06
I have a XP virtual machine that I want to get rid of to free up space. I'm trying to get rid of it via the GUI and am encountering problems.

If I right click on the machine in the main VM selector and hit "Delete", I get this message:

```
Failed to remove the virtual machine Windows XP.
Cannot unregister the machine 'Windows XP' because it has 1 snapshots.
```

Ok, simple enough. Delete the snapshot, right?

I open its snapshot tab, right click the snapshot and hit discard, but I get this error:

```
Failed to discard the current snapshot and the current state of the virtual machine Windows XP.
Hard disk '/home/danny/.VirtualBox/VDI/Windows XP.vdi' has more than one child hard disk (6).
```

Not quite sure what this means, so I decide to go into the hard disk dialog and just outright remove the Windows XP.vdi image. I open it up, select it, hit release, then remove and delete. It goes off the list, I try to remove the snapshot and I get the same error again. I go back in the hard disk dialog again and the XP image has re-appeared. 

How can I get this VM to completely go away?

---

### Post by jocampo on 2009-09-06
Via XML file :-) .. 

go to the XML config file or that machine and I think the main one, and get rid of everything that points to that machine. Later, delete the vdi file manually and you're done.

---

### Post by aesis05401 on 2009-09-06
Hrm, I thought that this is what the VMM is for.  The standard hdd dialog from the VM main window is not the full Virtual Media Manager.  If you go to File menu/Virtual Media Manager you will see a list of .vdi files.

Some of these will expand to show multiple child entries.  These entries are differential .vdi files that VBox uses to record changes.  I believe that these are what you need to delete.

Does this help?

Edit: Many people appear to be experiencing related issues: [http://www.virtualbox.org/ticket/2943]("http://www.virtualbox.org/ticket/2943")

---

### Post by Vunutus on 2009-09-06
> **aesis05401 said:**
> Hrm, I thought that this is what the VMM is for.  The standard hdd dialog from the VM main window is not the full Virtual Media Manager.  If you go to File menu/Virtual Media Manager you will see a list of .vdi files.

Some of these will expand to show multiple child entries.  These entries are differential .vdi files that VBox uses to record changes.  I believe that these are what you need to delete.

Does this help?

Edit: Many people appear to be experiencing related issues: [http://www.virtualbox.org/ticket/2943]("http://www.virtualbox.org/ticket/2943")

Wow yeah I didn't know there was another dialog for managing hard drives. I opened that up and saw all the other images that were created under it for some reason. There were lots of duplicates taking up LOTS of space. I got rid of them all and reclaimed something like 30% of my /home partition haha

Thanks :D

---

### Post by aesis05401 on 2009-09-06
Glad it helped!  Enjoy :)

---

### Post by Sabre307 on 2009-10-06
Awesome! Thanks for your help, that saved me. :guitar:

---

