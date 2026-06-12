---
title: "Samba Filesystem type impacts performance?"
date: 2010-06-04
forum: Server Platforms
---

### Post by X1R1 on 2010-06-04
Hi guys just wondering, I installed a month or so ago a Samba File Server along with Active Directory integration in my company. I choose to install on my newly created raid array, all in ext3 filesystem. The purpose of this fileserver is to have lots of files from the different departments on the company (all windows workstations except mine).

Everyone has a private folder and a department folder, along with the common folder for all employees.

So my question is, did I made a mistake formating all to ext3? would I get a significant increase in performance if I resize the current ubuntu partiton and created a new NTFS new one and move the files to it?

thanks in advance

---

### Post by HermanAB on 2010-06-04
Howdy,

Note that NTFS is not 100% supported on Linux.  It mostly works though.

I have done some tests a few years ago and for raw speed on a large file store, you should probably use XFS or JFS.  My favourite is JFS.

---

### Post by X1R1 on 2010-06-05
Herman,

Thanks for your reply. So, having the linux server on a different filesystem other than ntfs doesnt impact performance?

I ask because for example, if you copy a large file from a linux partition to a usb key in ntfs format, the copy speed starts to decrease rapidly, i tought that would be the same case for disk to disk copying?

---

