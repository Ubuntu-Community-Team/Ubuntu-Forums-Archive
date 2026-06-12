---
title: "Trying to understand how /usr/bin/ip and /bin/ip are linked"
date: 2023-10-31
forum: Ubuntu/Debian BASED
---

### Post by bpolgardy on 2023-10-31
I'm running Pop! OS 22.04 LTS, however, this question is a very general one and most likely not specific to this flavor only.

So, I've been digging into the Linux file system to try to find out how it is structured and where certain files are located.

Specifically, I looked at the **[FONT=courier new]ip[/FONT]** command/utility.

**[FONT=courier new]$whereis ip[/FONT]** shows the following two results (actually four, but I'm not counting the man page results):

**[FONT=courier new]/usr/bin/ip[/FONT]** and [FONT=courier new]**/usr/sbin/ip**[/FONT].

These two files are pointing to different inodes (28050065 and 28182231 respectively).

A further search reveals that **[FONT=courier new]/usr/sbin/ip[/FONT]** is actually a symlink to [FONT=courier new]**/bin/ip**[/FONT].

Now, interestingly, [FONT=courier new]**/bin/ip**[/FONT] appears to have an inode of 28050065, which is the same as that of [FONT=courier new]**/usr/bin/ip**[/FONT].

It is my understanding that this means that **[FONT=courier new]/bin/ip[/FONT]** and [FONT=courier new]**/usr/bin/ip**[/FONT] are linked.

However, I cannot, for the life of me, figure out how these two files are actually linked to each other.

Running [FONT=courier new]**ls -l**[/FONT] on both files gives the following:

-[FONT=courier new][B]rwxr-xr-x 1 root root 718896 Mar 24  2022 /usr/bin/ip

-rwxr-xr-x 1 root root 718896 Mar 24  2022 /bin/ip
[/B][/FONT]
As shown above, both files have a hard link count of 1. I believe this number ("1") refers to the file's directory entry itself, which serves as one link to the file's inode, thus suggesting there are no other links to either file. 

How are these files linked if there doesn't seem to be a hard link (nor a symlink) associated with them yet they both point to the same inode?

---

### Post by The Cog on 2023-10-31
/bin is a link to usr/bin. So /usr/bin/ip and /bin/ip are the same file, one inode, but two paths to find it.
```
~$ ls -ld /usr/bin /bin
lrwxrwxrwx 1 root root     7 May  2 11:37 /bin -> usr/bin
drwxr-xr-x 2 root root 69632 Oct 26 08:19 /usr/bin
```

---

### Post by bpolgardy on 2023-10-31
Awesome! Thank you very much!

---

