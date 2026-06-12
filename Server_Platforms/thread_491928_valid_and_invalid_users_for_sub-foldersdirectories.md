---
title: "valid and invalid users for sub-folders/directories"
date: 2007-07-04
forum: Server Platforms
---

### Post by 97ldave on 2007-07-04
Hi,

i am trying to set up at file server using Ubuntu 7.04 server edition. I have connected to the the domain etc. and I have tested the file sharing. This works fine.

However, I created a sub-folder within this directory and I want to restrict access to specific users. I thought it would be the same way for the other file i did, but it doesnt work. This is the smb.conf file for the test of file sharing:

[SharedFolder]
path = /home/lawrenced/Shared_Folder
valid users = @AES\everyone                                                     ---- allows everyone to access this folder
#invalid users = AES\lawrenced
available = yes
public = no
writable = yes
force create code = 0666
force directory code = 0777

[TestShare]
path = /home/lawrenced/Shared_Folder/Test_Share
valid users = @AES\everyone                                                 ---- allows everyone to access this folder
invalid users = AES\lawrenced                                                ---- should deny me access, but doesnt work
available = yes
public = no
writable = yes
force create code = 0666
force directory code = 0777

Does it work different for sub-folders?
Can anyone suggest anything

Thanks

---

### Post by vmikalinis on 2007-07-06
I think the sub folder is being affected by the original share definition, what happens if you move it outside that "tree"?  You could allow them using groups and folder permissions?

---

### Post by 97ldave on 2007-07-10
Outside the tree it works the same as the SharedFolder, but thats not what I want, i needs to be in that tree! I have tried setting the permissions for just that folder (Test_Share), but that doesnt seem to work either!

---

