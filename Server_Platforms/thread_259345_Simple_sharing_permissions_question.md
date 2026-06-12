---
title: "Simple sharing permissions question"
date: 2006-09-17
forum: Server Platforms
---

### Post by kgeil on 2006-09-17
So, I've been trying to set up an Ubuntu samba server with 2 directory types:
one will be for each user to access his/her personal files, which has gone fine.  The other is a "group files" directory, in which I want anyone from their workstation to be able to read or write to any file, regardless of who is the "owner" of the file.  

I have a group called everyone, and I've tried to recursively change ownership in the directory Group_Files through a command such as:

chgrp -R everybody /Group_Files

which does change group ownership to all files in the directory, but only for files created in the past.  If a new file is created, it is only writeable by the creator.

My question is, how do I set up a directory which users can access from their windows workstation, drag a file into it, and allow anyone to change it?  I don't want users to have to worry about permissions when they drag and drop.  (I don't even know if they can worry about Linux permissions from their Windows workstations.)


Following is my Group_Files section from smb.conf:


[Group_Files]
path = /Group_Files
comment = folder with open access to everyone
available = yes
browseable = yes
public = yes
writable = yes
](*,) 


Thanks,

Kevin

---

### Post by skirkpatrick on 2006-09-17
I believe you need to add:
**create mode = 0777**
which would give everybody complete access.

---

### Post by kidders on 2006-09-17
Hi there,

There are two ways of handling this problem. First, there are several options you can add to your smb.conf to control the permissions allocated to newly created files. Second, you could ignore smb.conf altogether and set the SGID bit on the actual shared directory itself. This would have the effect of forcing the directory's own group ownership on any new files.

Which you choose is up to you, really. Take a look at the "samba" and "chmod" man pages for a full explanation of either approach.

---

### Post by kgeil on 2006-09-17
Thanks to the both of you.  Adding the create mode line worked.  

AND, I was given two different approaches, one quick fix, and the other, a way to really understand what I was about to do.  My short experience in Linux is teaching me that quick fixes without understanding why is a great way to get in trouble.  (Yes, I did use the quick fix) So, it's time for me to do a little reading.  


Thanks again,

Kevin

---

