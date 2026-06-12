---
title: "Synchrorep - A one click folders synchronization"
date: 2019-09-07
forum: Ubuntu Application Development
---

### Post by sebk69 on 2019-09-07
I've just released version 1.5.5 of my synchronization app.

If you are interested you can find debian package [here]("https://small-iceberg.dev/all_packages/synchrorep-1.5.5.deb").

Find more informations [here]("https://small-iceberg.dev/synchrorep").

For developers, you can find source code on [gihub]("https://github.com/sebk69/Synchrorep").

Have fun !

---

### Post by TheFu on 2019-09-07
Is there a PPA 
or 
a snap?

---

### Post by cruzer001 on 2019-09-07
Nice and simple, I like it.

I use rsync to backup my Home directory to a second drive.  Could this do the same thing?  Sounds like it can.

---

### Post by sebk69 on 2019-09-08
> **TheFu said:**
> Is there a PPA 
or 
a snap?

No, not for the moment : I've not see documentation about ppa but it can be done shortly. I'ill post a comment when it's done

---

### Post by sebk69 on 2019-09-08
> **cruzer001 said:**
> Nice and simple, I like it.

I use rsync to backup my Home directory to a second drive.  Could this do the same thing?  Sounds like it can.

You can do like rsync (use copy option) but if you use sync, it's a bidirectionnal copy (files missing in A are copied to A **and** files missing in B are copied to B)

---

### Post by TheFu on 2019-09-08
s/mont/mount/  there is a typo on the "Overview" section of the website.

Are directories mirrored recursively?
Any known file system limitations?
How are incompatible filenames handled?   exFAT, NTFS, ext2/3/4, ZFS, BTRFS each have slight differences.
Any known file size limitation?  Someone will try to sync a 60GB virtual machine file. 
What happens if the VM file is a "sparse" file?  Will it get exploded or is it handled correctly? tar and rsync have special processing for sparse files. I haven't written any C++ in about 18 yrs and never knew if anything special in the code was needed. [https://www.systutorials.com/136652/handling-sparse-files-on-linux/](https://www.systutorials.com/136652/handling-sparse-files-on-linux/) and [https://www.systutorials.com/240892/how-to-efficiently-archive-a-very-large-sparse-file/](https://www.systutorials.com/240892/how-to-efficiently-archive-a-very-large-sparse-file/) explains.  

What is  *ssh network share*?  Do you mean sftp, scp, sshfs or something else?  I wouldn't include plain FTP support. Preventing people from making poor security choices is important.

What happens if no Trash API is on the system? Files just deleted?  Lots of people run minimal GUI systems.

Perhaps it is clear after install, but is this a GUI tool or can it work on servers?  I don't allow javascript on most websites.

---

### Post by sebk69 on 2019-09-08
> **TheFu said:**
> s/mont/mount/  there is a typo on the "Overview" section of the website.
Thanks, I will check it out

> **TheFu said:**
> Are directories mirrored recursively?
Yes

> **TheFu said:**
> Any known file system limitations?
How are incompatible filenames handled? exFAT, NTFS, ext2/3/4, ZFS, BTRFS each have slight differences.
Any known file size limitation? Someone will try to sync a 60GB virtual machine file.
I use gnome library for managing files, then limitations are gnome limitations 


> **TheFu said:**
> What happens if the VM file is a "sparse" file?  Will it get exploded or is it handled correctly? tar and rsync have special processing for sparse files. I haven't written any C++ in about 18 yrs and never knew if anything special in the code was needed. [https://www.systutorials.com/136652/handling-sparse-files-on-linux/](https://www.systutorials.com/136652/handling-sparse-files-on-linux/) and [https://www.systutorials.com/240892/how-to-efficiently-archive-a-very-large-sparse-file/](https://www.systutorials.com/240892/how-to-efficiently-archive-a-very-large-sparse-file/) explains. 
As I use gnome library to copy, the copy process don't come from my code. I've already use synchrorep with vdi and no problem with it.

> **TheFu said:**
> What is  *ssh network share*?  Do you mean sftp, scp, sshfs or something else?  I wouldn't include plain FTP support. Preventing people from making poor security choices is important.
I mean that I've not be clear with ***ssh network share. ***In fact I mean sftp mounted in gnome. (After the first run, it mount automatically).

> **TheFu said:**
> What happens if no Trash API is on the system? Files just deleted?  Lots of people run minimal GUI systems.
If the remote is not handle filesystem, the file is copied on local Trash

> **TheFu said:**
> Perhaps it is clear after install, but is this a GUI tool or can it work on servers?  I don't allow javascript on most websites.
This is a GUI tool. For next step of development, I will implement batch mode (especially to manage scheduled tasks) but you still need GUI to see logs and answer questions (in case for example of a file modified in both directory). This app is designed for desktop environments.

---

### Post by ryansenn on 2019-09-13
I've never developed anything on ubuntu, so out of interest: what made you decide to use C++? Familiarity with the language? Good GUI support? Sorry if it's a silly question, I code web stuff mainly.

---

