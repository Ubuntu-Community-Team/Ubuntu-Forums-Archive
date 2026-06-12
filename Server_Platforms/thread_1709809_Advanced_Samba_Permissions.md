---
title: "Advanced Samba Permissions"
date: 2011-03-18
forum: Server Platforms
---

### Post by redryno1221 on 2011-03-18
I want to allow my users on my sftp server (samba) to upload and download but I do not want them to be able to delete any files or folders. Is there any way this can be done? :confused: thanx

EDIT: Also i have tried several chmod and modifying the samba config to no avail

---

### Post by Vegan on 2011-03-18
What you want to do then is set SAMBA to force the file mask to a read only.

Then they cannot delete the file as they need permission.

This is complex and needs a lot of thought.

I am assuming you are using user accounts

---

### Post by redryno1221 on 2011-03-19
yes I am using user accounts and when I set the folder to read only the folder will not allow for uploading. 

I'm not sure if this is possible as I have searched everywhere and cannot find any relevant details. Thanks Vegan for the quick reply

---

