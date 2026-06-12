---
title: "see folder but not files in ubuntu one web page"
date: 2010-09-15
forum: Ubuntu One (CLOSED)
---

### Post by bill53 on 2010-09-15
I have synchronized one home folder and my documents folder by left clicking on the folder and clicking on synchronize with Ubuntu one. I can see the folders on the Ubuntu one web page, but when I click on the folder to open it I can't see the files that are supposed to be there.

How can I see those files? Does the fact that I cannot see the files mean that the folder was synchronized, but the files were not?

---

### Post by duanedesign on 2010-09-16
Ubuntu One sync the Folders (metadata) first, then it syncs the content. You can run the following commands in a Terminal (Applications -> Accessories -> Terminal) to see how many items are in the queue (this number should get smaller over time). 

```
u1sdtool --waiting-metadata | wc -l
```

```
u1sdtool --waiting-content | wc -l
```

You can take off the '| wc -l' to get detailed info about each item waiting to upload.

To see the current transfers.

```
u1sdtool --current-transfers
```

Additionally can you run this command in a Terminal (Applications -> Accessories -> Terminal) and post the output:

```
u1sdtool -s
```

thank you,
duanedesign

---

