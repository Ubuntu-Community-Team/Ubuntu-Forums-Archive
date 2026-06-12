---
title: "Retaining &quot;Date Created&quot; information..."
date: 2014-11-04
forum: Server Platforms
---

### Post by ooboontwo on 2014-11-04
Hello,

My company is running a small Linux file server and we've come across a problem that I am unsure how to resolve.

All our workstations are PCs running Windows 7. Therefore, we use Samba to share files between our Windows 7 PCs and the Linux file server which is running Jaunty.

We've just noticed that when modifying files on the file server the 'Date Created' changes along with the 'Date Modified.' I am supposing that this occurs because the file server or Samba is essentially removing the old version and creating a new instance of the modified file.

Is there any way to retain the correct 'Date Created' stamp when saving modified versions on the file server? Also, it would be great to know if this is Samba or Ubuntu itself which is causing the 'Date Created' to change with the 'Date Modified.'

Thank you!

---

### Post by lukeiamyourfather on 2014-11-04
As far as I know the date created attribute is not a POSIX file system requirement. Samba is probably using the modified date attribute for both since the underlying file system and operating system in this case don't actually track date created attribute.

---

### Post by LHammonds on 2014-11-04
When using ext2 or ext3, there is no "Date Created" attribute.

ext4 has [crtime]("http://tecadmin.net/file-creation-time-linux/") but it is not identical to "Date Created" on a FAT or NTFS system.

I'm not sure Samba would translate crtime to "Date Created" if the underlying system was ext4 so you'd have to experiment.  If it is already ext4, then you already know that answer.  I suspect it will always be linked to the modified date with no difference between the two.

---

### Post by ooboontwo on 2014-11-10
> **LHammonds said:**
> When using ext2 or ext3, there is no "Date Created" attribute.

ext4 has [crtime]("http://tecadmin.net/file-creation-time-linux/") but it is not identical to "Date Created" on a FAT or NTFS system.

I'm not sure Samba would translate crtime to "Date Created" if the underlying system was ext4 so you'd have to experiment.  If it is already ext4, then you already know that answer.  I suspect it will always be linked to the modified date with no difference between the two.

Thank you for this info. Our drives are ext3, so I will experiment with ext4 and see how it goes.

---

### Post by tgalati4 on 2014-11-10
Can you describe the Use Case?  Exactly how is the Date Created used in your network?  It might be worth hanging an external drive off of your server that is formatted with NTFS and see if that preserves the Date Created attribute.  Linux only cares about last written (modified) and last read (accessed).  Usually the file's header contains the first created date in the program making the file.  Otherwise including today's date in the file name when creating a new file would preserve it.  That requires naming discipline.

Do you use the date for deduplication or for backup or version control?

You might be able to use the *touch* command to preserve the Date Created by writing a script when certain applications are called.

```
man touch
```

---

### Post by nerdtron on 2014-11-10
> We've just noticed that when modifying files on the file server the  'Date Created' changes along with the 'Date Modified.' I am supposing  that this occurs because the file server or Samba is essentially  removing the old version and creating a new instance of the modified  file.

I think what is happening here is like this.
1. Opening a file from the samba share in windows 7.
2. Windows will download a copy of this file locally so that you can edit it.
3. When you save it, windows will re-upload the file.
4. Basically samba will see that you are uploading a new file with the same filename and replaces the current in the server.

Boom! Newly created file.

Just my theory though. I haven't really payed attention to it when I was using samba share. I cant right now.

---

### Post by sudodus on 2014-11-10
> **ooboontwo said:**
> ...the Linux file server which is running Jaunty.

The Ubuntu version Jaunty alias 9.04 has passed end of life long ago ([October 23, 2010]("https://lists.ubuntu.com/archives/ubuntu-announce/2010-September/000137.html")), and receives no security updates. I suggest that you replace the operating system with a current version. The long time support (LTS) versions are supported for 5 years, while Jaunty was only supported for 18 months and the new non-LTS versions are only supported for 9 months.

So depending on the computer hardware, I suggest that you consider Ubuntu Server 12.04.5 LTS (Precise) or 14.04.1 LTS (Trusty).

---

