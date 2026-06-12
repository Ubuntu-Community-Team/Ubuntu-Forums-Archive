---
title: "Creating an encrypted usb"
date: 2015-03-20
forum: Security
---

### Post by Drenriza on 2015-03-20
I'am currently trying to make a encrypted usb device that can be recognised by Linux, Windows and OS X systems without any special "magic". 
I have tried and follow this guide [https://help.ubuntu.com/community/EncryptedFilesystemsOnRemovableStorage](https://help.ubuntu.com/community/EncryptedFilesystemsOnRemovableStorage) but it does not seem to accomplish this.

Anyone who can point me in the right direction to accomplish this?

I also have a current problem where i followed the guide above, and wanted to get back to ground zero for the usb device by creating a new fat32 partition.

But now disk manager tells me
> Error deleting partition /dev/sdb1: Command-line `parted --script "/dev/sdb" "rm 1"' exited with non-zero exit status 1: Error: Partition doesn't exist. (udisks-error-quark, 0)

---

