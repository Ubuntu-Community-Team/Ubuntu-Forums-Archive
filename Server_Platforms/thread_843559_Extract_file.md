---
title: "Extract file"
date: 2008-06-28
forum: Server Platforms
---

### Post by leewilson78 on 2008-06-28
Hi there, 

Apologies if this is the wrong area of the forum. Basically, I have two Ubuntu servers. I would like to copy certain folders from one to another. I have got as far as creating a tar.gz of the complete home folder. I have also managed to copy that tar.gz backup file to the new server.

The main problem I have now is extracting the file, I have used the following command to extract: 

tar zxf

However, it a folder structure, which at the end contains the original tar.gz file.

I am scratching my head as to why it is not extracting all files and folders... can anyone help.

Thanks
Lee

---

### Post by cariboo on 2008-06-28
Why don't you just transfer over the origional backup file, or did you create the backups file in the sa,e directory that you were backing up? If so just create your backup file outside of the directory you are backing up. More info:

```
man tar
```

Jim

---

