---
title: "Create tgz file (with tar command) and only include /home/ directory"
date: 2008-06-10
forum: Server Platforms
---

### Post by mroski on 2008-06-10
Hello friends, I am trying to create a backup system, I have readed this article: [https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

What I want to do is to backup only the directory /home/ of my server because it is there that I store the mainly important information.

I have tried different commands but I can not do what I want, the last command I have tried was:

```
 tar -cvpzf /home/www/backup/backup.tgz --exclude=/proc --exclude=/lost+found --exclude=/home/www/backup/backup.tgz --exclude=/mnt --exclude=/sys
```
This should exclude all directories excepting /home/ (there are more directories and I have already tried to exclude them).

And one question related to this: How can I create an executable for PHP exec() function as to do what I asked before (backup of /home/ directory)?

Thanks !

---

