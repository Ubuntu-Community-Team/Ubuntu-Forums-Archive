---
title: "files are not uploaded to U1"
date: 2010-12-11
forum: Ubuntu One (CLOSED)
---

### Post by v923z on 2010-12-11
Hi All,
 
I have tried  to back up some material to Ubuntu One. I went through the sequence  Nautilus -> right click -> Synchronise this folder. The computer  was working for some time, and now the folder's symbol has a green and  blue arrow on it. Yet, when I log on to my Ubuntu One account, I see  only the folders, but not the files. Also, the quote counter shows that I  use 0% of the alloted 2 GB. (The folder is something like 200 MB on my  computer.) My question is if I miss a step here. Is there something else  that I should do in order to back up the content of a directory? I  don't want to move everything to the Ubuntu One folder on my computer. I run Maverick Meerkat.
 Thanks,
 Zoltán

---

### Post by duanedesign on 2010-12-12
The circular blue and green arrows means it is syncing. Ubuntu One syncs the metadata(folders) first, then the content. When the sync is complete the icon on the folder should change to a green tick mark.

From the Terminal (Applications > Accessories > Terminal) you can get the number of items waiting to be synced with these commands:

```
u1sdtool --waiting-metadata | wc -l
```

and

```
u1sdtool --waiting-content | wc -l
```

You can track progress as the numbers get smaller.

---

### Post by v923z on 2010-12-12
Hi,

Thanks for the reply! Unfortunately, it doesn't solve the problem. As far as I see, nothing really happens. The number of items waiting in the queue does not change at all. For some reason, the folders are uploaded properly (on the web interface, I see the same directory structure as on my computer), but the files are just not transferred. Any ideas why this c/should happen?
Zoltán

---

