---
title: "Specifying inode of a link"
date: 2008-05-08
forum: Security
---

### Post by aparicio on 2008-05-08
Hello

I know how to create a file with an inode the same as another file's inode. This is done simply by ```
ln TARGET LINK
```
But is there a way to create a file pointing to an inode that I specify by hand? For instance, suppose that I know a certain file's inode and write it down, then I rm the file. The inode now has no files pointing to it, so is there a command to create a file pointing to that inode that I still know?

Thank you

---

### Post by /etc/init.d/ on 2008-05-08
If an inode has no files pointing to it, it is considered free, and can be overwritten with new data.  Once an inode's reference count reaches zero, you can't guarantee that the original data will still be there, even if there was a way to "re-reference" it with the ln command.

---

### Post by aparicio on 2008-05-14
Yes, I understand that it is considered free and the data might have already been overwritten. But suppose I still want to try. Is there a way to re-reference it, as you put it, with ln or otherwise?

---

### Post by /etc/init.d/ on 2008-05-19
> **aparicio said:**
> Is there a way to re-reference it, as you put it, with ln or otherwise?
If you really want to reinstate a file potentially now containing corrupted data, debugfs might be able to do it.

---

