---
title: "How to: Move /home to it’s own partition"
date: 2011-08-22
forum: Server Platforms
---

### Post by fade2gray on 2011-08-22
If you have arrived here by searching, you may already have come across [[COLOR="Blue"]**this blog**[/COLOR]]("http://embraceubuntu.com/2006/01/29/move-home-to-its-own-partition/#comments") by Carthik.

While it is excellent in it's instruction, many readers are tripping up when it comes to maintaining the moved '/home' directories/files owner:group properties.

[QUOTE="Carthik"]Now, Copy files over:
Since the &#8220;/home&#8221; directory will have hardlinks, softlinks, files and nested directories, a regular copy (cp) may not do the job completely. Therefore, we use something we learn from the Debian archiving guide:
$cd /home/
$find . -depth -print0 | cpio --null --sparse -pvd /mnt/newhome/

**Make sure everything copied over correctly. You might have to do some tweaking and honing to make sure you get it all right, just in case**.[/QUOTE]
The above code may cause a real nightmare particularly if you have many users in the home directory, as all of the copied files and folders will become root:root.

This would be better handled by performing the following instead which will maintain owner:group properties for all directories/files copied over:-

```
$( cd /home ; tar cfv &#8211; . ) | ( cd /mnt/newhome ; tar xf &#8211; )
```

Hope this helps.

---

### Post by SeijiSensei on 2011-08-23
```
cd /home; rsync -av . /mnt/newhome
```

accomplishes this task as well.

---

### Post by fade2gray on 2011-08-23
> **SeijiSensei said:**
> ```
cd /home; rsync -av . /mnt/newhome
```

accomplishes this task as well.

Thanks for your input.

My observations on a home dIrectory size of 414.81MB:-

elapsed time using ```
( cd /home ; tar cfv – . ) | ( cd /mnt/newhome ; tar xf – )
```= 102 seconds


elapsed time using ```
cd /home; rsync -av . /mnt/newhome
```= 124 seconds

---

