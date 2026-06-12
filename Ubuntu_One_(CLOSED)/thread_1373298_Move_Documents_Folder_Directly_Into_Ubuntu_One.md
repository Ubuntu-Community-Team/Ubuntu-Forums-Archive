---
title: "Move Documents Folder Directly Into Ubuntu One"
date: 2010-01-05
forum: Ubuntu One (CLOSED)
---

### Post by ricksterinps on 2010-01-05
I'm really starting to like the service, but is there a way that I can just move my Document folder into the Ubuntu One folder and just change my bookmarks in Nautilus to that directory?  

I have 20gb of data and I would really like to have it backed up however often Ubuntu One does it.  I don't need instantaneous syncing so that isn't an issue.  

Thanks

---

### Post by mocoloco on 2010-01-05
I wonder if a symbolic link would work?  Right-click on your documents folder and choose "make link".  Drag the new link into your Ubuntu One folder.  You can rename it to just "Documents" after that if you want.  Sync and see what happens.

---

### Post by emurphy on 2010-01-05
Not in Ubuntu 9.10, but we're working on a feature for Ubuntu 10.04 so that you can just right-click on your Documents folder and choose something like "sync this folder with Ubuntu One".

The symlink idea is clever, but it won't work because the sync code ignores symlinks currently.

---

### Post by ricksterinps on 2010-01-05
OK thanks.  I'll just wait for 10.04.

---

