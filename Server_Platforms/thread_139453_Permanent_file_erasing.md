---
title: "Permanent file erasing"
date: 2006-03-04
forum: Server Platforms
---

### Post by draconian on 2006-03-04
I do a lot of work from home and my employer insists that all file I work on are erased using a Gutmann (stop hardware recovery) method.
I have finally decided to dump Windows as it slowed my laptop down so much I was losing the will to live!
I now have to demonstrate to my employer that I can still erase the files securely using Ubuntu
Is there a program out there that will enable me to achieve this?

Thanx

---

### Post by roshan.s on 2006-03-04
Take a look at the shred command. Type "man shred" in a terminal to see the details.

To delete a file, type "shred --remove filename" or "shred -u filename"

---

### Post by draconian on 2006-03-04
Thank you for the quick respaonse, I will read it right now

:) \\:D/ ;)

---

### Post by sockrebel on 2006-03-12
how do i remove directories with shred?  there is no recursive option
tia

---

### Post by skymt on 2006-03-12
I'd use the find command, as follows:

```

find dir_to_delete -type f -exec shred &#8217;{}&#8217; \;
rm -r dir_to_delete

```

The first command will shred every file in the directory, the second recursively deletes the (now empty) directories. I haven't tested this, so be careful. The find command is lifted from 'man find' replacing rm with shred, so it should work fine.

---

### Post by JoWilly on 2006-03-12
[QUOTE=draconian]I do a lot of work from home and my employer insists that all file I work on are erased using a Gutmann (stop hardware recovery) method.
I have finally decided to dump Windows as it slowed my laptop down so much I was losing the will to live!
I now have to demonstrate to my employer that I can still erase the files securely using Ubuntu
Is there a program out there that will enable me to achieve this?

Thanx[/QUOTE]

Install "wipe", its in the repos.

To delete dirs use it like this: wipe -rfs

Add a nautilus action (menu system > prefs > nautilus actions) like this to make it available in nautilus (you can then select all the dirs and files you want and shred them with 1 right click):

path : wipe
params: -rfs %M

Edit: you need to install nautilus-actions from the repos for this...

---

### Post by jon_k on 2006-03-12
Unfortunately, shred is useless on most modern file systems - it doesn't work effectively on any that support journalling. (ext3, reiserfs, etc).

You'll be limited to ext2 or other non journaling FS types for this to work.

---

### Post by trriangle on 2006-03-28
Hi,

When I was also in need of totaly erasing data I came across a boot disk CD image that claimed to include tool to erase data completely. Guttman's algorithm was also among it's featurest. The tool was KillDisk and it was launched from DOS. that turned out to be truth and it really erased data completely. On that image (Boot Disk) there were also other data tools for backup and recovery. If you wish you can give it a glance too.
[http://www.ntfs.com/boot-disk.htm](http://www.ntfs.com/boot-disk.htm)

---

### Post by ihristov on 2007-06-13
I believe using an encrypted disk mitigates the issues of a journaling file system like ext3.

---

