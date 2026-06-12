---
title: "Security Tabs and Samba"
date: 2005-11-22
forum: Server Platforms
---

### Post by grendelkhan on 2005-11-22
Is anyone else getting a problem using a straight up Breezy install to share out to a Windows XP workgroup and on the Windows clients there is no security tab on the directories and files?

I'm using XFS as my filesystem and I never had this issue under Fedora with ext3 filesystems.

---

### Post by LordHunter317 on 2005-11-22
Are you sure the client isn't in 'Simple Filesharing mode'?

---

### Post by grendelkhan on 2005-11-22
Not that I know of, but how do I check?  In the authentication tab for the network adapter, I've got "authenticate as computer" turned off, what else am I missing?

---

### Post by LordHunter317 on 2005-11-22
In the options for Explorer, make sure 'Use simple filesharing' isn't selected.  You'll also get a radically different sharing tab if it is.

---

### Post by grendelkhan on 2005-11-22
SWEET JESUS YOU'RE A GENIUS!

Why does XP have this crap in it?  I don't remember Win2k being like this.

---

### Post by LordHunter317 on 2005-11-22
It was originally intended for Home edition, I think.  I'm not sure you can even enable it on machines attached to a domain.

---

