---
title: "File belongs to root with chmod 600 but a user can still delete/rename it???"
date: 2006-09-05
forum: Server Platforms
---

### Post by HTorun on 2006-09-05
Hello everybody,

I recently installed ubuntu server (LAMP). Several years ago I had some experience with Unix systems but you may consider me a beginner. 

I noticed that a user can delete or rename a file although the file owner is root and no read or write permissions are granted to the user(chmod 600).

See this for an example:
```
tesuser@efs1:~$ ls -l
total 4
drwxr-xr-x 7 testuser testuser 4096 2006-09-05 22:58 mytestdir
-rw------- 1 root    root       0 2006-09-05 23:59 test
testuser@efs1:~$ mv test test1
testuser@efs1:~$ ls -l
total 4
drwxr-xr-x 7 testuser testuser 4096 2006-09-05 22:58 mytestdir
-rw------- 1 root    root       0 2006-09-05 23:59 test1
testuser@efs1:~$ rm test1
rm: remove write-protected regular empty file `test1'? y
testuser@efs1:~$ ls -l
total 4
drwxr-xr-x 7 testuser testuser 4096 2006-09-05 22:58 mytestdir
testuser@efs1:~$
```

Is this normal/expected? Is there a way I can prevent a user from deleting/renaming a file in home dir?

Thanks,

---

### Post by Glut on 2006-09-06
That's expected behaviour. Directory permission 'w' allows the user to delete any files in the directory.
You can override this with the 'sticky bit'. For reference: *chmod +t /home/foobar* will do it for you. It's a valid thing to do, but you will need to make sure that everything will play nicely with a sticky home (e.g. X/gdm)

---

### Post by HTorun on 2006-09-06
> **Glut said:**
> That's expected behaviour. Directory permission 'w' allows the user to delete any files in the directory.
You can override this with the 'sticky bit'. For reference: *chmod +t /home/foobar* will do it for you. It's a valid thing to do, but you will need to make sure that everything will play nicely with a sticky home (e.g. X/gdm)
Thanks for the tip Glut. At first it did not work as I wanted because the sticky bit on a directroy does not prevent a user to delete/rename a file if he/she is the owner of that directory. So I checked man pages for chmod +t. What I did was to "chown root" the home directory of the user and give write permission to the group user belongs as well as chmod +t.

I hope it is safe to do this. Any comments on security implications of doing this?

---

