---
title: "I can't access some files Samba, ACL"
date: 2017-02-23
forum: Server Platforms
---

### Post by roliee on 2017-02-23
I have a Samba server configured with acl,

I have two files in the same directory.

The permissions are the same. From Windows Samba Client I can access to one of them only. I get an error message if I open "Presentaion script.docx": "Access denied. Please Contact administrator." I can't copy or delete this file...

Here are the results for ls -l, getfacl.

-rwxrwx---+ 1 root root    21359 Feb  8 12:50 Presentation script 2.docx
-rwxrwx---+ 1 root root    21359 Feb  8 12:50 Presentation script.docx

getfacl "Presentation script.docx"

# file: Presentation script.docx
# owner: root
# group: root
user::rwx
user:root:rwx
user:rc:rwx
user:kr:rwx
user:ma:rwx
user:bo:rwx
group::---
group:root:---
mask::rwx
other::---

getfacl "Presentation script 2.docx"
# file: Presentation script 2.docx
# owner: root
# group: root
user::rwx
user:root:rwx
user:rc:rwx
user:kr:rwx
user:ma:rwx
user:bo:rwx
group::---
group:root:---
mask::rwx
other::---


Share Conf:
[Playground MA]
path = "/Playgrounds/Playground MA"
valid users = kr, ma
read only = no
guest ok = no
vfs objects = acl_xattr
nt acl support = yes
inherit acls = yes
inherit owner = yes
inherit permissions = yes
map acl inherit = yes
store dos attributes = yes
dos filemode = no
acl map full control = False


Please help to find out what is the solution. It randomly occur with other files as well. If I copy the file on the server to another temporary location and copy it back and set acl permissions, I can read/write the file from the samba client. But this is not a good solution....

---

### Post by volkswagner on 2017-02-24
You say it's intermittent, but since you're pointing to MS Office documents I'm compelled to point out
some previous posts regarding ACL, SAMBA and MS Office docx, xlsx.

[https://ubuntuforums.org/archive/index.php/t-2061725.html](https://ubuntuforums.org/archive/index.php/t-2061725.html)
[http://pig.made-it.com/samba-file-rights.html#25963](http://pig.made-it.com/samba-file-rights.html#25963)

If you do an 
```
ls -al /directory/holding/problemFiles
```
Maybe you'll see some stuck temp files with ~, maybe the an old temp file is clogging up the works?


Do you need "nt acl support = yes" as part of your config? Can you change it to no?
Also if you explore the files from windows machine and check permissions (file and directory), do you get expected results?

---

