---
title: "Folder Perms not being inherited for OSX cleints via NFS"
date: 2011-05-25
forum: Server Platforms
---

### Post by dtd646 on 2011-05-25
I created a NFS share and Mac cleints can successfully upload files to this share.  At this point, I am not concerned with security and have set the directory permission to chmod -R 777.  When new folders are uploaded from a Mac cleint, the folders and files in those folders get set to 775 and I cannot delete these files from the NFS share.  After the files are uploaded, I can change there permissions to 777 on the server, which allows them to be modified/deleted from the server.
 
How can I get these folders/files to inherite the permission from the top level folder?  My NFS exports file currently reads this:
 
/storage1/media 192.168.7.0/24(rw,insecure,no_root_squash,async)
 
Thanks in advance

---

