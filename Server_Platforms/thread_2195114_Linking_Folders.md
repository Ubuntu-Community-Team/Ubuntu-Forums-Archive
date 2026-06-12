---
title: "Linking Folders"
date: 2013-12-22
forum: Server Platforms
---

### Post by adam17 on 2013-12-22
Hi all,

I have been looking for a solution to a problem I am having with MiniDlna. I believe I have found a solution and I need to link or create a soft link or something (was mentioned on another site).

How do I do this? I am having trouble finding a working solution for me.

I want to have several links within the folder /media/MyDlnaFiles to /media/Disk2/HD Videos
                                                                                                  /media/Disk2/TV Shows
                                                                                                  /media/Disk2/Music Videos
                                                                                                  /media/Disk3/Videos

This will then enable Mini Dlna to scan these links and separate the media into folders I believe.

How would I create a link between the MyDlnaFiles folder and the media folders?

Thanks In Advance.

Adam

---

### Post by ajgreeny on 2013-12-22
What filesystem is the external (I assume it's external) drive formatted to, and also the other /media/Disks?

To make a soft link you will need the folder in which the link is made to be one of the Linux filesystems, eg ext4.  If you have a windows filesystem, eg ntfs partition, you will not be able to make a soft link to another folder.

Give us more detail and we may be able to help you more.

---

