---
title: "Cant login to Ubuntu after restarting my computer"
date: 2007-06-12
forum: Testimonials &amp; Experiences
---

### Post by tlhern on 2007-06-12
hi, i have been doing a task of Remastering Ubuntu Dapper. i have done for the preparation which is stated below:

1) get a handle on the ISO image by running the command 'mount -o loop dapper.iso /mnt'
2) copy all of that to a working location with a 1Gb free. Lets call that $CD:
'rsync -ax /mnt/. $CD/'

so far no problem is happen until i come the step which is 

3) Edit $CD/isolinux/isolinux.cfg to add
'preseed/locale=en_GB kbd-chooser/method=gb DEBCONF_PRIORITY=critical'

when i type 'gedit isolinux.cfg' the terminal is hanged after running the process. so i reopen a new terminal and continue the below steps.

4) dismount the CD by typing the code

umount /mnt

5)  unpack the real working file system, which is inside a compressed filesystem on the CD setup. 

'mount $CD/casper/filesystem.squashfs /mnt -t squashfs -o loop'

6) I find it easiest to copy this to a directory on disk. Make this on an ext2 partition, however. Lets call that $Source; copy over the contents, and unmount the file system:

'rsync -av /mnt/. $Source/.
umount /mnt'

here again after running the process the terminal is hanged again adn i couldnt proceed to next step. 

when i reopen the terminal again, it appear the statement " I have no name@tlhern-desktop:$" whereas my username is tlhern. i even cannot login as superuser too, and all the installation process cannot be done. 

seeing this problem, i restart my computer again and when i try to login using the same and the only one username and password, the username and password are invalid. 

can any one propose me some ideas why is this happen?? thank you

---

### Post by Lord_Alda on 2007-06-12
Wrong thread :-P.... Try the Hardware & Laptop Thread....:-({|=

---

### Post by Geekkit on 2007-06-13
Sorry guy, you'll want:

[http://ubuntuforums.org/forumdisplay.php?f=131](http://ubuntuforums.org/forumdisplay.php?f=131)

Or better known as [General Help]("http://ubuntuforums.org/forumdisplay.php?f=131")

In this forum, we're just the strange front door/meet-and-greet people.

---

### Post by wolfen69 on 2007-06-13
go to the absolute beginers room, take a deep breath.

---

