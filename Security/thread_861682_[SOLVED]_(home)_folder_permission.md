---
title: "[SOLVED] (home) folder permission"
date: 2008-07-16
forum: Security
---

### Post by Kognit on 2008-07-16
Hi

Recently my ubuntu went wrong because of kleansweeper. So i decided to reinstall it. I created two partition and on the one the old ubuntu stayed. then i ireinstall it on the other partition. So, i we got on one partition now (old) home folder which i don't want to delete. But the problem is that i cannot change the name of "home" folder, only the names of subfolders. I tried many things, but didn't help.

Any suggestions

Thanks very much

---

### Post by tuxxy on 2008-07-16
Try editing the permissions to read and write, locate the folder in nautlius - right click the folder icon > properties and find the permissions setting.

---

### Post by Kognit on 2008-07-16
i tried tha long before but didn't work

any more suggestions?

i even tried with the chmod and chown command

---

### Post by Gamma746 on 2008-07-16
Press Alt+F2 and type ```
gksudo nautilus
``` Type in your password, then change the permissions from that window.

---

### Post by hyper_ch on 2008-07-17
just mount the backuped partition as /home and all is set... you do need a folder /home if you want to mount the other partition so there is no need to rename the newly created home upon installation.

---

### Post by Kognit on 2008-07-17
Thanks, i did run nautilus and works. 

Thanks to everyone and have a good time

---

