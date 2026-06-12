---
title: "recovery of lost data"
date: 2008-05-02
forum: Security
---

### Post by pkj on 2008-05-02
Hi,

Just want to know if there are any tools available to recover deleted data from the USB drive....

pkj

---

### Post by munkyeetr on 2008-05-02
One thing to try first is to plug the drive in and once it mounts, press CTRL+H to show all hidden files and look in the .Trash folders and see if the files are actually gone. They may still be sitting there and you can just copy them to whereever you want.

If they are truly deleted, it will then depend on the filesystem the USB drive is formatted as...

If it is in NTFS or FAT(32) you could probably plug it into a Windows machine and use something like [Restoration]("http://www.snapfiles.com/get/restoration.html") to "undelete" the files.

If it is formatted ext2/3, you would be out of luck as far as I know.

---

### Post by lemming465 on 2008-05-02
Yes e.g. *autopsy*

---

### Post by cdenley on 2008-05-02
If it is ntfs, you can use ntfsundelete from the ntfsprogs package. The testdisk package has a program called photorec which will search for common file types on any filesystem, deleted or not. You will lose the file names/paths, though.

---

### Post by pkj on 2008-05-02
Thanks

pkj

---

