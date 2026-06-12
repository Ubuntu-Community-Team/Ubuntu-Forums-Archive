---
title: "Samba allow modify but not delete"
date: 2007-01-29
forum: Server Platforms
---

### Post by detectiveinspekta on 2007-01-29
Need to create a share that allows modification but it not to be deleted.

I have already experimented with ext2 attrubutes, and using the command chattr, but its not sufficient as the "a" flag only allows for "appendage", ie cat >> test.txt

I was told redhat did it but I'm with ubuntu trying to create a server with LAMP

---

### Post by detectiveinspekta on 2007-01-30
Obviously this is too complicated for a community forum. :o 
Back to google....

---

### Post by detectiveinspekta on 2007-01-30
just in case someone finds this thread looking for the answer or has the answer please do register.

I have a partial solution, it does allow modification and doesn't allow delete. But it doesn't allow new file/folder creation which is a bummer.

So I learned that file creation/deletion is based on permissions of the file the are in.
Doing a ```
ls -l
``` sees the file permission with something like rwx etc. So I put the files inside the folder. Then I did a ```
chmod -w sharedfolder
``` which takes away (hence the "-w" minus sign) write capabilitys. On the files inside the folder itself made sure they were writable with ```
chmod +w file1.txt
```

---

