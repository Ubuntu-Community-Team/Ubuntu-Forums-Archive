---
title: "how to delete all Ubuntu One files?"
date: 2013-03-02
forum: Ubuntu One (CLOSED)
---

### Post by mdshaver on 2013-03-02
I currently have just under 60 GB of files/folders in my Ubuntu One account. I do not currently have these files synced to any computers. I would like to easily delete all these files in the cloud so that I can start over. This doesn't seem to be as straight forward as expected. I can manualy delete files and folders but I only have the option to "stop syncing" directories (e.g., Documents, Music, etc). I want to totally wipe everything without, quite tediously, deleting every file and folder manually. I also do not want to wait for all files to sync to the computer and then delete them locally. That would also be incredibly inconvenient.


Any thoughts?

---

### Post by Irihapeti on 2013-03-04
You could try accessing Ubuntu One by ftp, as described here: [https://one.ubuntu.com/help/faq/how-can-access-my-files-via-ftp-on-ubuntu/](https://one.ubuntu.com/help/faq/how-can-access-my-files-via-ftp-on-ubuntu/)

You can also use a ftp client such as FileZilla if you prefer that. Either method should allow deletion of multiple files/folders at a time.

---

### Post by DenHeldert on 2013-05-04
If use my Ubuntu One account through FTP as described in your link.
But when I try to delete files I get an error stating 'access denied' 

Any solution?

---

### Post by Irihapeti on 2013-05-04
I've discovered that I try to delete a folder via, the files within it are deleted but not the folder itself. I'm not sure if that's deliberate or a bug. It seems that empty folders have to be deleted via "stop syncing" in the web interface.

But definitely the files should delete when using ftp, so I'm not sure what's happening.

---

