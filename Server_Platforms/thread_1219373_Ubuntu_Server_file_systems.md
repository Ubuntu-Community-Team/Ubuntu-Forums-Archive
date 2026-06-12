---
title: "Ubuntu Server file systems"
date: 2009-07-21
forum: Server Platforms
---

### Post by zetanuxi on 2009-07-21
What is the best file system to format my server hard drives in?
I'm using it as a file and media server. It will service Windows and Linux systems alike.

Is there a file system optimized for use with media? Because I have Windows machines connecting to my server, would I have to format my storage hard drives in NTFS? Or would Samba take care of the format issue if the hard drives were in ext2, ext3, etc.?

---

### Post by iponeverything on 2009-07-21
I would go with ext3. I don't think Samba cares what the underlying format of the drive is. I would not go with ext4 quite yet, as there still seems to be some rare corruption issues poping up now and again.  Speaking from experience, if drive corruption happens to you -- the unlikelihood does not mean much.

I had a reiserfs drive on a production box get totally scrambled on me once.. no fun.

---

### Post by HermanAB on 2009-07-22
Ext3 is stable and the Linux default.  JFS and XFS are more mature and more efficient, especially for large files.  Any of those three will do.

---

### Post by Vegan on 2009-07-22
the default ext3 is fine in my shop. world+dog all like it.

---

### Post by dragos2 on 2009-07-22
> **HermanAB said:**
> Ext3 is stable and the Linux default.  JFS and XFS are more mature and more efficient, especially for large files.  Any of those three will do.

I have ext3 and JFS and XFS. Indeed XFS performs a little better sometimes but you should
have told him that if that a crash occurs the changes of recovery are lower.

I am eager for btrfs and maybe zfs to linux ? Who knows.

---

### Post by HermanAB on 2009-07-22
The choice of UPS is more important than the choice of FS...

---

### Post by druhboruch on 2009-07-22
> **HermanAB said:**
> The choice of UPS is more important than the choice of FS...

I definitely agree with this statement.

---

