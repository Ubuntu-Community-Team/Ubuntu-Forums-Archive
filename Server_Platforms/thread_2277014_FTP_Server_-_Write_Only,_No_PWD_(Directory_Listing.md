---
title: "FTP Server - Write Only, No PWD (Directory Listing) and No Viewable Folders"
date: 2015-05-06
forum: Server Platforms
---

### Post by danielcarroll on 2015-05-06
Hi All,

I am new to Linux administration, I was wondering if anyone was able to help me with a few things. I have tried many servers/configurations but I am unable to get this working.

[B]What I need

[/B]A folder with Writable but not Readable Permissions (I have tried using CHMOD, FTP Servers seem to ignore this). User connects to FTP, Users can see NOTHING, User just uploads.

**What Servers I have used** 

VSFTPD
ProFTPD
and PureFTPD

[B]My Questions
[/B]
1) What would be the easiest, most granular server when it comes to permissions?

2) How would I go about setting up permissions on (Y) Server?

Thank you so much for any help you may provide to me, Please let me know if you need more information.

---

### Post by nerdtron on 2015-05-07
> User connects to FTP, Users can see NOTHING, User just uploads.
How does the user knows the file is uploaded?

[quoet](I have tried using CHMOD, FTP Servers seem to ignore this). [/quote]

What folder permission have you tried?

---

