---
title: "Rsync backup-dir default"
date: 2008-05-11
forum: The Cafe
---

### Post by smfaisalabbas on 2008-05-11
Could any one point out the rsync backup-dir defualt? That is if -b option is used but --backup-dir is not used.

In my case I am using rsync on local machine for both source and destination.

My command was 
rsync -auvzbr myDirectory /media/disk/myDirectory

---

### Post by natedawg on 2008-05-11
I'm not sure what the default is but as a side note you should always test your rsync commands with the **-n** option to make sure you know what is going on and don't end up screwing up your files.

---

