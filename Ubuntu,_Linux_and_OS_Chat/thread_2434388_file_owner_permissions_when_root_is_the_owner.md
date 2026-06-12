---
title: "file owner permissions when root is the owner"
date: 2020-01-04
forum: Ubuntu, Linux and OS Chat
---

### Post by Skaperen on 2020-01-04
a file owned by root has permission mode in the owner bits as "r--".   that is no "w" and no "x" permission.  you can set this with "chmod 4xx filename" where "x" can be any octal digit. when root tries to execute the  file the result is "permission denied".  however, when root tries to  open the file for writing, it succeeds and the file is truncated.  does  this sound right to you?

---

### Post by bernard010 on 2020-01-19
Yes unless you change the root permissions. By changing file owner and group or with chmod.
To change or edit files of root that is where sudo comes in. r,w,x  chmod same except 4,2,1
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
Question how can x become any octal digit ? I don't understand. read is 4 and write is 2 ,
execute is 1

Am I correct? I am still re-learning some of this. Thanks, the refresher comes to mind, been a while.

---

### Post by Skaperen on 2020-01-20
IOW, a non-root user can prevent itself from executing or writing an owned file by doing chmod 4xx filename while root can only do this for execute but not for write.  this is, therefore, something a non-root user can do but root cannot do.  it sounds inconsistent to me.  it also sounds like my newest sysadmin job prospect interview question (when the day comes i need to hire another).

---

### Post by Skaperen on 2020-01-20
chmod will accept any octal digit where i showed.  other values are combinations of bits, such as 7 means all 3 bits in that position are ON.

---

### Post by kevdog on 2020-01-23
I have no idea what you guys are talking about.

If a file is owned by root with permissions 400 (r--,---,---), there is no way the root user can modify this file.  Try it.  Create a 400 file owned by root and then try to use vim/nano/whatever to write to it.   You can't.  You must change the permissions to at least 600 for root to write to the file.

---

### Post by Skaperen on 2020-01-23
```

lt2a/root /root 1# ls -dl foo
/bin/ls: cannot access 'foo': No such file or directory
lt2a/root /root 2# echo > foo
lt2a/root /root 3# ls -dl foo
-rw-r--r-- 1 root root 1 Jan 23 21:35 foo
lt2a/root /root 4# chmod 400 foo
lt2a/root /root 5# ls -dl foo
-r-------- 1 root root 1 Jan 23 21:35 foo
lt2a/root /root 6# echo bar > foo
lt2a/root /root 7# ls -dl foo
-r-------- 1 root root 4 Jan 23 21:36 foo
lt2a/root /root 8# cat foo
bar
lt2a/root /root 9# 

```

---

### Post by Skaperen on 2020-01-23
i meant to do [COLOR=#0000cd][FONT=courier new]**echo foo**[/FONT][/COLOR] but an empty line actually shows the change as a result of writing more readily, anyway.  i was not going to run some program that might misinterpret the permission bits, give an error message resulting from that misinterpretation, and quit.  the bash shell will really *try* to open the file for writing with a ">" redirection.  for root it succeeds even if root owns the file.

---

