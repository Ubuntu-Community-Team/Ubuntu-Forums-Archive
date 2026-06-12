---
title: "Ubuntu One and Large files"
date: 2010-09-12
forum: Ubuntu One (CLOSED)
---

### Post by svyatoslav on 2010-09-12
Good day Ubuntu One Team!

I have a small problem. My system is Ubuntu 10.04. My u1 size is 50G. I have copied the file size 9G to "Ubuntu one" directory on my local computer. After the synchronization process on the file icon appeared green check mark, so, synchronization is completed. But I do not see that file on the site [https://one.ubuntu.com](https://one.ubuntu.com). Smaller files are synchronized correctly.

P.S.

After the beginning of the synchronization of large files the size of the directory tmp has been increased up to 30G. Since space is not enough, I cleaned this directory. Perhaps the reason for this?

---

### Post by duanedesign on 2010-09-13
From the command line (Terminal) you can get additional detaiils about pending syncs. You can run the following commands:

```
u1sdtool --waiting-metadata | wc -l
```
and
```
u1sdtool --waiting-content | wc -l
```

Those commands will provide the number of items waiting. You can remove the '| wc -l' to get details about the items waiting to sync. Thhis will be helpfull if for some reason a large amount of metadata is syncing prior to your upload. Also you might try:

```
u1sdtool --current-transfers
```

I will look into what if any possible upload size their might be.

thank you,
duanedesign

---

