---
title: "Trash folder should be deleted if empty on removable media for Windows compatability"
date: 2008-06-11
forum: Ubuntu Brainstorm
---

### Post by CrazyGuy123 on 2008-06-11
If the hidden ".Trash-1000" folder is empty when a device is unmounted through gnome, the folder should be deleted.

I suggest this because it confuses many users who use USB sticks on both Ubuntu and Windows, and particularly those who don't store data in the trash folder after removing the usb stick.

Another solution would be to set the MS-DOS attribute "hidden" on the folder (or all files/folders beginning with a "."), since by default windows won't then show it.

---

### Post by smartboyathome on 2008-06-11
This has been suggested many times. Try searching. :)

---

### Post by CrazyGuy123 on 2008-06-12
Just did a search and still can't find it (looked through all the results in this topic, and the first couple of pages of results on other topics) - forgive my incompetance!

What was the reason for not implementing it?

---

### Post by smartboyathome on 2008-06-12
I think it was because of the backend rewrite, it just hasn't been implimented yet due to not a high enough priority versus other features. Can't quite remember though.

---

### Post by bruce89 on 2008-06-12
> **CrazyGuy123 said:**
> What was the reason for not implementing it?

Nobody can be arsed.

In FOSS, people need to write stuff they want to see, no-one else will do it for you.

---

### Post by CrazyGuy123 on 2008-06-15
Well it looks to me like it could be quite easy to implement, and if I get time I could even do it myself.  If I did write a patch for this, what are the chances of it being included?  (I don't want to spend ages finding the right bit of code to change only to find it's wasted effort)

---

### Post by smartboyathome on 2008-06-15
Pretty good I think, though the window for inclusion to GNOME 2.24 might be closed (dont know) but 2.26 is a definate if they dont all hate the idea.

---

### Post by LaRoza on 2008-06-15
> **CrazyGuy123 said:**
> If the hidden ".Trash-1000" folder is empty when a device is unmounted through gnome, the folder should be deleted.

I suggest this because it confuses many users who use USB sticks on both Ubuntu and Windows, and particularly those who don't store data in the trash folder after removing the usb stick.

Another solution would be to set the MS-DOS attribute "hidden" on the folder (or all files/folders beginning with a "."), since by default windows won't then show it.

How about Windows following the standards instead of using their own method? The Linux way of dealing with Trash has been standardized already. There is no reason to try to maintain compatability with a non standard legacy operating system.

---

### Post by Frak on 2008-06-16
Even OS X implements a .Trashes into all volumes it finds.

This is a standardized method. It's more of Windows XP fault of not supporting it.

Though, a hidden atribute *might* help.

---

### Post by LaRoza on 2008-06-16
> **Frak said:**
> 
Though, a hidden atribute *might* help.

I don't think so. There would be the mysterious missing space on the drive with no hint as to what the cause is in Windows.

---

### Post by Frak on 2008-06-16
> **LaRoza said:**
> I don't think so. There would be the mysterious missing space on the drive with no hint as to what the cause is in Windows.
I eated it.

Nom nom nom nom nom nom nom nom nom.

:D

---

