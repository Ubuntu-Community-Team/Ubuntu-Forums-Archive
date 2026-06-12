---
title: "Deselect a sub folder for synchronising"
date: 2013-03-07
forum: Ubuntu One (CLOSED)
---

### Post by stevebond001 on 2013-03-07
Hi
Is there any way to deselect a sub folder and prevent it synching with Ubuntu One?  I have synched my "Documents" folder but there is a sub folder which I don't need backing up.
Can I exclude it from the synch process?

Thanks in advance.

---

### Post by slickymaster on 2013-03-07
Have you tried to unsubscribe that folder from the Ubuntu One web interface?

Go to [one.ubuntu.com/files/]("https://one.ubuntu.com/files/") and under _My synced folders_ there is a list of the folders outside of **~/Ubuntu One** that you have synced. Click on the **More** link next to the folder you want to stop syncing, and then click the **Stop syncing this folder** link.

---

### Post by stevebond001 on 2013-03-08
> **slickymaster said:**
> Have you tried to unsubscribe that folder from the Ubuntu One web interface?

Go to [one.ubuntu.com/files/]("https://one.ubuntu.com/files/") and under _My synced folders_ there is a list of the folders outside of **~/Ubuntu One** that you have synced. Click on the **More** link next to the folder you want to stop syncing, and then click the **Stop syncing this folder** link.

Hi
Thanks for the response.  I have tried to do this but there is no option to stop syncing the folder.
I can stop syncing the top level folder (i.e. "Documents"), but I can't do it with sub folders (there is a folder within my "Documents" folder I don't want to share).

Any other ideas would be welcome

---

### Post by schragge on 2013-03-08
Move that folder to another place outside of the synced path and replace it with a symlink. AFAIK, UbuntuOne doesn't support synchronizing symlinks.

---

### Post by stevebond001 on 2013-03-08
OK I'll give it a go.
Thanks for your help

---

