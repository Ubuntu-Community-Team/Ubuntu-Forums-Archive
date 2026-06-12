---
title: "Grant restricted users permission read only"
date: 2013-03-28
forum: Security
---

### Post by pptwhite on 2013-03-28
I'm wanting to grant access to my server though make it so they can only view/look at the code. Read only view. It's to hire a new programmer. Looking to have them look at the code though not make any changes. 

How can I allow this? can it be done? 

Thank you,

---

### Post by Bashing-om on 2013-03-28
pptwhite; Hi ! Welcome to the forum.

Granting limited access is a strong point within linux (ubuntu). There are a number of ways to do this.

Here is a tutorial to point you toward some idea as to how to set it up:
[URL="https://help.ubuntu.com/community/FilePermissions"]https://help.ubuntu.com/community/FilePermissions
[/URL]
Lots more if you search at this link:
[https://help.ubuntu.com/community/NewDocs](https://help.ubuntu.com/community/NewDocs)[INDENT=2]
If this does not suffice, by all means post back
[/INDENT]

---

### Post by papibe on 2013-03-28
Hi pptwhite. Welcome to the forums ):P

Yes, it can be done.

This would be the general steps:
[LIST]
[*]Create a new user.
[*]Give the candidate his/her user and password. Also the absolute path to the project files.
[*]Install openssh-server if you want to grand him/her remote access.
[*]By default the candidate:
[LIST]
[*][*]will have read access to the files, and
[*][*]won't be able to modify the files.
[/LIST]
[*]In case you want to make extra sure of the permissions you can run these commands:
```
chmod -R o-w,o+r  /path/to/project

find /path/to/project -type d -exec chmod o+x '{}' \;
```
[/LIST]
Hope it helps. Let us know how it goes.
Regards.

---

