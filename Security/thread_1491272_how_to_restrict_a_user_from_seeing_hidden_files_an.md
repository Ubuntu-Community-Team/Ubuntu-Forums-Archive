---
title: "how to restrict a user from seeing hidden files and folders?"
date: 2010-05-23
forum: Security
---

### Post by cscat on 2010-05-23
Hi guys,
Thanks for your answers.
Reza

---

### Post by kevdog on 2010-05-23
I think the concept of a linux jail is appropriate if you are using ssh.  I need more information please.

---

### Post by cscat on 2010-05-23
yes I saw jail but couldn't make anything out cuz the documentation was not clear for me. :(

---

### Post by Agent ME on 2010-05-23
Do you want to prevent a user from looking at another user's files? You just need to set the permissions of the folder to be not viewable by other users. Right-click, properties, permissions. Then set the Folder Access for Groups and Other to "None".

---

### Post by cscat on 2010-05-23
no! it's a partition with NTFS that I mounted in ubuntu. Permission says root owns the folder and the group is "plugdev"... I can't change none of them, although I log in with root user and try to change it!!!

---

### Post by OpSecShellshock on 2010-05-23
So are you trying to view/change files yourself or to keep others from viewing them? I wouldn't think non-admin users could even mount the NTFS partition under those settings.

---

### Post by cscat on 2010-05-23
> **OpSecShellshock said:**
> So are you trying to view/change files yourself or to keep others from viewing them? I wouldn't think non-admin users could even mount the NTFS partition under those settings.
oh yes I'm trying to keep others from viewing them. non root users can mount NTFS, you can set it so that it will not be automounted but then the whole NTFS partition will be unaccessible, which is not what I want. I want just a folder to be unaccessible, or at the least because I made it hidden, that user can't see hidden folders at all.

---

### Post by Zemblan on 2010-05-23
Not entirely sure about this, but I think if you remove the execute permissions from the mount directory for all except the owner, then no one else will be able to look at the contents. For directories the execute permission is what allows/disallows a user from looking at the contents.

EDIT: set these permissions before mounting the device.

---

### Post by cscat on 2010-05-23
> **Zemblan said:**
> Not entirely sure about this, but I think if you remove the execute permissions from the mount directory for all except the owner, then no one else will be able to look at the contents. For directories the execute permission is what allows/disallows a user from looking at the contents.

EDIT: set these permissions before mounting the device.
Thanks Zemblan, can you explain step by step?

@OpSecShellshock: I meant "defauts" option in fstab has all this info in it.

---

