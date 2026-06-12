---
title: "Users Home directory invisible"
date: 2012-01-30
forum: Server Platforms
---

### Post by rsteinmetz70112 on 2012-01-30
I have a new problem. One of my users home directory is suddenly invisible. 

su -k ./username shows significant size (several hundred megabytes)
ls -l ./username shows no files at all 
mkdir ./username/knowndirectory returns "directory exists"
fsck of the file system shows no problems.

I'm stumped.

---

### Post by ruffEdgz on 2012-01-30
Are you root when you complete the commands or are you another user?:
```

ls -l ./username

```
Can you type in this command and share it on the forum (make sure to change any information to another name just in case):
```

ls -ld ./username

```
We should see something like so:
```

drwxr-xr-x 2 username group 4096 2012-01-30 12:30 ./username/

```
It sounds like a directory permission issue to me.

---

