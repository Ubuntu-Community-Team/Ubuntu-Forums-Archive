---
title: "file system type"
date: 2013-07-07
forum: Server Platforms
---

### Post by nerdtron on 2013-07-07
Any suggestions on what filesytem is good at handling the following scenario?

  * nfs file server with large number(1,000,000 files in a directory) of small files(less than 4kb)
  * nfs file server with small number of large files(21GB minimum)

I have used ext4 and XFS with the default parameters. Will I gain any significant improvements (both read and write, but mostly write) by modifying mount options? Or should I look for other filesystem types?

Thanks!

---

### Post by sandyd on 2013-07-07
> **nerdtron said:**
> Any suggestions on what filesytem is good at handling the following scenario?

  * nfs file server with large number(1,000,000 files in a directory) of small files(less than 4kb)
  * nfs file server with small number of large files(21GB minimum)

I have used ext4 and XFS with the default parameters. Will I gain any significant improvements (both read and write, but mostly write) by modifying mount options? Or should I look for other filesystem types?

Thanks!

For ext4-> See [https://www.kernel.org/doc/Documentation/filesystems/ext4.txt](https://www.kernel.org/doc/Documentation/filesystems/ext4.txt)
All of the info about the options and performance is at the top.

Generally, I find JFS good for tonnes of small files, and XFS good for large files. However, in the past, I have found XFS does not handle disk/io/corruption errors as well as other filesystems

---

