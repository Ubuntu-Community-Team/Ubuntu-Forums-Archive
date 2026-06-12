---
title: "Unable to remove files"
date: 2009-01-15
forum: Server Platforms
---

### Post by sportster3 on 2009-01-15
I have a server (recently upgraded to Ubuntu 8.10) with a 4TB reiserfs partition.  I went to remove a directory (sudo rm -rf <directory>) and 4 files gave permission denied errors.  An ls -al gives
```

# ls -al
ls: cannot access attrib: Permission denied
ls: cannot access ffile1: Permission denied
ls: cannot access ffile2: Permission denied
ls: cannot access ffile3: Permission denied
total 0
drwxr-x--- 2 backuppc backuppc 216 2009-01-15 09:01 .
drwxr-x--- 3 backuppc backuppc  72 2009-01-15 09:01 ..
?????????? ? ?        ?          ?                ? attrib
?????????? ? ?        ?          ?                ? ffile1
?????????? ? ?        ?          ?                ? ffile2
?????????? ? ?        ?          ?                ? ffile3


```

sudo chown root ffile1 doesn't work.  sudo rm -f ffile1 doesn't work. sudo chmod 777 ffile1 doesn't work.

I'm assuming that these are corrupt files.  Any ideas on how I can delete them?

Thanks

---

### Post by Titan8990 on 2009-01-15
I have seen that problem from putting certain protected windows files on Ubuntu.

No idea on a fix....

---

### Post by HermanAB on 2009-01-15
It looks like a corrupt super block.  You need to repair the file system then try again.

Cheers,

Herman

---

### Post by sportster3 on 2009-01-16
> **HermanAB said:**
> It looks like a corrupt super block.  You need to repair the file system then try again.

Cheers,

Herman

Bummer.  Any idea how long reiserfsck would take on a 4TB partition about 75% full? 

What kind of risk to I run of a repair messing up everything?

---

