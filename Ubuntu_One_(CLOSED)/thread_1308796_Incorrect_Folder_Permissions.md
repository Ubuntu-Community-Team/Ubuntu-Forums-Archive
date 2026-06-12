---
title: "Incorrect Folder Permissions?"
date: 2009-10-31
forum: Ubuntu One (CLOSED)
---

### Post by promet on 2009-10-31
Hello,

Ubuntuone seems to set the folder permissions incorrectly (I assume I should be able to write to it) for the ~/.local/share/ubuntuone/shares (i.e. the symolic link for the ~/Ubuntu One/Shared With Me) folder. So, I cannot write to it. 

I've tried reinstalling the software, manually changing the permissions in various ways, but the application forces a reset on these permission to be again invalid. has anyone else had this issue? Any ideas?

Thanks

---

### Post by yesint on 2009-11-01
The same problem. Have no idea how to fix it.

---

### Post by promet on 2009-11-01
Yeah, it's a bummer huh? I'd really like to play around with it.

---

### Post by ilpiero on 2009-11-02
Maybe i've got the same problem, the ubuntuOne folder was accessbile by my user but not writable , i changed the permission and seems to work (but now that you say the program reset them i'll check again).

I'll let you know if i  find a solution.

---

### Post by joshuahoover on 2009-11-02
> **promet said:**
> Hello,

Ubuntuone seems to set the folder permissions incorrectly (I assume I should be able to write to it) for the ~/.local/share/ubuntuone/shares (i.e. the symolic link for the ~/Ubuntu One/Shared With Me) folder. So, I cannot write to it. 

I've tried reinstalling the software, manually changing the permissions in various ways, but the application forces a reset on these permission to be again invalid. has anyone else had this issue? Any ideas?

Thanks

This is intentional. The "Shared With Me" folder is a special one that we use to hold all the folders other Ubuntu One users share with you. If someone shares a folder with you and makes that share writeable, you should be able to read, write and delete files from that folder within the "Shared With Me" folder.

Thank you,

Joshua

---

### Post by promet on 2009-11-02
AH! Brilliant! Thank you Joshua! I totally misunderstood that.

Okay that is one hill climbed. So, how does the "drag and drop" sync thing work, do I just create new folders in the "Ubuntu One" Directory, or just toss goodies in there? Both, I assume, but clearly, my "assumptions" have gotten me into trouble already, ;)

Cheers!

---

### Post by ilpiero on 2009-11-03
> **joshuahoover said:**
> This is intentional. The "Shared With Me" folder is a special one that we use to hold all the folders other Ubuntu One users share with you. If someone shares a folder with you and makes that share writeable, you should be able to read, write and delete files from that folder within the "Shared With Me" folder.

Thank you,

Joshua

D'oh!! So where should i put the shared files? Just in th UbuntuOne folder?
And btw there should be a "Share with ubuntu one" Nautilus contextual menu entry everywhere or just in some particular foders?

Thanks!!

---

