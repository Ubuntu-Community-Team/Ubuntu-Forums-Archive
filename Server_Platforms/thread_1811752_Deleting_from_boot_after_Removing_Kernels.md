---
title: "Deleting from /boot after Removing Kernels"
date: 2011-07-25
forum: Server Platforms
---

### Post by borntoventure on 2011-07-25
I received an alarm on a server stating that the /boot partition was 90% used. The partition contains several old kernels so I removed all but the current and previous 2 known stable versions using apt. This did not purge the files from the /boot partition.

The /boot partition still contains the kernel files for 12 old versions. Is it safe to delete these files after the kernel has been removed using apt? Below is the output of the /boot partition.

Thanks in advance for any help!



```
total 201M
drwxr-xr-x  4 root root 3.0K 2011-07-25 08:54 .
drwxr-xr-x 24 root root 4.0K 2011-07-25 09:39 ..
-rw-r--r--  1 root root 621K 2010-04-16 07:02 abi-2.6.32-21-server
-rw-r--r--  1 root root 621K 2010-06-03 18:24 abi-2.6.32-22-server
-rw-r--r--  1 root root 631K 2010-06-11 06:59 abi-2.6.32-23-server
-rw-r--r--  1 root root 631K 2010-09-16 13:55 abi-2.6.32-24-server
-rw-r--r--  1 root root 632K 2010-10-16 15:51 abi-2.6.32-25-server
-rw-r--r--  1 root root 632K 2010-11-24 05:13 abi-2.6.32-26-server
-rw-r--r--  1 root root 632K 2010-12-01 23:22 abi-2.6.32-27-server
-rw-r--r--  1 root root 632K 2011-01-10 18:42 abi-2.6.32-28-server
-rw-r--r--  1 root root 632K 2011-02-11 15:52 abi-2.6.32-29-server
-rw-r--r--  1 root root 632K 2011-03-01 20:02 abi-2.6.32-30-server
-rw-r--r--  1 root root 632K 2011-04-08 18:07 abi-2.6.32-31-server
-rw-r--r--  1 root root 632K 2011-04-20 17:53 abi-2.6.32-32-server
-rw-r--r--  1 root root 632K 2011-07-07 20:35 abi-2.6.32-33-server
-rw-r--r--  1 root root 108K 2010-04-16 07:02 config-2.6.32-21-server
-rw-r--r--  1 root root 108K 2010-06-03 18:24 config-2.6.32-22-server
-rw-r--r--  1 root root 108K 2010-06-11 06:59 config-2.6.32-23-server
-rw-r--r--  1 root root 108K 2010-09-16 13:55 config-2.6.32-24-server
-rw-r--r--  1 root root 109K 2010-10-16 15:51 config-2.6.32-25-server
-rw-r--r--  1 root root 109K 2010-11-24 05:13 config-2.6.32-26-server
-rw-r--r--  1 root root 109K 2010-12-01 23:22 config-2.6.32-27-server
-rw-r--r--  1 root root 109K 2011-01-10 18:42 config-2.6.32-28-server
-rw-r--r--  1 root root 109K 2011-02-11 15:52 config-2.6.32-29-server
-rw-r--r--  1 root root 109K 2011-03-01 20:02 config-2.6.32-30-server
-rw-r--r--  1 root root 109K 2011-04-08 18:07 config-2.6.32-31-server
-rw-r--r--  1 root root 109K 2011-04-20 17:53 config-2.6.32-32-server
-rw-r--r--  1 root root 109K 2011-07-07 20:35 config-2.6.32-33-server
drwxr-xr-x  3 root root 4.0K 2011-07-25 08:54 grub
-rw-r--r--  1 root root 8.7M 2010-06-11 09:18 initrd.img-2.6.32-21-server
-rw-r--r--  1 root root 8.7M 2010-06-11 09:54 initrd.img-2.6.32-22-server
-rw-r--r--  1 root root 8.7M 2010-07-13 15:08 initrd.img-2.6.32-23-server
-rw-r--r--  1 root root 8.7M 2010-09-21 08:31 initrd.img-2.6.32-24-server
-rw-r--r--  1 root root 8.7M 2010-11-01 12:22 initrd.img-2.6.32-25-server
-rw-r--r--  1 root root 8.7M 2011-01-06 21:35 initrd.img-2.6.32-26-server
-rw-r--r--  1 root root 8.7M 2011-01-20 08:42 initrd.img-2.6.32-27-server
-rw-r--r--  1 root root 8.7M 2011-01-28 07:52 initrd.img-2.6.32-28-server
-rw-r--r--  1 root root 8.7M 2011-03-15 09:28 initrd.img-2.6.32-29-server
-rw-r--r--  1 root root 8.7M 2011-03-21 08:12 initrd.img-2.6.32-30-server
-rw-r--r--  1 root root 8.7M 2011-05-12 09:04 initrd.img-2.6.32-31-server
-rw-r--r--  1 root root 8.7M 2011-06-03 09:25 initrd.img-2.6.32-32-server
-rw-r--r--  1 root root 8.7M 2011-07-25 08:54 initrd.img-2.6.32-33-server
drwxr-xr-x  2 root root  12K 2010-06-11 09:12 lost+found
-rw-r--r--  1 root root 157K 2010-03-23 04:40 memtest86+.bin
-rw-r--r--  1 root root 2.1M 2010-04-16 07:02 System.map-2.6.32-21-server
-rw-r--r--  1 root root 2.1M 2010-06-03 18:24 System.map-2.6.32-22-server
-rw-r--r--  1 root root 2.1M 2010-06-11 06:59 System.map-2.6.32-23-server
-rw-r--r--  1 root root 2.1M 2010-09-16 13:55 System.map-2.6.32-24-server
-rw-r--r--  1 root root 2.1M 2010-10-16 15:51 System.map-2.6.32-25-server
-rw-r--r--  1 root root 2.1M 2010-11-24 05:13 System.map-2.6.32-26-server
-rw-r--r--  1 root root 2.1M 2010-12-01 23:22 System.map-2.6.32-27-server
-rw-r--r--  1 root root 2.1M 2011-01-10 18:42 System.map-2.6.32-28-server
-rw-r--r--  1 root root 2.1M 2011-02-11 15:52 System.map-2.6.32-29-server
-rw-r--r--  1 root root 2.1M 2011-03-01 20:02 System.map-2.6.32-30-server
-rw-r--r--  1 root root 2.1M 2011-04-08 18:07 System.map-2.6.32-31-server
-rw-r--r--  1 root root 2.1M 2011-04-20 17:53 System.map-2.6.32-32-server
-rw-r--r--  1 root root 2.1M 2011-07-07 20:35 System.map-2.6.32-33-server
-rw-r--r--  1 root root 1.4K 2010-04-16 07:05 vmcoreinfo-2.6.32-21-server
-rw-r--r--  1 root root 1.4K 2010-06-03 18:27 vmcoreinfo-2.6.32-22-server
-rw-r--r--  1 root root 1.4K 2010-06-11 07:02 vmcoreinfo-2.6.32-23-server
-rw-r--r--  1 root root 1.4K 2010-09-16 13:58 vmcoreinfo-2.6.32-24-server
-rw-r--r--  1 root root 1.4K 2010-10-16 15:53 vmcoreinfo-2.6.32-25-server
-rw-r--r--  1 root root 1.4K 2010-11-24 05:15 vmcoreinfo-2.6.32-26-server
-rw-r--r--  1 root root 1.4K 2010-12-01 23:28 vmcoreinfo-2.6.32-27-server
-rw-r--r--  1 root root 1.4K 2011-01-10 18:43 vmcoreinfo-2.6.32-28-server
-rw-r--r--  1 root root 1.4K 2011-02-11 15:53 vmcoreinfo-2.6.32-29-server
-rw-r--r--  1 root root 1.4K 2011-03-01 20:08 vmcoreinfo-2.6.32-30-server
-rw-r--r--  1 root root 1.4K 2011-04-08 18:13 vmcoreinfo-2.6.32-31-server
-rw-r--r--  1 root root 1.4K 2011-04-20 17:54 vmcoreinfo-2.6.32-32-server
-rw-r--r--  1 root root 1.4K 2011-07-07 20:38 vmcoreinfo-2.6.32-33-server
-rw-r--r--  1 root root 4.0M 2010-04-16 07:02 vmlinuz-2.6.32-21-server
-rw-r--r--  1 root root 4.0M 2010-06-03 18:24 vmlinuz-2.6.32-22-server
-rw-r--r--  1 root root 4.0M 2010-06-11 06:59 vmlinuz-2.6.32-23-server
-rw-r--r--  1 root root 4.0M 2010-09-16 13:55 vmlinuz-2.6.32-24-server
-rw-r--r--  1 root root 4.0M 2010-10-16 15:51 vmlinuz-2.6.32-25-server
-rw-r--r--  1 root root 4.0M 2010-11-24 05:13 vmlinuz-2.6.32-26-server
-rw-r--r--  1 root root 4.0M 2010-12-01 23:22 vmlinuz-2.6.32-27-server
-rw-r--r--  1 root root 4.0M 2011-01-10 18:42 vmlinuz-2.6.32-28-server
-rw-r--r--  1 root root 4.0M 2011-02-11 15:52 vmlinuz-2.6.32-29-server
-rw-r--r--  1 root root 4.0M 2011-03-01 20:02 vmlinuz-2.6.32-30-server
-rw-r--r--  1 root root 4.0M 2011-04-08 18:07 vmlinuz-2.6.32-31-server
-rw-r--r--  1 root root 4.0M 2011-04-20 17:53 vmlinuz-2.6.32-32-server
-rw-r--r--  1 root root 4.0M 2011-07-07 20:35 vmlinuz-2.6.32-33-server

```

---

### Post by arrrghhh on 2011-07-25
Yes, you can remove those just fine.

```
rm *2.6.32-2*
``` etc to get rid of multiples... Just be **very** careful when structuring 'fuzzy' rm statements - you don't want to accidentally delete them all or the wrong one!

---

### Post by CharlesA on 2011-07-25
> **arrrghhh said:**
> Yes, you can remove those just fine.

```
rm *2.6.32-2*
``` etc to get rid of multiples... Just be **very** careful when structuring 'fuzzy' rm statements - you don't want to accidentally delete them all or the wrong one!
+1.

When in doubt, use rm -i so it prompts you to confirm each file deletion.

---

### Post by borntoventure on 2011-07-25
Ok no problem with removing them I just wanted to make sure before I did. Over all the years I've been managing Linux servers this is the first time I've ever had this come up!

Thanks for the help!

---

