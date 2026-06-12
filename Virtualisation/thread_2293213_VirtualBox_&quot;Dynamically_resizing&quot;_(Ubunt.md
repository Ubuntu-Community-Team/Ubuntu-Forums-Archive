---
title: "VirtualBox: &quot;Dynamically resizing&quot; (Ubuntu guest) hard drive does not resize"
date: 2015-09-03
forum: Virtualisation
---

### Post by codingbutstillaliv on 2015-09-03
I am running my beloved Ubuntu in a Windows 8.1 machine under VirtualBox and configured the virtual disk drive to automatically grow if needed. However, it does not do so and I am running out of space.

---

### Post by monkeybrain20122 on 2015-09-03
Well the disk doesn't automatically grow. It just means that you can add contents to VM until the allocated disk is filled. :) Kind of misleading (I suppose you can't add anything to a static VM) but this is what it really means. Found out a while back. :)

Edited: [http://www.howtogeek.com/124622/how-to-enlarge-a-virtual-machines-disk-in-virtualbox-or-vmware/](http://www.howtogeek.com/124622/how-to-enlarge-a-virtual-machines-disk-in-virtualbox-or-vmware/)

---

### Post by SeijiSensei on 2015-09-04
If you have a lot of unallocated space on the Windows partition, you can use it for storage of documents, video, etc.  Create a directory in Windows, then make it available using the "Shared Folders" feature of VirtualBox.  I use this method to make my large NTFS-formatted drive with video files on it accessible from my Kubuntu VM running on top of Windows.

Because NTFS doesn't support POSIX file permissions, you can't put executable files on an NTFS-formatted filesystem.  But for bulk storage it works just fine.

---

