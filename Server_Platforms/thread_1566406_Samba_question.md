---
title: "Samba question"
date: 2010-09-02
forum: Server Platforms
---

### Post by Ubunt2u on 2010-09-02
I have a few ubuntu servers which have samba shares on the network and for the most part have had little trouble with them.  Recently we purchased a few iMac's for one of our deptartments and, while we're able to access the shares, all the files on them are read-only and we are unable to delete/modify files using the iMacs.
This is not an issue with any of our windows machines (W2K, WinXP, Vista).

Any thoughts?

---

### Post by lykwydchykyn on 2010-09-02
What security mode is your server running in?  Can you post your smb.conf?
And what are the local filesystem permissions on the files?  Are you using posix ACLs or just Unix permissions?

---

### Post by Ubunt2u on 2010-09-02
in smb.conf security = user is commented out

i've also discovered a wrinkle which may be complicating things; when we set up the imacs, we made the usernames 2 words (user name).  which, if i add it to valid users, will be a problem for samba.

so i guess the first step is to rename the usernames on the imacs to a single word.

---

