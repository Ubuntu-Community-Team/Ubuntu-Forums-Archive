---
title: "Why don't files deleted from a thumb drive go to the actual trash?"
date: 2010-01-06
forum: The Cafe
---

### Post by sp0tz on 2010-01-06
People get an "error" frequently and it's been posted on the forums two or three times that I've found:

A thumb drive gets connected to an ubuntu pc. The thumb drive is almost full. The user highlights some of the files on the thumb drive and presses the "delete" key. This causes the files to disappear in nautilus (really they're just moved to a hidden '.trash' folder in the thumb drive). The user THINKS that the files are gone, deleted, and not taking up any more space, but they're still on the thumb drive until you unmount the thumb drive. 

It's possible to bypass this by holding 'shift' while pressing 'delete', but I was wondering why files from the thumb drive aren't moved to the user's regular trash folder. This temporary, hidden trash folder on the thumb drive is very confusing in several ways.

It's a question of theory. Wouldn't it be better to remove the files from the thumb drive when the user wants to delete them?

---

### Post by FuturePilot on 2010-01-06
After moving files to the trash from a USB drive you can open the trash and empty it. You don't have to wait until you unmount it. 
Moving the files to the "regular" trash directory is a bad idea. Suppose you're deleting a large file. Do you know how long that would take?

---

### Post by Xbehave on 2010-01-06
To your filebrowser a 1GB flashpen, a 1TB external drive and an internal partition all look the same so it has to behave in a consistent way (and move things to local trash).

A filebrowser could try and be clever (e.g if its a usb pen and small and the files are small move them to local trash) but:
1) trying to be clever is generally a dumb thing to do
2) nautilus (the gnome browser) is the least likely to do this.

---

### Post by sp0tz on 2010-01-06
Hm. Well you're right; that would cause a write operation from the thumb drive to the hdd *and* a delete operation from the thumb drive, but it's odd that user's aren't notified somehow that the files still take up space on the drive until it's properly unmounted or the trash is emptied.

It's not a big deal when working only on the hard drive, because it's very unlikely that the hard drive is going to fill up, but this does cause people to run into insufficient space errors when trying to write to the thumb drive sometimes.

Maybe if the default deletion action in a thumb drive was "delete and bypass trash" (with the 'are you sure' prompt, of course), it would be a little better? I'm not sure what purpose it serves to have deleted items still reside on the thumb drive.

edit: the post above mine says that the OS doesn't know that a thumb drive is a thumb drive and an external HDD is not. That kind of messes up the above suggestion. Guess we just have to depend on users always using the "safely remove" option...

---

### Post by FuturePilot on 2010-01-06
> **sp0tz said:**
>  I'm not sure what purpose it serves to have deleted items still reside on the thumb drive.

The same purpose that deleted items still reside on your hard drive until you empty the trash.

---

### Post by cariboo on 2010-01-06
Trash cans on all operating systems work the same way, the file isn't actually deleted until the trash is emptied. By moving the trash to a single trash can, they are effectively being deleted from the original drive. If you don't like that behavior, enable delete by going to Nautilus-->Edit-->Preferences-->Behavior and enable the delete command. That way you can bypass trash completely by deleting the file.

---

### Post by Mr. Picklesworth on 2010-01-06
I think it's kind of a cool approach, really. The trash directory on the flash drive is certainly not hidden - at least no more so than the one in your home folder. If you check out the trash: file system (follow the Trash shortcut in Nautilus), it lists items from any trash bin that is attached.

Granted, I haven't seen what happens when someone trashes a file to free space then tries to add a really big file (exceeding the available space). Does it complain cryptically?

Moving the deleted file to your home folder's .trash would be an insane waste of time and resources — especially resources! — while just completely deleting it in that case would be inconsistent. We can't have one button that looks the same but does completely different things (one considerably more dangerous than the other) based on a very loosely defined context.

In my opinion, this trash approach is considerably better designed than the proprietary competition. (Also years overdue, but I think it was worth it).


Maybe it would work to have an [info bar]("http://library.gnome.org/devel/gtk/stable/GtkInfoBar.html") (or something along those lines) appear when users delete files (maybe when they copy them, too), briefly listing the files along with some means of accessing a function like Restore or Paste in a point-and-click fashion.
Sorry, I couldn't do it myself; Nautilus's source code makes me want to slam my head through a wall every time I look at it. Mainly my own allergy to C, though.

---

### Post by xuCGC002 on 2010-01-06
> **sp0tz said:**
> 
It's possible to bypass this by holding 'shift' while pressing 'delete', but I was wondering why files from the thumb drive aren't moved to the user's regular trash folder. This temporary, hidden trash folder on the thumb drive is very confusing in several ways.

I've actually found this to be better than the old Windows removable storage deleting system. Once I deleted an important file for school, only to realize it was gone forever, and have to start all over again (I had to remember to save a copy). Once I got Ubuntu (later Kubuntu), a similar problem happened and I just restored the file from the trash avoiding a huge waste of time.

---

### Post by earthpigg on 2010-01-06
i really don't like the whole 'trash can' paradigm in general.

what i would like, and what i would implement if i was more knowledgeable than i currently am:

user clicks on a file and presses the 'delete' button on their keyboard.

the file listing for that file turns from black text and whatever icon to red text and red-tinted icon. maybe hovering over shows "marked for deletion". the file is still regarded by the file manager to take up X bites of space.

the trash can lists the files, and where they reside. emptying the trash hunts the files down and deletes them. the "trash can" is just a plain text file. created on whatever partition. if its an NTFS or FAT32 partition then it is a dotfile marked as 'hidden or system file' or whatever. on a proper partition, it's a dotfile.


with the current trash can paradigm, something is either deleted or semi-deleted-in-the-trash or not deleted at all.

lets remove that middle-man rubbish.

the file is there.

the file is marked for deletion (but otherwise unmodified). the right-click-context menu doesn't use the word 'delete' by itself, which is inaccurate under the current paradigm.

the file is deleted.



same two-step process (declare your intent to delete it, then delete it for real) as the current paradigm, but less ambiguity. simpler. more logical and rational. the user doesn't see right-click context menus that lie to them.

---

### Post by Crunchy the Headcrab on 2010-01-07
Meh, I like the trash can.  I don't want to see files I've removed unless I need to restore them.  Moving them to the trash is more about cleaning up my interface, because if I really wanted to directly delete them, that's just what I'd do.

---

