---
title: "trashinfo files not deleted when I empty trash"
date: 2010-05-24
forum: Security
---

### Post by moftasa on 2010-05-24
I don't know whether this is a bug or feature. But I find the fact that the Trash in Gnome doesn't delete trashinfo files a security liability. 

I found in ./local/share/Trash/info thousands of .trashinfo files named exactly like the files deleted and each one contains the date of deletion. 

I thought when I empty the trash bin every record of the files were removed. I understand that there are forensic ways to recover data and rm isn't very secure with journaled file systems, but forensic recovery isn't 100% and if the disk is written over several times the data is gone. 

Here you have a permanent list of all the files you've deleted, without you knowing and the dates of deletion. IMO that's too much information.

Update: Weird after removing the files manually and then trying to delete files again using the trash I found no .trashinfo files, this time. So they were probably leftover files, but they didn't have a different owner/permission. Could this have been an issue and now fixed? (running Lucid)

---

### Post by cariboo on 2010-05-24
If you don't like the way Trash is behaving, I would suggest you not use it, enable the delete option by going to Nautilus->Edit->Preferences->Behavior then adding a checkmark to include a delete command to bypass trash. I also disable the message asking if it is OK.

---

