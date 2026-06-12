---
title: "Somebody help me.. I have problem About file system.. My space lost."
date: 2010-08-22
forum: Server Platforms
---

### Post by kongkiat2000 on 2010-08-22
[IMG]http://img832.imageshack.us/img832/7407/selection001e.png[/IMG]

Please Look at image capture..
capacity 141.0GB
used 90.8 GB
available 50.3 GB

Why root use 4.9 GB.. It should eq used..
Why it lost 89.9 GB.. Pls Help me... What happen..
I use file system EXT4..
How I fix it..

Thk U...

---

### Post by clrg on 2010-08-22
Edit: See next post, he's got it right :)

---

### Post by bcbc on 2010-08-22
I think the disk usage analyzer is 'misleading' (putting it politely). My one shows the same: / is 4.9GB 100% but I have space available too.

I guess it's analyzing the space that is USED. So of the 4.9GB used on / root, (100% under /) then 49% is under /usr, 35% is under /home etc. It doesn't show how much space is free.

Just go to a command line and run: df -h

Still not sure where your other 90GB used would be... is this a wubi install? that might explain it.

---

### Post by kongkiat2000 on 2010-08-23
I don't use wubi.. This is my "df -h" Thank U.

[IMG]http://img266.imageshack.us/img266/8301/selection002g.png[/IMG]

---

### Post by bcbc on 2010-08-23
So, are the files that make up the 90GB still there, i.e. is it just a bug in the disk usage analyzer? Or have you actually lost that data?

---

### Post by clrg on 2010-08-23
You have two mounted partitions, '/' and '/home/samba'. 

/ has 46GB free space
/home/samba has 710GB free space

There is no problem with disk space. I advise you to use the coreutils (like df) instead of some strange GUI programs in order to get reliable information.

Edit: If you want to know the size of a directory, use du. For example:

```
 du -kshc /home/samba/folder 
```

---

